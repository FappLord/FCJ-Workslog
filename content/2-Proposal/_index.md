---
title: "Proposal"
date: 2026-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# GuardScript — Secure Code Distribution Platform
## A Serverless AWS Solution for Encrypted Script Delivery & License Management

### 1. Project Overview

**GuardScript** is a cloud-native platform built to solve the problem of unauthorized code redistribution. It provides developers and software vendors with a secure way to distribute their scripts (Python, Node.js) while maintaining full control over who can execute the code, on which hardware, and for how long.

The platform is built by **Team TheBois** as the main project for the FCJ 2026 internship program. It runs entirely on AWS serverless infrastructure, ensuring automatic scalability, low operational overhead, and pay-per-use efficiency.

**My role in this project** focuses on:
- Frontend website design and implementation (landing page, dashboard, workspace IDE, auth pages).
- Team coordination, task distribution, and progress tracking.
- Basic support in infrastructure setup and testing.

### 2. Objectives

1. **Secure Distribution:** Enable developers to distribute encrypted scripts that can only be executed by authorized users with valid licenses.
2. **License Management:** Provide a complete license lifecycle — creation, batch generation, HWID locking, expiration, and revocation (kill switch).
3. **Workspace Isolation:** Allow multiple isolated workspaces with independent projects, team members, encryption keys, and access rules.
4. **Team Collaboration:** Support role-based team collaboration (owner, admin, editor, viewer) with invitation-based onboarding.
5. **Cloud-Native Deployment:** Run the entire platform on AWS serverless services for cost efficiency and automatic scaling.
6. **Professional Frontend:** Deliver a polished, responsive web interface for managing all platform features.

### 3. Problem Statement

#### The Problem
Independent developers, small studios, and educators who distribute scripts (automation tools, plugins, training materials) face a common challenge: **once code is shared, it can be freely copied and redistributed** without the author's consent. Existing solutions are either:
- Too expensive (enterprise DRM platforms).
- Too complex (custom licensing servers requiring dedicated infrastructure).
- Language-specific (only work for compiled languages, not interpreted scripts like Python or JavaScript).

There is no lightweight, cloud-native solution that provides:
- Encrypted script delivery for interpreted languages.
- Hardware-locked licensing.
- Per-project access control and analytics.
- A simple web interface for managing everything.

#### The Impact
Without code protection, script authors lose revenue, have no way to enforce usage terms, and cannot track how their code is being used. This discourages authors from sharing valuable tools and educational content.

### 4. Proposed Solution

GuardScript addresses this by providing an **end-to-end encrypted delivery pipeline**:

1. **Upload:** Authors upload their scripts (single file or multi-file projects) via the web dashboard.
2. **Encrypt:** Scripts are compressed (gzip) and encrypted at rest using AES-256-GCM with workspace-level encryption keys.
3. **License:** Authors create license keys (single or batch) with optional HWID locking, expiration dates, and per-project binding.
4. **Distribute:** End-users receive a lightweight loader script (Python or Node.js) configured with their license key.
5. **Execute:** The loader performs an ECDH key exchange with the server, receives the encrypted script, decrypts it client-side, and executes it in a sandboxed environment.
6. **Control:** Authors can monitor executions, revoke licenses, block IPs, and toggle projects on/off — all from the dashboard.

**Key Features:**
- **Workspace isolation** — each workspace has its own encryption key, projects, team, and access rules.
- **Multi-language loaders** — Python and Node.js loaders with ECDH handshake, AES decryption, and HWID fingerprinting.
- **Role-based team collaboration** — owner > admin > editor > viewer hierarchy with invitation system.
- **IP whitelist/blacklist** — per-workspace access rules.
- **Execution analytics** — usage counts, last-used timestamps, geo-location logging.
- **Kill switch** — instantly disable any project or license.

### 5. Architecture Overview

The platform uses a fully serverless AWS architecture. All compute, storage, and database services are managed by AWS, eliminating the need for server provisioning or maintenance.

> **Note:** The detailed architecture diagram is currently being finalized. The description below reflects the actual deployed infrastructure as defined in the SAM template (`infra/template.yaml`).

**High-Level Architecture:**

```
[End User / Loader] ──HTTPS──▶ [Lambda Function URL]
                                       │
                               ┌───────┴────────┐
                               │  API Router     │
                               │  (Express.js)   │
                               └───────┬────────┘
                          ┌────────────┼────────────┐
                          ▼            ▼            ▼
                    [DynamoDB]    [S3 Content]  [CloudWatch]
                    12 tables     Encrypted      Alarms &
                    + GSIs        files           Dashboard

[Browser] ──HTTPS──▶ [CloudFront CDN] ──▶ [S3 Frontend Bucket]
                      OAC + SPA rewrite    Static HTML/CSS/JS
```

**Data Flow — Script Execution:**
1. Loader sends license key + HWID to `/api/v5/handshake`.
2. Server validates license, HWID, IP rules, and rate limits.
3. Server generates ephemeral X25519 key pair, derives shared secret via ECDH.
4. Server encrypts script content with AES-256-GCM using the derived key.
5. Server responds with encrypted payload + server public key + HMAC signature.
6. Loader derives the same shared secret, verifies HMAC, decrypts script, and executes.

### 6. AWS Services Used

