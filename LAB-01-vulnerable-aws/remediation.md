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
S3 Fix

Disable public access

Add bucket policy restricting IAM principals
resource "aws_s3_bucket_public_access_block" "default" {
  bucket = aws_s3_bucket.vuln.id

  block_public_acls   = true
  block_public_policy = true
  ignore_public_acls  = true
  restrict_public_buckets = true
}
Detection

Enable logging for:

AssumeRole

ListRoles

GetRole

S3:GetObject

Add CloudWatch alarm for unusual role assumptions.
Validation

Attempt same exploit again — should fail

Confirm logs show denied request

Run Pacu again → no privilege escalation path

This shows you understand *fixing*, not just breaking.

---

## **05 — GitHub Action: terraform validate**

`.github/workflows/terraform.yml`

```yaml
name: Terraform Validation

on: [pull_request]

jobs:
  validate:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: hashicorp/setup-terraform@v1
      - run: terraform init ./LAB-01-vulnerable-aws/terraform
      - run: terraform validate ./LAB-01-vulnerable-aws/terraform
