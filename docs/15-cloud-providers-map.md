# Part 15 — Cloud Providers Map (AWS / GCP / Azure)

Conceptual map — not certification prep. Pick **one** cloud for depth.

---

## Universal building blocks

| Concept | AWS | GCP | Azure |
|---------|-----|-----|-------|
| VM | EC2 | Compute Engine | Virtual Machines |
| Object storage | S3 | GCS | Blob Storage |
| Managed SQL | RDS | Cloud SQL | Azure SQL |
| VPC | VPC | VPC | VNet |
| IAM | IAM | Cloud IAM | Entra + RBAC |
| DNS | Route53 | Cloud DNS | Azure DNS |
| LB | ALB/NLB | Cloud LB | App Gateway |
| Container | ECS/EKS | GKE/Cloud Run | AKS/Container Apps |
| Secrets | Secrets Manager | Secret Manager | Key Vault |
| CI | CodePipeline | Cloud Build | DevOps |

All run **Linux guests** except Windows SKUs.

---

## Solo cost-conscious path

1. Single region  
2. Small VM or PaaS free tier  
3. S3-compatible R2/B2 for backups  
4. Budget alerts Day 1  

Part 28 FinOps.

---

## Identity (critical DevSecOps)

- Humans: MFA, no root daily  
- CI: OIDC federation to role  
- App: instance role / workload identity — no static keys on disk  

Part 20.

---

## Landing zone (future team)

- Org account / billing  
- Separate staging/prod accounts  
- Central logging bucket  

Overkill for first VPS — grow into it.

Next: [Part 16 — Bare metal & homelab](16-bare-metal-vms-homelab.md)