| Service | Purpose | Why This Service |
|:---|:---|:---|
| **AWS Lambda** | Single function handling all API routes (Node.js 20.x) via Function URL | Zero server management, automatic scaling, pay-per-invocation. Ideal for variable workloads. |
| **Amazon DynamoDB** | Primary database — 12 tables with Global Secondary Indexes | Serverless NoSQL with single-digit-ms latency. GSIs enable flexible query patterns without schema migrations. |
| **Amazon S3** (2 buckets) | Frontend static hosting + encrypted project file storage | Durable, cost-effective object storage. Versioning enabled for frontend rollbacks. AES256 server-side encryption. |
| **Amazon CloudFront** | CDN for frontend delivery with OAC and SPA routing | Global edge distribution, HTTPS termination, custom error pages, path-based rewriting for SPA. |
| **AWS SAM / CloudFormation** | Infrastructure as Code — defines all resources in a single template | Repeatable deployments, version-controlled infrastructure, automatic dependency resolution. |
| **AWS IAM** | Service roles and permission policies | Least-privilege access for Lambda to DynamoDB and S3. No over-permissioned roles. |
| **Amazon CloudWatch** | Monitoring: logs, alarms (errors, throttles, p95 latency), dashboard | Centralized observability. Alarms trigger on error spikes or performance degradation. |

### 7. Timeline

| Phase | Period | Activities |
|:---|:---|:---|
| **Weeks 1–5** (Jan 5 – Feb 6) | AWS Learning & Project Ideation | AWS fundamentals (EC2, S3, VPC, IAM, Lambda, DynamoDB), project brainstorming, team setup, certifications. |
| **Tết Break** (Feb 7 – Feb 22) | Holiday | — |
| **Week 6** (Feb 23) | Project Design | Post-Tết sync, GuardScript scope definition, architecture design, crypto research. |
| **Weeks 7–8** (Mar 2 – Mar 14) | Local Prototype | Backend development (Express.js + SQLite), auth, controllers, crypto module, loaders, license system. |
| **Week 9** (Mar 16) | AWS Migration | SAM template, DynamoDB migration, S3 setup, frontend landing & auth pages design. |
| **Week 10** (Mar 23) | Frontend & Testing | Dashboard, workspace IDE, responsive design, integration testing. |
| **Weeks 11–12** (Mar 30 – Apr 11) | Polish & Delivery | Final testing, bug fixes, documentation, architecture diagram finalization, report preparation. |

### 8. Budget / Cost Estimation

| Item | Cost |
|:---|:---|
| AWS Lambda | Covered by free tier / credits |
| Amazon DynamoDB | Covered by free tier / credits |
| Amazon S3 | Covered by free tier / credits |
| Amazon CloudFront | Covered by free tier / credits |
| CloudWatch | Covered by free tier / credits |
| **Total estimated cost** | **0 USD** |

> **Note:** All infrastructure costs are covered by **AWS promotional credits (200 USD)**. The project is designed to operate well within the free tier limits for development and low-traffic production use. No additional hardware or third-party service costs are required.

### 9. Risk Assessment

| Risk | Impact | Probability | Mitigation |
|:---|:---:|:---:|:---|
| **Credit exhaustion** | Medium | Low | Monitor usage with AWS Budgets and Cost Explorer. Architecture uses serverless pay-per-use services, keeping costs minimal. |
| **DynamoDB throttling** | Medium | Low | On-demand capacity mode handles traffic spikes automatically. GSIs designed to distribute queries evenly across partitions. |
| **Loader reverse engineering** | Medium | Medium | ECDH key exchange ensures each session uses a unique encryption key. Script content is never cached in plaintext on disk. Obfuscation of loaders adds an extra layer. |
| **Key/credential leakage** | High | Low | No secrets stored in code. Environment variables injected via SAM template. JWT tokens have 7-day TTL with password-change invalidation. |
| **CloudFront cache staleness** | Low | Medium | Cache invalidation on deployment. Versioned S3 objects for frontend assets. |
| **Team coordination delays** | Medium | Medium | Weekly syncs, clear task ownership documentation, daily check-ins during critical phases. |

### 10. Future Improvements

1. **Additional Language Loaders:** Extend support to Lua, Ruby, or other interpreted languages.
2. **Usage Analytics Dashboard:** Visualize execution patterns, geographic distribution, and license utilization with charts.
3. **Webhook Notifications:** Alert authors when licenses are activated, expired, or when suspicious activity is detected.
4. **Custom Domain Support:** Allow authors to serve loaders from their own branded domains.
5. **CI/CD Pipeline:** Automate deployments with GitHub Actions for continuous delivery.
6. **Monaco Editor Integration:** Embed a full-featured code editor (Monaco) in the workspace IDE for in-browser editing.
7. **Two-Factor Authentication:** Add TOTP-based 2FA for enhanced account security.
8. **Audit Logging:** Comprehensive audit trail for compliance-sensitive use cases.

### 11. Personal Contribution Context

As a team leader, my primary contributions to this project are:

- **Frontend website design and implementation:** Designed and built all frontend pages (landing, login, register, dashboard, workspace IDE) with responsive layouts, theme switching, and interactive components.
- **Team coordination and progress tracking:** Managed task distribution across Team TheBois, conducted weekly syncs, tracked milestones, and ensured alignment between frontend and backend development.
- **Limited technical support:** Assisted with basic infrastructure tasks (S3 configuration, CloudFront setup, SAM template review) but did not own the backend security architecture or cryptographic implementation, which were handled by other team members with deeper security expertise.
