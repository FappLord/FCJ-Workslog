---
title: "Self-Assessment"
date: 2026-03-26
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Self-Assessment

During my internship at **Amazon Web Services Vietnam** as part of the **First Cloud AI Journey 2026** program (05/01/2026 – 18/04/2026), I had the opportunity to apply and significantly deepen my understanding of cloud-native development in a real project context.

As **Team Lead** of Team TheBois, I led the design and end-to-end implementation of **GuardScript** — a serverless script distribution platform with loader-based access control deployed on AWS. This involved hands-on work across architecture design, backend development (Node.js Lambda), infrastructure as code (AWS SAM / CloudFormation), security implementation (HMAC, ECDH, AES-GCM), and frontend integration.

Throughout the program I consistently pushed myself beyond comfort, tackling challenges in cryptographic protocol design, DynamoDB multi-table modeling, CloudFront behavior configuration, and real-time WebSocket integration — areas that were largely new to me at the outset.

---

## Self-Evaluation Table

| No. | Criteria | Description | Good | Fair | Average |
|:---:|---|---|:---:|:---:|:---:|
| 1 | **Professional knowledge & skills** | Applying AWS services, Node.js, security algorithms, IaC in a real project | ✅ | ☐ | ☐ |
| 2 | **Ability to learn** | Absorbing new services and concepts (X25519 ECDH, SAM, CloudFront behaviors) quickly | ✅ | ☐ | ☐ |
| 3 | **Proactiveness** | Self-directed research, proposing architecture decisions, raising blockers early | ✅ | ☐ | ☐ |
| 4 | **Sense of responsibility** | Delivering sprint tasks on time, owning design decisions as Team Lead | ✅ | ☐ | ☐ |
| 5 | **Discipline** | Adhering to sprint schedules and team commitments | ☐ | ✅ | ☐ |
| 6 | **Progressive mindset** | Actively seeking feedback on architecture and security design | ✅ | ☐ | ☐ |
| 7 | **Communication** | Writing documentation, presenting technical decisions clearly to the team | ☐ | ✅ | ☐ |
| 8 | **Teamwork** | Coordinating task distribution across 6 team members, unblocking teammates | ✅ | ☐ | ☐ |
| 9 | **Professional conduct** | Maintaining respectful, constructive collaboration throughout the program | ✅ | ☐ | ☐ |
| 10 | **Problem-solving skills** | Diagnosing system issues, iterating on security protocol design | ☐ | ✅ | ☐ |
| 11 | **Contribution to project/team** | Core architect and primary implementer of GuardScript | ✅ | ☐ | ☐ |
| 12 | **Overall** | Delivered a complete, production-grade serverless platform within the internship period | ✅ | ☐ | ☐ |

---

## Areas for Improvement

1. **Discipline & time management** — Sprint deadlines were met, but task estimation accuracy and buffer planning need improvement for larger-scale work.
2. **Technical communication** — I can explain architecture well one-on-one but need to improve at writing concise, audience-appropriate summaries for non-technical stakeholders.
3. **Delegation** — As Team Lead, I tended to take on too many implementation tasks myself rather than distributing more evenly across the team.
4. **Testing discipline** — More emphasis on automated testing (unit, integration) from the start of development would have caught several edge cases earlier.

---

## Key Takeaways

- Building a production-quality serverless system requires careful attention to IAM scoping, TTL-based cleanup, and security at every layer.
- AWS SAM + CloudFormation significantly reduces deployment complexity but requires a thorough understanding of resource dependencies.
- Real-time features (WebSocket API) add meaningful user experience value but introduce connection-state management complexity.
- The FCJ program provided an environment where I could take genuine technical ownership — a rare opportunity that accelerated my growth considerably.
