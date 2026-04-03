---
title: "Proposal"
date: 2026-03-26
weight: 2
chapter: false
pre: " <b> 2. </b> "
--------------------

# GUARDSCRIPT — Code Protector Platform

## Project Proposal

**Team Members:**

| Full Name         | Student ID | Role        |
| ----------------- | ---------- | ----------- |
| Võ Tấn Phát       | SE194484   | Team Leader |
| Bùi Minh Hiển     | SE190829   | Member      |
| Dương Nguyên Bình | SE194067   | Member      |
| Trần Vinh         | SE193927   | Member      |
| Nguyễn Duy Tùng   | SE196572   | Member      |
| Nguyễn Đức Trí    | SE194091   | Member      |

**AWS Services (implemented in code/infra):** `Lambda` · `DynamoDB` · `S3` · `CloudFront` · `CloudWatch` · `API Gateway WebSocket`

---

### 1. Executive Summary

**GuardScript** is a script distribution platform with loader-based access control. Instead of distributing source code directly, the system serves script content through controlled endpoints with signature checks, timestamp/nonce validation, license enforcement, HWID binding, and workspace access policies.

The solution uses a serverless AWS architecture to reduce operational overhead, support scale, and satisfy cloud workshop objectives.

---

### 2. Problem Statement

#### Current Problems

The team identified three key issues in script delivery workflows:

1. Source code can be copied and redistributed without authorization.
2. Access revocation and device-bound licensing are difficult to enforce.
3. Operational visibility is often missing for abuse detection and troubleshooting.

#### Solution

The proposed system addresses these issues through:

1. Loader-based script retrieval instead of direct source distribution.
2. Dual transfer protocols: v2 (XOR + response verification) and v3 (X25519 ECDH + AES-GCM).
3. License/HWID controls with access list policies.
4. Cloud-native observability using CloudWatch and application logs.

#### Benefits and ROI

1. Stronger control over script usage and distribution.
2. Better protection against API abuse via signed requests and rate limits.
3. Cost-efficient operation for student/demo workloads with pay-per-use services.

---

### 3. Solution Architecture

The architecture follows a serverless model with edge delivery for frontend and Lambda-based API processing.

**Typical request flow:**

```
Client (browser / loader)
  → CloudFront Distribution (SSL termination, cache layer)
    → Static assets: S3 bucket (frontend)
    → API /api/*, /files/*: Lambda Function URL origin
      → DynamoDB (users, workspaces, projects, licenses, logs, rate_limits, ...)
      → S3 (script/content objects)
  → API Gateway WebSocket (real-time updates)
  → CloudWatch Logs / Alarms / Dashboard
```
![IrisAuth System Architecture](/images/2-Proposal/architecture.jpg)

#### AWS Services Used

| Layer          | Service                   | Details                                                                       |
| -------------- | ------------------------- | ----------------------------------------------------------------------------- |
| Runtime API    | AWS Lambda (Node.js 20.x) | Modular monolith backend handlers |
| Database       | Amazon DynamoDB           | Multi-table model, PAY_PER_REQUEST, TTL for temporary records |
| Object Storage | Amazon S3                 | Frontend hosting and content objects |
| CDN & Edge     | Amazon CloudFront         | Static delivery and route behaviors for `/api/*`, `/files/*` |
| Monitoring     | Amazon CloudWatch         | Alarms for errors/throttles/p95 duration + operational dashboard |
| Real-time      | API Gateway WebSocket API | Workspace/user/admin event broadcasting |
| Delivery       | GitHub Actions + SAM      | Automated infrastructure and frontend deployment |

#### Component Design

1. **Client Layer**: web dashboard and loader clients (Python/Node/Lua).
2. **Edge Layer**: CloudFront routing and caching.
3. **Compute Layer**: Lambda handlers for auth, workspace, project, license, and loader protocols.
4. **Data Layer**: DynamoDB + S3.
5. **Observability Layer**: CloudWatch metrics/alarms/dashboard and application logs.

