# Part 40 — Cloud VPC, IAM Policies & Object Storage

AWS-centric; map to GCP VPC / Azure VNet mentally.

---

## VPC pattern (3-tier)

```
Internet
   → IGW
   → Public subnet (ALB, NAT gateway)
   → Private subnet (app EC2/ECS)
   → Private subnet (RDS, no internet)
```

**NAT gateway:** private subnets reach internet for updates without inbound exposure.

**Peering:** connect two VPC CIDRs non-overlapping (10.0.0.0/16 ↔ 10.1.0.0/16).

---

## IAM policy example (least privilege CI deploy)

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": ["ecr:GetAuthorizationToken", "ecr:BatchCheckLayerAvailability", "ecr:PutImage"],
      "Resource": "*"
    },
    {
      "Effect": "Allow",
      "Action": ["ecs:UpdateService", "ecs:DescribeServices"],
      "Resource": "arn:aws:ecs:region:account:service/cluster/*"
    }
  ]
}
```

Review with [IAM policy simulator](https://policies.simulator.aws.amazon.com/).

GitHub OIDC trust policy on role — no long-lived keys (Part 20).

---

## S3 bucket hardening

```hcl
resource "aws_s3_bucket_public_access_block" "b" {
  bucket                  = aws_s3_bucket.app.id
  block_public_acls       = true
  block_public_policy     = true
  ignore_public_acls      = true
  restrict_public_buckets = true
}
```

Bucket policy: allow CloudFront OAC only; deny insecure transport.

---

## Landing zone (org)

- AWS Organizations: separate accounts staging/prod  
- SCPs: deny root, restrict regions  
- Central CloudTrail log bucket  

Overkill until revenue; know the names.

Next: [Part 41 — Managed services & serverless](41-cloud-managed-services-serverless.md)
