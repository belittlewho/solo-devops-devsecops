# Part 41 — Managed DB, Cache, Queues, Lambda & CloudFront

---

## RDS / Cloud SQL ops

| Task | Practice |
|------|----------|
| Params | Parameter groups; `max_connections` |
| Backups | Automated retention; test restore |
| Failover | Multi-AZ RDS — DNS endpoint same |
| Minor version | Auto minor upgrade window |
| Monitoring | Enhanced monitoring, Performance Insights |

Never expose 5432 to 0.0.0.0; security group app tier only.

---

## ElastiCache / Memorystore (Redis)

Use for cache/session; **no source of truth** without persistence config (AOF/RDB). Eviction policy `allkeys-lru` for cache.

---

## SQS / SNS / EventBridge

```
API → SQS queue → worker service → DLQ on fail
SNS → fan-out email/SMS/lambda
EventBridge → cron + event bus between AWS services
```

GCP: Pub/Sub. Azure: Service Bus.

---

## Lambda / Cloud Functions ops

| Concern | Mitigation |
|---------|------------|
| Cold start | Provisioned concurrency |
| Timeout | Set below client timeout |
| Secrets | Secrets Manager + IAM role |
| VPC access | ENI cold start penalty |
| Observability | CloudWatch logs/metrics |

Package as container image for large deps.

---

## CloudFront + S3 static site

1. S3 bucket private  
2. CloudFront OAC  
3. ACM cert in **us-east-1** for CloudFront  
4. Route53 alias to distribution  

Dynamic API stays on ALB/ECS separate from static.

---

## EKS managed (lab outline)

Terraform: `module "eks"`. Node group or Fargate profiles. Add-ons: VPC CNI, CoreDNS, kube-proxy. CI: `kubectl set image` or Helm via GitOps.

Details: Parts 36, 50, 52.

Next: [Part 42 — PostgreSQL](42-postgresql-operations.md)
