---
title: "Week 2: Storage, Databases & Project Inception"
date: 2026-01-16
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### 1. Objectives

* **Technical Core:** Deep dive into AWS Storage (S3, EBS) and Database (RDS) services; implement a practical file upload system.
* [cite_start]**Project Kick-off:** Finalize the proposal for **"Website Security Baseline Assessment Platform"** – a portable tool for quick security risk assessment[cite: 1, 3, 59].
* **Upskilling:** Enhance NLP knowledge through Coursera certifications to support the AI aspect of the internship.

### 2. Weekly Tasks Breakdown

| Day | Main Task | Details | Status | Links / Evidence |
|:---:|:---|:---|:---:|:---|
| **Mon** | **Storage & Databases** | - Study **S3** (Buckets, lifecycle policies).<br>- Study **EBS** (Volumes, snapshots) & **RDS** (Setup, management).<br>- *Source: Week 2 Curriculum.* | Completed | [Link to Course/Docs] |
| **Tue** | **Hands-on Lab** | - **Build file upload system:**<br>&nbsp;+ Configured S3 bucket for storage.<br>&nbsp;+ Connected backend to S3 for file handling. | Completed | [Link to GitHub/Repo] |
| **Wed** | **Project Proposal** | - [cite_start]**Drafted Proposal:** Defined scope for "Website Security Baseline Assessment Platform".<br>- **Key Features Defined:**<br>&nbsp;+ Basic checks: HTTPS/SSL, Robots.txt [cite: 30, 33][cite_start].<br>&nbsp;+ Vulnerability scanning: SQL Injection, XSS, File Uploads [cite: 38, 39, 52][cite_start].<br>- **Architecture:** Designed portable core (Local/VPS/AWS) independent of cloud infra[cite: 59]. | Completed | [Link to Proposal PDF] |
| **Thu** | **AI/NLP Certification** | - Completed 2 DeepLearning.AI courses on Coursera:<br>&nbsp;1. NLP with Attention Models.<br>&nbsp;2. NLP with Classification and Vector Spaces. | Completed | [Link to Cert 1]<br>[Link to Cert 2] |
| **Fri** | **AWS Specialization** | - Found and started planning for "AWS Fundamentals Specialization".<br>- Weekly team review & retrospectives. | In Progress | [Link to AWS Course] |

### 3. Key Results (Deliverables)

#### Technical & Hands-on:
* **Storage Mastery:** Successfully understood and managed S3 Lifecycles and EBS Snapshots.
* **Practical Implementation:** Built a functional **File Upload System** utilizing AWS S3.

#### Project (Team TheBois):
* **Proposal Finalized:** Completed the proposal for **Website Security Baseline Assessment Platform**.
* [cite_start]**Defined Scope:** Agreed on focusing on "Baseline Assessment" (pre-pentest) to identify common risks like Injection, Broken Access Control, and Security Misconfiguration[cite: 4, 44, 49].
* [cite_start]**Architecture Strategy:** Decided on a flexible architecture where AWS is used for storage/logging, but the core scanning logic remains portable[cite: 66, 67].

#### Certifications & Learning:
* **Coursera Completion:** Earned 2 certificates from DeepLearning.AI (completed Jan 15, 2026):
    * *Natural Language Processing with Attention Models*
    * *Natural Language Processing with Classification and Vector Spaces*

### 4. Issues & Solutions
* **Issue:** [Ví dụ: Difficulty in defining the legal scope for scanning external websites]
* [cite_start]**Solution:** [Ví dụ: Clarified in proposal - "Only perform with explicit written consent" ]