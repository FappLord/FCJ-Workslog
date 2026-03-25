---
title: "Week 9: GuardScript — AWS Migration & Frontend Design"
date: 2026-03-16
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### 1. Objectives

* **AWS Migration:** Begin migrating GuardScript from the local prototype (Express.js + SQLite) to a fully serverless AWS architecture.
* **Infrastructure as Code:** Set up the SAM/CloudFormation template defining Lambda, DynamoDB, S3, and CloudFront resources.
* **Frontend Design:** Design and build the frontend pages for the GuardScript web application (landing page, authentication pages).
* **Team Coordination:** Coordinate task distribution across Team TheBois for the migration effort.

### 2. Weekly Tasks Breakdown

| Day | Main Task | Details | Status |
|:---:|:---|:---|:---:|
| **Mon** | **Migration Planning** | - Reviewed the local prototype with the team and outlined the AWS migration plan.<br>- Identified AWS services needed: Lambda (compute), DynamoDB (database), S3 (storage + hosting), CloudFront (CDN).<br>- Distributed tasks: frontend (my responsibility), backend migration (team members), infrastructure setup (collaborative). | Completed |
| **Tue** | **Landing Page Design** | - Designed and built the GuardScript landing page (`frontend/index.html`, `style.css`, `script.client.js`).<br>- Created hero section with animated binary canvas background.<br>- Designed feature cards section showcasing 6 core features: licensing, cloud loader, workspace isolation, analytics, kill switch, access policies.<br>- Added workflow steps section and responsive navigation bar. | Completed |
| **Wed** | **Auth Pages Design** | - Designed and built login page (`frontend/login/`) with matrix background animation, email/password form, and benefits list.<br>- Designed and built registration page (`frontend/register/`) with matching visual style.<br>- Implemented auth-aware navigation (show/hide login/register/dashboard links based on session). | Completed |
| **Thu** | **SAM Template & S3 Setup** | - Reviewed and contributed to the SAM template (`infra/template.yaml`).<br>- Helped configure S3 bucket for frontend hosting with versioning and AES256 encryption.<br>- Set up CloudFront distribution with Origin Access Control (OAC) for secure S3 access.<br>- Configured CloudFront behaviors for SPA routing (rewrite subpaths to `index.html`). | Completed |
| **Fri** | **Team Sync & DynamoDB Review** | - Conducted team progress review — backend migration to DynamoDB on track.<br>- Reviewed DynamoDB schema design: 12 tables with Global Secondary Indexes (GSIs).<br>- Planned dashboard page layout and workspace IDE page structure for next week.<br>- Updated project timeline and task board. | Completed |

### 3. Key Results (Deliverables)

#### Frontend (Personal Contribution):
* **Landing Page:** Fully designed and implemented with:
    * Animated binary canvas hero section.
    * 6 feature cards with icons and descriptions.
    * Workflow visualization (3-step process).
    * Responsive navigation with auth-awareness.
    * Clean, professional dark theme visual identity.
* **Authentication Pages:** Login and registration pages with:
    * Matrix background animation effect.
    * Form validation and error handling.
    * Consistent visual language across pages.

#### Infrastructure (Team Effort):
* **SAM Template:** CloudFormation template defining all AWS resources:
    * `ApiFunction` — Lambda function (Node.js 20.x) with Function URL.
    * `FrontendBucket` — S3 bucket for static frontend hosting.
    * `ContentBucket` — S3 bucket for encrypted project file storage.
    * `Distribution` — CloudFront CDN with OAC and SPA rewriting.
    * 12 DynamoDB tables with GSIs for query optimization.
    * CloudWatch alarms (errors, throttles, p95 latency) and dashboard.
* **DynamoDB Migration:** Data layer ported from SQLite to DynamoDB using `DynamoDBDocumentClient`.

#### Team Management (Personal Contribution):
* Task distribution finalized — clear ownership for frontend, backend, and infrastructure.
* Progress tracking updated — team aligned on weekly deliverables.

### 4. Issues & Solutions
* **Issue:** CloudFront SPA routing — single-page application subpaths (e.g., `/workspace/123`) returned 403 errors because no corresponding S3 object existed.
* **Solution:** Configured CloudFront Functions to rewrite request URIs for known subpaths (`/dashboard/*`, `/workspace/*`, `/login/*`, `/register/*`) to their respective `index.html` files.

### 5. Lessons Learned
* CloudFront Origin Access Control (OAC) replaces the legacy Origin Access Identity (OAI) for improved security when serving S3 content.
* SAM templates significantly reduce deployment complexity — a single `sam deploy` replaces dozens of manual console steps.
* Designing the frontend visual identity early creates a consistent user experience across all pages.
* Clear task distribution with documented ownership prevents duplication and keeps the team moving in parallel.

### 6. Next Steps
* Implement the dashboard page with stats, workspace grid, and navigation.
* Build the workspace IDE page with file explorer, editor, and project settings.
* Complete backend migration testing on AWS.
* Begin end-to-end integration testing.
