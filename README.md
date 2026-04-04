# First Cloud AI Journey 2026 — Internship Worklog

Official documentation and worklog for my internship at the **First Cloud AI Journey (FCJ) 2026** program. Records weekly activities, the GuardScript project proposal, a full AWS deployment workshop, participated events, self-evaluation, and feedback.

## Author

| Field | Value |
|---|---|
| Name | Võ Tấn Phát |
| Student ID | SE194484 |
| Role | Team Lead — AI Engineer |
| Team | TheBois |
| Program | First Cloud AI Journey 2026 |
| Period | 05/01/2026 – 18/04/2026 |

## Team TheBois

| No. | Name | Role | Track |
|:---:|---|---|---|
| 1 | Võ Tấn Phát | Leader | AI |
| 2 | Dương Nguyên Bình | Member | AI |
| 3 | Nguyễn Đức Trí | Member | IA |
| 4 | Trần Vinh | Member | IA |
| 5 | Nguyễn Duy Tùng | Member | IA |
| 6 | Bùi Minh Hiển | Member | IA |

## Content Structure

```
1. Worklog           — Weekly activity logs (12 weeks)
2. Proposal          — GuardScript project proposal (architecture, tech requirements, phases, cost, risk)
3. Events            — Participated FCJ events
4. Workshop          — Step-by-step AWS deployment guide for GuardScript
5. Self-evaluation   — Personal reflection and assessment
6. Feedback          — Sharing and suggestions
```

## Project — GuardScript

**GuardScript** is a serverless script distribution platform with loader-based access control, deployed on AWS.

**Architecture:**
```
Client (browser / loader)
  → CloudFront (SSL, cache, SPA rewrite)
    → S3 (frontend static assets)
    → Lambda Function URL (API backend — /api/*, /files/*)
      → DynamoDB (14 tables — PAY_PER_REQUEST)
      → S3 (encrypted script content)
  → API Gateway WebSocket (real-time events)
  → CloudWatch (Alarms, Dashboard, Logs)
```

**Key AWS Services:** Lambda (Node.js 20.x) · DynamoDB · S3 · CloudFront · API Gateway WebSocket · CloudWatch · AWS WAF · ACM · SAM/CloudFormation · GitHub Actions

**Security:** HMAC-SHA256 token signing · PBKDF2-SHA256 password hashing · ECDH X25519 + AES-256-GCM (Protocol v3) · XOR + HMAC (Protocol v2) · Nonce + Timestamp replay protection · HWID binding

## Workshop Summary

The [Workshop section](./content/5-Workshop/) provides a full step-by-step deployment guide:

| Phase | Content |
|---|---|
| 5.1 Overview | Architecture, request flow, loader protocols |
| 5.2 Prerequisites | Tools (Node.js 20.x, AWS CLI v2, SAM CLI), IAM permissions |
| 5.3 Phase 1 | Package Lambda ZIP → Upload to S3 |
| 5.4 Phase 2 | `sam build` + `sam deploy` — full infrastructure stack |
| 5.5 Phase 3 | Sync frontend to S3 + CloudFront invalidation |
| 5.6 Phase 4 | Seed DynamoDB config → create admin → smoke tests |
| 5.7 Cleanup | Delete stack + empty versioned S3 buckets |

## Technology Stack

| Tool | Purpose |
|---|---|
| Hugo | Static site generator |
| Markdown | Content formatting |
| Git & GitHub | Version control and hosting |
| AWS | Primary cloud platform |

## Local Development

```bash
# Clone the repository
git clone https://github.com/FappLord/FCJ-Workslog.git
cd FCJ-Workslog

# Start Hugo dev server
hugo server

# Open in browser
# http://localhost:1313
```

## License

Created for educational purposes within the FCJ 2026 Internship program.

