---
title: "Week 4: Identity, Security & re:Invent Updates"
date: 2026-01-26
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### 1. Objectives

* **Security & Identity:** Master AWS Identity and Access Management (IAM) to secure the team's environment. Focus on granular permissions (Policies), Roles, and MFA enforcement.
* **Technology Update:** Update knowledge with the latest innovations from **AWS re:Invent 2025** (Event on Jan 27).
* **Project Integration:** Evaluate new features (S3 Vector, Bedrock Agents) for potential integration into the **Website Security Baseline Assessment Platform**.

### 2. Weekly Tasks Breakdown

| Day | Main Task | Details | Status | Evidence |
|:---:|:---|:---|:---:|:---|
| **Mon** | **IAM Core Concepts** | - **Users & Groups:** Created individual IAM users for team TheBois (Binh, Tri, Hien, Tung, Vinh).<br>- **Groups:** Organized users into functional groups (Dev, Admin, Audit) to manage permissions efficiently. | Completed | \ |
| **Tue** | **AWS Event** | - **Event:** Attended "AWS re:Invent 2025 Recap" (Jan 27, 2026).<br>- **Summary:** Updates on GenAI (Bedrock Agents), SageMaker Unified Studio, and S3 optimizations.<br>*(See detailed Event Participated for more info)* | Completed | \ |
| **Wed** | **Policies & Security** | - **Permissions:** Crafted JSON Policies (Least Privilege) restricting access to specific S3 buckets and EC2 instances.<br>- **Security Hardening:** Enforced **MFA (Multi-Factor Authentication)** for the Root account and all IAM users. | Completed | \ |
| **Thu** | **Tech Evaluation** | - Analyzed **S3 Vector** and **S3 Tables** for cost-effective log storage and retrieval in the Security Platform project.<br>- Explored **Bedrock Agents** capabilities for automating security scan workflows. | Completed | \ |
| **Fri** | **AWS Specialization** | - Continued progress on **AWS Fundamentals Specialization** (Coursera).<br>- Reviewed security best practices learned in Week 3 (VPC) vs Week 4 (IAM). | In Progress | \ |

### 3. Key Results (Deliverables)

#### Technical & Hands-on:
* **IAM Infrastructure:** Fully configured a secure access environment.
    * **Users/Groups:** Created and assigned.
    * **Policies:** Custom policies applied to ensure developers can only access resources relevant to "Website Security Baseline Assessment Platform".
    * **MFA:** 100% enforcement across the team.
* **Security Posture:** Eliminated the use of Root Account for daily tasks.

#### Knowledge Update (Event Summary):
* **GenAI & Data:** Gained high-level insights into Bedrock Agents and S3 Vector from the AWS re:Invent Recap event.
* **Application:** Identified potential to use **Cognito** and **S3 Vector** for the project's backend.
* *(Note: A detailed summary of the sessions and speakers is documented separately.)*

### 4. Issues & Solutions
* **Issue:** Complexity in writing custom JSON Policies for specific resource restrictions (ARN formatting).
* **Solution:** Used the **AWS Policy Generator** tool to draft the initial policy, then manually refined the JSON to match the specific S3 bucket names of the project.