---

### 4. Technical Implementation

#### 4.1. Authentication System

Token format: `v2.<payload_base64url>.<signature_base64url>`

1. Tokens are signed with HMAC-SHA256 using a secret stored in app config.
2. Password hashing uses PBKDF2-SHA256 (210000 iterations).
3. Signature verification uses timing-safe comparison.
4. Workspace PIN verification uses TTL-based session tokens.

#### 4.2. Two Code Distribution Protocols

**Protocol v2 — GET /api/v5/execute (XOR)**

1. Client sends `id`, `license`, `HWID`, `timestamp`, `nonce`, `signature`.
2. Server validates signature, timestamp window (±300s), and rate limits.
3. Response is XOR-encrypted and signed.

**Protocol v3 — POST /api/v5/handshake (ECDH + AES-GCM)**

1. Client sends an X25519 public key to handshake endpoint.
2. Server derives shared secret and AES key.
3. Script is encrypted using AES-GCM and returned with response signature.

#### 4.3. Security Algorithms and Standards

| Algorithm                          | Usage                                                 |
| ---------------------------------- | ----------------------------------------------------- |
| PBKDF2-SHA256 (210,000 iterations) | Password hashing, Workspace PIN hashing               |
| HMAC-SHA256                        | Token signing, request signing, response signing      |
| ECDH X25519                        | Key exchange in Protocol v3                           |
| HKDF-SHA256                        | AES key derivation from ECDH shared secret (RFC 5869) |
| AES-256-GCM                        | Script encryption (S3 + transmission in Protocol v3)  |
| XOR + SHA-256                      | Transmission encryption (Protocol v2)                 |
| crypto.timingSafeEqual           | Secure comparison to prevent timing attacks           |
| Nonce + Timestamp ±5 minutes       | Replay attack protection                              |
| S3 SSE-S3 (AES256)                 | Default object encryption in current template         |

#### 4.4. Database — Amazon DynamoDB

| Table                   | Partition Key / Sort Key                | Purpose                                                |
| ----------------------- | --------------------------------------- | ------------------------------------------------------ |
| users                 | PK: userId                            | User accounts, roles, password_changed_at            |
| workspaces            | PK: workspaceId                       | Workspace config, loader_key, encryption_key, PIN hash |
| projects              | PK: workspaceId, SK: projectId      | Project settings, execution count                      |
| project_files         | PK: projectId, SK: fileId           | Project file structure, entry point, ordering          |
| licenses              | PK: workspaceId, SK: licenseKey    | License info, HWID, expiration, usage count            |
| access_lists          | PK: workspaceId, SK: ip#type        | IP blacklist/whitelist                                 |
| workspace_members     | PK: workspaceId, SK: userId         | Workspace members and roles                            |
| workspace_invitations | PK: token                             | Team invitation tokens, **TTL enabled**                |
| pin_verifications     | PK: sessionToken                      | PIN verification sessions, **TTL enabled**             |
| logs                 | PK: workspaceId, SK: timestamp#uuid | Event logs, GSI on country, timestamp              |
| app_config            | PK: configKey                         | System configs (HMAC secret, loader secret…)           |
| rate_limits           | PK: rateLimitKey                      | Sliding window rate limiting with **TTL**              |

> **Design Note**: TTL is enabled on `workspace_invitations`, `pin_verifications`, and `rate_limits` to automatically delete expired records without cron jobs. GSI on `country` and `timestamp` supports analytics queries.

---

### 5. Roadmap & Milestones

