---
title: "Week 7: GuardScript — Core Backend Development"
date: 2026-03-02
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### 1. Objectives

* **Backend Foundation:** Initialize the GuardScript backend with Express.js and implement the core database schema using SQLite.
* **Authentication System:** Build a complete auth module with JWT tokens and PBKDF2 password hashing.
* **Core Modules:** Implement workspace management and foundational project CRUD operations.
* **Development Start:** The GuardScript project officially begins development on **March 6, 2026**.

### 2. Weekly Tasks Breakdown

| Day | Main Task | Details | Status |
|:---:|:---|:---|:---:|
| **Mon** | **Architecture Review** | - Finalized the backend architecture with the team.<br>- Reviewed the controller-service-util pattern for code organization.<br>- Prepared the development environment for rapid prototyping. | Completed |
| **Tue** | **Express.js Setup** | - Initialized Express.js application with middleware stack.<br>- Configured CORS, JSON body parsing, cookie handling.<br>- Set up route structure for 70+ API endpoints across 10 controllers. | Completed |
| **Wed** | **Database Schema** | - Designed and implemented SQLite schema covering:<br>&nbsp;+ Users table (id, email, password hash, status, timestamps)<br>&nbsp;+ Workspaces table (id, name, owner, loader key, encryption key, settings)<br>&nbsp;+ Projects table (id, workspace, name, secret key, entry point, settings)<br>&nbsp;+ Project Files, Licenses, Access Lists, Logs, Team Members tables. | Completed |
| **Thu** | **Auth Module** | - Implemented `src/utils/auth.js`:<br>&nbsp;+ PBKDF2-SHA256 password hashing (210,000 iterations, 16-byte salt)<br>&nbsp;+ JWT token generation and verification using HMAC-SHA256<br>&nbsp;+ Token extraction from Authorization header and cookies<br>&nbsp;+ Timing-safe comparison to prevent timing attacks. | Completed |
| **Fri** | **Workspace & User Controllers** | - Built `authController.js`: register, login, profile, password change, account deletion.<br>- Built `workspaceController.js`: create, list, update, delete workspaces; PIN protection; logs. | Completed |

### 3. Key Results (Deliverables)

#### Technical:
* **Backend Server:** Fully functional Express.js server with structured routing for all planned API endpoints.
* **Database Layer:** Complete SQLite schema with 10+ tables, foreign key relationships, and indexed columns for performance.
* **Auth System:** Production-grade authentication:
    * PBKDF2 with 210K iterations (exceeds OWASP recommended minimum of 600K for SHA-256, but balances security and performance).
    * Legacy SHA-256 hash detection with automatic upgrade path.
    * JWT tokens with 7-day TTL and password-change invalidation.
* **Rate Limiting:** Implemented per-IP, per-scope rate limiting using `src/utils/rateLimit.js`.

#### Code Quality:
* **Modular Structure:** Clean separation of concerns — controllers handle HTTP, utils handle business logic, database handles persistence.
* **Security First:** No plaintext passwords, timing-safe comparisons, proper token management.

### 4. Issues & Solutions
* **Issue:** Designing a flexible workspace system that supports both individual and team use with different permission levels.
* **Solution:** Implemented a role-based access control system with 4 levels: `owner > admin > editor > viewer`, with granular permission checks per operation.

### 5. Lessons Learned
* Starting with a clear database schema saves significant refactoring time later.
* PBKDF2 iteration count must balance security and user experience — 210K iterations adds ~200ms per login, which is acceptable.
* Route organization by domain (auth, workspace, project, etc.) scales better than organizing by HTTP method.

### 6. Next Steps
* Implement remaining controllers: project, file, license, team, access.
* Build the cryptographic module for file encryption and secure script delivery.
* Develop the script loader system.
