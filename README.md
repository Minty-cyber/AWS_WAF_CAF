# AWS Well-Architected & Cloud Adoption Framework Lab


## Project Overview

This labs focuses on migrating a **two-tier web application** (frontend web servers + backend database) from on-premises to AWS.

The work demonstrates a structured, best-practice approach using:
- The **AWS Well-Architected Framework (WAF)** — evaluating and improving the workload across its **six pillars** (Operational Excellence, Security, Reliability, Performance Efficiency, Cost Optimization, and Sustainability)
- The **AWS Cloud Adoption Framework (CAF)** — assessing organizational readiness across its **six perspectives** (Business, People, Governance, Platform, Security, Operations)

## Key Deliverables in This Repository

- **`aws_waf_caf_assessment.md`**  
  Full report covering all lab tasks:
  - Task 1: Review of existing (lift-and-shift) architecture + risks/weaknesses
  - Task 2: WAF evaluation table (six pillars: one strength, one improvement, recommendation, AWS service per pillar)
  - Task 3: CAF readiness analysis (~150–200 words per perspective)
  - Task 4: Description of the improved architecture + how it addresses all WAF pillars
  - Brief reflection (150+ words) on key learnings

- **`architecture-diagram.png`** (or `.drawio` source file)  
  Visual diagram of the **revised, production-ready architecture** created in lucide chart

- This **README.md** — explains the overall approach and how the submission meets the lab objectives

## Architecture Diagram

![Two-Tier Web Application Architecture](architecture-diagram.png)

**High-level overview of the improved design**:
- Global edge delivery: **Amazon Route 53** (DNS) + **Amazon CloudFront** (CDN) + **AWS WAF** (web protection)
- Traffic distribution: **Application Load Balancer (ALB)** in public subnets
- Web tier: **EC2 instances** in **Auto Scaling Group (ASG)** across multiple Availability Zones (public subnets)
- Database tier: **Amazon RDS Multi-AZ** (master + synchronous standby) in private subnets
- Security: Least-privilege security groups, private subnets for DB, no public SSH
- Multi-AZ redundancy for high availability and failover

## My Approach

I followed the lab tasks step-by-step while applying AWS best practices:

1. **Task 1** — Analyzed the hypothetical lift-and-shift deployment (single-AZ EC2 + RDS, open ports, no load balancing, etc.) and listed components + risks.
2. **Task 2** — Evaluated against the six WAF pillars (updated framework), identifying realistic strengths/improvements and recommending specific AWS services.
3. **Task 3** — Assessed organizational maturity across all six CAF perspectives with actionable enablers (e.g., CCoE, training, Control Tower, least-privilege IAM).
4. **Task 4** — Designed a modern architecture (shown above) that:
   - Uses multi-AZ for Reliability
   - Enforces defense-in-depth for Security
   - Scales elastically for Performance & Cost
   - Minimizes waste for Sustainability
   - Automates and monitors for Operational Excellence
5. **Reflection** — Summarized key learnings about frameworks, and the holistic cloud adoption.

## Tools & References Used

- Diagram tool: Lucidchart
- AWS Documentation:
  - [Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html)
  - [Cloud Adoption Framework](https://aws.amazon.com/cloud-adoption-framework/)
  - VPC, ALB, Auto Scaling, RDS Multi-AZ, CloudFront, WAF best practices