| Phase                 | Content                                                                       | Timeline   |
| --------------------- | ----------------------------------------------------------------------------- | ---------- |
| 1. Analysis & Design  | Requirements, DynamoDB schema, API and architecture design                    | Week 1–3   |
| 2. Backend Core       | Auth, workspace, project, file, and license APIs                              | Week 4–6   |
| 3. Loader Security    | Protocol v2/v3, HWID lock, access policy, rate limits                         | Week 7–9   |
| 4. Frontend & Integrations | Dashboard/workspace UI and cloud integration                              | Week 10    |
| 5. Hardening & Documentation | Monitoring baseline, deployment pipeline, final reporting             | Week 11–12 |

---

### 6. Cost Estimation

| Service           | Estimated Cost     | Notes                           |
| ----------------- | ------------------ | ------------------------------- |
| AWS Lambda        | ~$0.00/month       | Free tier: 1M requests/month    |
| Amazon DynamoDB   | ~$0.00–$1.00/month | On-demand, 25 GB free storage   |
| Amazon S3         | ~$0.10–$0.50/month | Frontend + content storage      |
| Amazon CloudFront | ~$0.00–$1.00/month | 1 TB free transfer (first year) |
| Amazon CloudWatch | ~$0.00–$0.50/month | 30-day log retention            |
| API Gateway       | ~$0.01–$0.10/month | REST + WebSocket                |
| **Total**         | **~$1–3/month**    | Usage-based                     |

---

### 7. Risk Assessment

| Risk                      | Impact | Probability | Mitigation                             |
| ------------------------- | ------ | ----------- | -------------------------------------- |
| Lambda cold start latency | Medium | Medium      | Optimize handlers and monitor p95      |
| DynamoDB throttling       | High   | Low         | On-demand scaling, CloudWatch alerts   |
| S3 PUT/GET failures       | High   | Low         | Retry logic, versioning enabled        |
| Budget overrun            | Medium | Low         | AWS Budgets alerts, optimize TTL/cache |
| Replay attacks            | High   | Low         | Timestamp + nonce + HMAC required      |

**Contingency Plan:**

* If primary endpoint behavior fails → fallback to Lambda Function URL.
* If S3 is unavailable → retry with exponential backoff, log to CloudWatch.
* Use SAM/CloudFormation stacks for quick infrastructure recovery.

---

### 8. Security Considerations

1. Signed request/response validation with HMAC-SHA256.
2. Timestamp + nonce verification for replay resistance.
3. IP/scope rate limiting with TTL-based cleanup.
4. Role-based access control at workspace level.
5. HWID lock enforcement for licensed scripts.
6. IAM role permissions scoped to stack resources.

---

### 9. Monitoring / Logging / Validation

1. CloudWatch alarms are configured for `Errors`, `Throttles`, and `p95 Duration`.
2. A CloudWatch dashboard is provisioned for runtime visibility.
3. Application-level logs are stored by workspace for auditability.
4. Validation checklist includes auth, protocol, access-list, and alarm tests.

---

### 10. Deployment / Implementation Plan

1. Deploy infrastructure via AWS SAM (`sam build`, `sam deploy`).
2. Sync frontend artifacts to S3 hosting bucket.
3. Invalidate CloudFront after frontend updates.
4. Optionally use GitHub Actions pipeline for automated deployment.
5. Validate output endpoints (CloudFront, Lambda URL, WebSocket, table names).

---

### 11. Expected Outcomes

**Technical Outcomes:**

* End-to-end AWS serverless deployment with validated API and loader flow.
* Dual loader protocol support with security controls (signature, HWID, rate-limit).
* Baseline observability for runtime health and performance.
* Reproducible deployment process aligned with workshop requirements.

**Long-term Value:**

* Extendable architecture for additional loaders and governance features.
* Reusable cloud-native reference for future FCJ workshop projects.

---


### 12. Future Improvements

1. Add production-ready SES email workflow for invitations.
2. Add AWS WAF managed rules for edge protection.
3. Upgrade S3 encryption controls from SSE-S3 to SSE-KMS CMK where needed.
4. Add AWS Budgets and Cost Anomaly Detection.
5. Increase automated test coverage (unit/integration/security checks).