# Remediation — LAB-01

## Goal
Fix privilege escalation chain, enforce least privilege, prevent S3 abuse.

---

## IAM Fix

### Problem
Role allowed `sts:AssumeRole` from wildcard principals.

### Fix (Terraform)

```hcl
resource "aws_iam_role" "secure_role" {
  name = "SecureRole"
  
  assume_role_policy = jsonencode({
    Version = "2012-10-17",
    Statement = [{
      Effect = "Allow",
      Principal = { AWS = "arn:aws:iam::<account>:role/AppRole" },
      Action = "sts:AssumeRole"
    }]
  })
}
