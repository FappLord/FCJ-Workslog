---
title: "Week 8: GuardScript — Feature Development & Crypto Module"
date: 2026-03-09
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### 1. Objectives

* **Controller Layer:** Implement all remaining controllers — project management, file management, license management, team collaboration, and access control.
* **Crypto Module:** Build the cryptographic backbone for encrypted file storage and secure script delivery via ECDH key exchange.
* **Script Loader System:** Develop the Python and Node.js loaders that securely deliver encrypted code to end-users.
* **Access Control:** Implement IP whitelist/blacklist and hardware ID (HWID) locking for license management.

### 2. Weekly Tasks Breakdown

| Day | Main Task | Details | Status |
|:---:|:---|:---|:---:|
| **Mon** | **Project & File Controllers** | - Implemented `projectController.js`: CRUD operations, toggle active status, reset stats, project settings (license required, HWID lock, IP whitelist, rate limits).<br>- Implemented `fileController.js`: file tree retrieval, content editing, upload, search (plaintext & regex), copy, rename, move, entry point management. | Completed |
| **Tue** | **Crypto Module** | - Built `src/utils/crypto.js` with:<br>&nbsp;+ AES-256-GCM encryption/decryption for file content at rest.<br>&nbsp;+ X25519 ECDH key pair generation and shared secret derivation.<br>&nbsp;+ HKDF key derivation, SHA-256 hashing, Base64-URL encoding.<br>&nbsp;+ HMAC-SHA256 for data integrity verification. | Completed |
| **Wed** | **License Controller** | - Implemented `licenseController.js`:<br>&nbsp;+ Single & batch license creation with custom keys.<br>&nbsp;+ License export, toggle active/inactive status.<br>&nbsp;+ HWID lock toggle and HWID reset.<br>&nbsp;+ Expiration date support. | Completed |
| **Thu** | **Script Loaders** | - Developed **Python Loader** (`python/unified-loader.py`):<br>&nbsp;+ ECDH handshake with server for key exchange.<br>&nbsp;+ AES-256-GCM script decryption on client side.<br>&nbsp;+ Hardware ID generation (MAC, hostname, CPU, OS).<br>- Developed **Node.js Loader** (`javascript_nodejs/unified-loader.txt`):<br>&nbsp;+ Multi-file manifest support with custom `require()` implementation.<br>&nbsp;+ VM sandbox execution context for security isolation. | Completed |
| **Fri** | **Access & Team Controllers** | - Built `accessController.js`: IP whitelist/blacklist rules per workspace.<br>- Built `teamController.js`: team member listing with role hierarchy, invitation system (7-day expiry), role updates, member removal. | Completed |

### 3. Key Results (Deliverables)

#### Technical:
* **Complete Controller Layer:** All 10 controllers implemented with full CRUD and domain-specific operations.
* **Encryption Pipeline:** End-to-end encryption flow:
    1. File uploaded → compressed (gzip) → encrypted (AES-256-GCM) → stored.
    2. User requests script → ECDH handshake → shared secret derived → script encrypted with session key → delivered.
    3. Client loader decrypts with session key → executes in sandbox.
* **Loader System:** Both Python and Node.js loaders functional with:
    * Secure key exchange (X25519 ECDH).
    * Client-side hardware fingerprinting (MAC, hostname, CPU).
    * Transparent script execution with error handling.
* **License Management:** Complete license lifecycle — creation, batch generation, HWID locking, expiration, export.

#### Security:
* **Defense in depth:** Encryption at rest (AES-256-GCM) + encryption in transit (ECDH + AES) + access control (IP/HWID/license) + rate limiting.
* **Zero plaintext exposure:** Script content is never sent in plaintext over the network.

### 4. Issues & Solutions
* **Issue:** ECDH key exchange adds latency to the loader handshake process (~100ms per handshake).
* **Solution:** Accepted the tradeoff — security is more important than marginal latency for a code protection platform. The handshake happens only once per session.

### 5. Lessons Learned
* AES-256-GCM provides both confidentiality and integrity (authenticated encryption), eliminating the need for a separate HMAC step on encrypted data.
* X25519 ECDH is significantly faster than RSA for key exchange while providing equivalent security (128-bit security level).
* Designing loaders for multiple languages (Python, Node.js) reveals the importance of consistent API contracts across implementations.

### 6. Next Steps
* Begin AWS migration — design the serverless architecture.
* Create SAM/CloudFormation template.
* Port SQLite data layer to DynamoDB.
