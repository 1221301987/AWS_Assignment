# Secure Migration of a Legacy Employee Directory to AWS

This repository contains all artefacts for *CCS6344 – Database and Cloud Security, Assignment 2* (Group 49).

## Team & Contribution Split (33.33 % each)
| Student | ID | Key Responsibilities |
|---------|----|----------------------|
| **AL REFAI, AL BARAA** | 1221301987 | Cloud architecture design, Infrastructure-as-Code (legacy-stack.yml), security testing (CLI) |
| **Youssef Fathy Fathy Mahrous Elsakkar** | 1221302092 | Application refactor & hardening, migration to AWS (EC2, RDS), documentation (report & diagrams) |
| **Bin Afeef, Abdullah Omar Hamad** | 1211306604 | VPC & network security, logging/monitoring (CloudTrail, CloudWatch), video demonstration |

## Repository Structure
```
employee-app/           # PHP legacy application (cleaned & ready for AWS)
legacy-stack.yml        # CloudFormation template used in the report
README.md               # You are here
```

## How to Deploy
1.  Clone the repo and change into the directory.
2.  Deploy the CloudFormation template:
    ```bash
    aws cloudformation deploy \
        --template-file legacy-stack.yml \
        --stack-name legacy-employee-app \
        --capabilities CAPABILITY_NAMED_IAM
    ```
3.  Upload `employee-app` code to the created EC2 instances **or** bake into an AMI/container as required.

## Sandbox Limitations
Due to AWS Academy Sandbox restrictions, the following features could **not** be implemented. They are documented in the report and accounted for in the architecture but left disabled in code:
1. **AWS WAF** – service unavailable in sandbox (would provide SQLi/XSS protection).
2. **CloudFront CDN** – restricted; production would add edge security & global cache.
3. **AWS Inspector** – not accessible; production would run continuous vulnerability scans.
4. **Advanced SSL/TLS (ACM)** – custom certificate management limited; production would use ACM.
5. **DevSecOps Pipeline** (CodePipeline/CodeBuild) – sandbox blocks these services.
6. **Multi-Region Deployment** – sandbox limited to a single region; production would add DR.
7. **Advanced CloudWatch Dashboards** – some premium monitoring features restricted.

These restrictions do **not** impact the core security principles demonstrated.

## Demo Video
Presentation & live demo: **https://youtu.be/zqWv2mHKVfI**

---
© 2025 Group 49. 