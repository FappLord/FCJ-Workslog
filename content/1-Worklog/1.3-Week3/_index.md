---
title: "Week 3: Networking & Infrastructure Security"
date: 2026-01-19
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### 1. Objectives

* **Networking Mastery:** Understand the core of AWS networking including VPC architecture, subnetting, and network security boundaries (SGs vs NACLs).
* **Infrastructure Foundation:** Configure Internet Gateways (IGW) and NAT Gateways to manage traffic for the "Website Security Baseline Assessment Platform".
* **Advanced AI/NLP:** Finalize the NLP specialization by mastering Sequence Models to support future AI integration in the project.

### 2. Weekly Tasks Breakdown

| Day | Main Task | Details | Status | Links / Evidence |
|:---:|:---|:---|:---:|:---|
| **Mon** | **Networking Core** | - **Deep Dive VPC:** Studied VPC concepts, CIDR blocks, and Subnetting (Public vs. Private).<br>- **Connectivity:** Configured Internet Gateway (IGW) for public access and NAT Gateway for private instances.<br>- *Source: Week 3 Curriculum.* | Completed | \ |
| **Tue** | **NLP Certification** | - Completed the final course of the specialization:<br>&nbsp;**Natural Language Processing with Sequence Models**.<br>- Covered RNNs, LSTMs, and GRUs for advanced text processing. | Completed | [Link to Cert](https://www.coursera.org/account/accomplishments/verify/MKFJD7RKYZC0) |
| **Wed** | **AWS Specialization** | - Continued the **"AWS Fundamentals Specialization"** on Coursera.<br>- Focused on modules related to AWS core services and security concepts. | In Progress | [Link to AWS Fundamentals Specialization](https://www.coursera.org/programs/fptu-spring-2026-6010y/specializations/aws-fundamentals?source=search) |
| **Thu** | **Project Infrastructure** | - Evaluated network requirements for the **Website Security Baseline Assessment Platform**.<br>- Discussed with team *TheBois* on how to isolate the scanning engine using VPC for security. | Completed | \ |
| **Fri** | **Network Security** | - **Security Layers:** Analyzed differences between Security Groups (Stateful) and NACLs (Stateless).<br>- **Lab:** Set up a secure VPC environment for potential future project deployment. | Completed | \ |

### 3. Key Results (Deliverables)

#### Technical & Hands-on:
* **VPC Architecture:** Successfully designed a custom VPC with public/private subnets, ensuring a secure network topology.
* **Traffic Management:** Implemented Route Tables, IGW, and NAT Gateways to control inbound/outbound traffic effectively.
* **Security Posture:** Clearly distinguished usage scenarios for Security Groups (instance level) versus NACLs (subnet level).

#### Project (Team TheBois):
* **Infrastructure Strategy:** Aligned the networking setup with the **Website Security Baseline Assessment Platform** needs—ensuring the scanning tool operates in a controlled environment to prevent unintended exposure during vulnerability checks.

#### Certifications & Learning:
* **Coursera Completion:** Earned the certificate from DeepLearning.AI:
    * *Natural Language Processing with Sequence Models*
    * *(This marks the completion of the NLP Specialization - Optional Note)*

### 4. Issues & Solutions
* **Issue:** Confusion between stateful (Security Groups) and stateless (NACLs) rules during the lab setup.
* **Solution:** Conducted a connectivity test (ping) to observe how return traffic is handled, clarifying that SGs automatically allow return traffic while NACLs do not.