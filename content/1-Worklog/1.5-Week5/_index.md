---
title: "Week 5: Serverless Deep Dive & Project Ideation"
date: 2026-02-02
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### 1. Objectives

* **Serverless Mastery:** Deep dive into AWS Lambda, API Gateway, and DynamoDB — the core serverless building blocks.
* **Certification Progress:** Continue the AWS Fundamentals Specialization on Coursera.
* **Project Ideation:** Brainstorm and evaluate project ideas with Team TheBois for the main FCJ internship project.
* **Pre-Tet Wrap-Up:** Consolidate learning from Weeks 1–4 before the Tet holiday break.

### 2. Weekly Tasks Breakdown

| Day | Main Task | Details | Status |
|:---:|:---|:---|:---:|
| **Mon** | **Lambda Deep Dive** | - Studied AWS Lambda execution model, cold starts, and pricing.<br>- Explored Lambda function URLs as lightweight API endpoints.<br>- Practiced creating Lambda functions with Node.js runtime. | Completed |
| **Tue** | **API Gateway & DynamoDB** | - Studied API Gateway REST vs HTTP API differences.<br>- Deep dive into DynamoDB: partition keys, sort keys, GSIs, and query patterns.<br>- Explored DynamoDB's PAY_PER_REQUEST billing mode. | Completed |
| **Wed** | **Hands-on Lab** | - Built a simple serverless REST API:<br>&nbsp;+ Lambda function handling CRUD operations.<br>&nbsp;+ DynamoDB table as data store.<br>&nbsp;+ Tested via Lambda Function URL. | Completed |
| **Thu** | **Project Brainstorming** | - Team TheBois meeting to discuss project directions.<br>- Evaluated ideas: secure code distribution, license management, cloud-based code editor.<br>- Initial concept for **GuardScript** — a platform to securely distribute and protect source code with licensing. | Completed |
| **Fri** | **Pre-Tet Review** | - Consolidated notes from Weeks 1–5.<br>- Continued AWS Fundamentals Specialization (Coursera).<br>- Prepared task backlog for post-Tet work.<br>- *Note: Tet holiday break starts next week (2 weeks off).* | Completed |

### 3. Key Results (Deliverables)

#### Technical:
* **Serverless Knowledge:** Gained practical understanding of the Lambda + API Gateway + DynamoDB stack, which would later form the foundation for the GuardScript AWS deployment.
* **Hands-on Practice:** Successfully built and tested a serverless CRUD API, validating the feasibility of a Lambda-based backend architecture.

#### Project (Team TheBois):
* **Concept Defined:** Identified the core idea for **GuardScript** — a secure code distribution platform addressing the problem of unauthorized code redistribution.
* **Initial Feature List:** Brainstormed key features: encrypted script delivery, license management, hardware ID locking, workspace isolation, access control.

### 4. Issues & Solutions
* **Issue:** DynamoDB query patterns require careful upfront design of partition keys and GSIs, unlike SQL where ad-hoc queries are straightforward.
* **Solution:** Studied the Single-Table Design vs Multi-Table Design patterns. Decided that a multi-table approach with targeted GSIs would be cleaner for the GuardScript use case.

### 5. Lessons Learned
* Serverless architecture requires a different mindset than traditional server-based design — statelessness, cold starts, and pay-per-use pricing all influence architecture decisions.
* DynamoDB schema design must be query-driven, not entity-driven.

### 6. Next Steps
* Enjoy Tet holiday break (2 weeks).
* Return with a finalized project scope for GuardScript.
* Begin architecture design and development planning.
