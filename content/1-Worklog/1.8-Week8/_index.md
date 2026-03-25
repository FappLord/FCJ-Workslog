---
title: "Week 8: GuardScript — Feature Development, Crypto Module & Frontend Improvements"
date: 2026-03-09
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### 1. Objectives

* **Controller Layer:** Implement all remaining controllers — project, file, license, team, and access control.
* **Crypto Module:** Build the cryptographic backbone for encrypted file storage and secure script delivery via ECDH key exchange.
* **Script Loader System:** Develop the Python and Node.js loaders for end-users.
* **Frontend Improvements:** Fix UI bugs, develop collapsible sidebar, update logo and documentation.

### 2. Weekly Tasks Breakdown

| Day | Main Task | Details | Status |
|:---:|:---|:---|:---:|
| **Mon** | **Project & File Controllers** | - Implemented `projectController.js`: CRUD, toggle active, reset stats, project settings.<br>- Implemented `fileController.js`: file tree, upload, search, entry point management.<br>- Fixed workspace page layout issues on certain viewports.<br>- Merged PR Fix-UI, created project README. | Completed |
| **Tue** | **Crypto Module** | - Built `crypto.js`: AES-256-GCM encryption/decryption, X25519 ECDH key exchange, HKDF key derivation, HMAC-SHA256. | Completed |
| **Wed** | **License Controller & Sidebar** | - Implemented `licenseController.js`: single/batch creation, HWID lock, export, expiration.<br>- Tested collapsible sidebar feature across screen sizes. | Completed |
| **Thu** | **Script Loaders & Sidebar UI** | - Developed Python Loader (ECDH handshake, AES-256-GCM decryption, HWID) and Node.js Loader (multi-file manifest, VM sandbox).<br>- Fixed sidebar UI, updated logo, fixed dashboard quick-action pointers. | Completed |
| **Fri** | **Access/Team Controllers & Cleanup** | - Built `accessController.js` (IP whitelist/blacklist) and `teamController.js` (invite, roles, removal).<br>- Cleaned up dead code, added repo links to documentation. | Completed |

### 3. Key Results

#### Technical:
* **Complete Controller Layer:** All 10 controllers implemented.
* **End-to-end Encryption Pipeline:** File upload → gzip → AES-256-GCM → storage; ECDH handshake → session key → deliver to client → decrypt in sandbox.
* **Loader System:** Both Python and Node.js loaders functional with ECDH key exchange and hardware fingerprinting.
* **License Management:** Complete lifecycle — creation, HWID lock, expiration, export.

#### Frontend:
* Fixed workspace layout, collapsible sidebar, new logo, comprehensive README.
* Merged PR#3 Fix-UI, cleaned up unused imports.

### 4. Issues & Solutions
* **Issue:** ECDH key exchange adds ~100ms latency per handshake.
* **Solution:** Accepted the tradeoff — security is more important; handshake happens only once per session.

### 5. Next Steps
* Begin AWS migration — design serverless architecture.
* Create SAM/CloudFormation template.
* Continue improving overall UI.
