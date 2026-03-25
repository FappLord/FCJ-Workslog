---
title: "Week 6: Post-Tet Sync & GuardScript Project Design"
date: 2026-02-23
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### 1. Objectives

* **Team Sync:** Reconnect with Team TheBois after the Tet holiday; review progress and align on project direction.
* **Project Finalization:** Formally adopt **GuardScript** as the main FCJ internship project and define its scope.
* **Architecture Design:** Design the high-level system architecture, database schema, and API structure.
* **Research:** Study encryption techniques (AES-GCM, ECDH) and code protection strategies relevant to the project.

### 2. Weekly Tasks Breakdown

| Day | Main Task | Details | Status |
|:---:|:---|:---|:---:|
| **Mon** | **Team Sync** | - Reconnected with Team TheBois after 2-week Tet break.<br>- Reviewed project ideas from Week 5.<br>- Formally selected **GuardScript** as the primary project. | Completed |
| **Tue** | **Scope Definition** | - Defined core features:<br>&nbsp;+ Workspace-based project management<br>&nbsp;+ Encrypted script distribution (Python, Node.js)<br>&nbsp;+ License key management with HWID locking<br>&nbsp;+ Role-based team collaboration<br>&nbsp;+ Access control (IP whitelist/blacklist) | Completed |
| **Wed** | **Architecture Design** | - Designed backend structure: Express.js + SQLite for the initial prototype.<br>- Planned modular controller pattern (auth, project, file, license, workspace, team, access controllers).<br>- Sketched API route structure (~70 endpoints). | Completed |
| **Thu** | **Crypto Research** | - Researched AES-256-GCM for file content encryption.<br>- Studied ECDH (X25519) key exchange for secure loader handshake.<br>- Evaluated PBKDF2 (210K iterations) for password hashing vs bcrypt. | Completed |
| **Fri** | **Development Setup** | - Initialized Node.js project with Express framework.<br>- Set up project repository structure.<br>- Created initial `package.json` with dependencies.<br>- Configured development environment and tooling. | Completed |

### 3. Key Results (Deliverables)

#### Technical:
* **Architecture Plan:** Designed a modular monolith backend with clear separation:
    * **Controllers:** 10 domain-specific controllers handling different aspects of the platform.
    * **Utils:** Reusable crypto, auth, rate-limiting, and response modules.
    * **Storage:** File system-based storage with encryption at rest.
* **Security Design:** Selected industry-standard cryptographic approaches:
    * AES-256-GCM for file content encryption.
    * ECDH key exchange for loader handshake.
    * PBKDF2-SHA256 (210K iterations) for password storage.
    * JWT (HMAC-SHA256) for authentication tokens.

#### Project (Team TheBois):
* **Scope Locked:** Team agreed on GuardScript scope — focusing on the core problem of unauthorized code redistribution.
* **Architecture Aligned:** All team members understand the planned system architecture.

### 4. Issues & Solutions
* **Issue:** Choosing between SQLite (simple, file-based) vs PostgreSQL (robust, networked) for the initial prototype.
* **Solution:** Selected SQLite for the prototype phase due to zero-config setup and portability. Planned migration to DynamoDB for the AWS deployment phase.

### 5. Lessons Learned
* Defining clear project scope early prevents feature creep.
* Modular controller patterns make it easier to parallelize development across team members.
* Selecting the right cryptographic primitives upfront is critical for security-sensitive applications.

### 6. Next Steps
* Begin hands-on development of the GuardScript backend.
* Implement core database schema and authentication module.
* Start building the controller layer for workspace and project management.
