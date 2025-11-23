# Aidil — Cloud Security Portfolio

I build, break and secure cloud environments (AWS focus).
This repo contains hands-on labs, exploit chains, remediation steps, Terraform modules, and automation tools.

The goal: demonstrate real-world security capability through reproducible labs.

---

## 🔥 Current Labs

| Lab | Description | Status | Link |
|-----|-------------|--------|------|
| LAB-01 | IAM misconfig → role abuse → S3 data exfiltration | In Progress | /LAB-01-vulnerable-aws |
| LAB-02 | Public EC2 metadata exposure → SSRF → privilege escalation | Planned | /LAB-02-metadata |
| LAB-03 | S3 bucket takeover via misconfigured policy | Planned | /LAB-03-s3-takeover |

---

## 🛠 Tools

| Tool | Purpose |
|------|---------|
| iam_scanner.py | Enumerate role trust relationships |
| recon.sh | Basic AWS recon (bash) |

---

## 🏗 Infrastructure Modules

| Module | Purpose |
|--------|---------|
| secure-iam/ | Secure IAM baseline (least privilege + no wildcards) |
| logging/ | CloudTrail + S3 log storage config |

---

## 📚 Learning Log

I write nightly logs documenting what I learned.

- /logs/
- Topics: IAM, VPC, GuardDuty, Terraform, Pacu, SSRF, lateral movement

---

### Contact
- Email: <your-email>
- GitHub: https://github.com/<username>
- Region: Malaysia
