# LAB-01 — IAM Misconfiguration → Privilege Escalation → S3 Exfiltration

**Objective:** Build a vulnerable AWS environment, exploit it using legitimate AWS APIs, then fix it.

**Attack Surface:**
- EC2 instance with over-permissive IAM role
- S3 bucket with weak policy
- CloudTrail enabled

**Tools Used:**
- AWS CLI
- Pacu
- Terraform

**Artifacts:**
- /terraform/main.tf
- /exploit_steps.md
- /remediation.md

This lab is intentionally insecure and must never be used in production.

