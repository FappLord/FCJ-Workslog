---
title: "Event 3"
date: 2026-04-04
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# Event 3: Secure Hybrid Access to S3 using VPC Endpoints

### Event Details
| | |
|:---|:---|
| **Date & Time** | April 4, 2026, 9:00 a.m |
| **Location** | Academy Hall, FPT University |
| **Role** | Attendee |

### Event Objectives

- Understand how to securely access Amazon S3 from different environments (cloud and on-premises)
- Learn about VPC Endpoints and their role in private connectivity
- Explore Gateway and Interface Endpoint implementations
- Design hybrid architectures with secure access to AWS services

### Event Description

This workshop focused on how to securely access Amazon S3 from different environments (cloud and on-premises) using VPC Endpoints.

The session introduced how modern cloud architectures can avoid exposing traffic to the public internet while still maintaining efficient and secure communication between services.

---

## Main Content

### 1. Overview of Private Connectivity

The workshop introduced **AWS PrivateLink**, which enables private communication between VPCs and AWS services without using the public internet.

Key ideas:

- Keep traffic inside AWS network
- Improve security and reduce exposure risks
- Ensure stable and low-latency connections

---

### 2. Types of VPC Endpoints

Two main types were presented:

#### Gateway Endpoint

- Used for **Amazon S3 and DynamoDB**
- Route traffic via **route tables**
- No need for public IP
- Cost-effective solution for accessing S3

#### Interface Endpoint

- Uses **Elastic Network Interfaces (ENI)**
- Supports more AWS services
- Uses **DNS resolution**
- Works well for hybrid/on-premises systems
- Enables private access from external networks

---

### 3. Access S3 from VPC

Steps demonstrated:

- Create a **Gateway Endpoint**
- Configure route tables
- Test connection from EC2 to S3

Result:

- EC2 can access S3 privately
- No internet gateway required
- All traffic remains within AWS network

---

### 4. Access S3 from On-Premises

The workshop also simulated hybrid architecture:

- On-premises system connects to AWS via VPC
- Use **Interface Endpoint**
- Configure DNS for service resolution

This allows secure access from external systems into AWS services without exposing them to the public internet.

---

### 5. VPC Endpoint Policies

- Control access at a fine-grained level
- Restrict which resources can be accessed
- Improve security by applying least privilege principle
- Monitor and audit endpoint access

---

## Key Takeaways

From this workshop, I learned that:

- VPC Endpoints are essential for secure cloud architecture
- It is possible to access AWS services without using the public internet
- Gateway and Interface endpoints serve different use cases
- Hybrid architectures require proper DNS and networking setup
- Security can be enhanced using endpoint policies
- Private connectivity reduces attack surface and improves overall system security

---

## Personal Experience

This workshop helped me better understand how networking works in AWS, especially in secure and enterprise environments.

I found it very useful because it relates directly to real-world systems where security and data privacy are critical.

The knowledge gained is highly applicable to my current project, especially when working with AWS services like S3 and designing a secure architecture for the GuardScript platform.

---

## Conclusion

This event provided practical knowledge on how to build secure and scalable architectures using VPC Endpoints.

It strengthened my understanding of AWS networking and gave me a clearer view of how to design systems that are both efficient and secure.

The concepts learned here directly support building enterprise-grade cloud solutions with minimal exposure to public internet threats.
