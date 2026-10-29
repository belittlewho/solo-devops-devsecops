# Part 19 — Backup, Disaster Recovery & Runbooks

---

## RPO & RTO

| Term | Meaning |
|------|---------|
| **RPO** | Max data loss (backup age) |
| **RTO** | Max downtime to restore |

Solo starter: RPO 24h, RTO 4h — daily DB dump + infra in git.

---

## What to backup

| Asset | Method |
|-------|--------|
| Database | `pg_dump` cron → encrypted object storage |
| Uploads | rsync/rclone to S3 |
| Secrets | password manager + vault export |
| IaC | git |
| Server config | Ansible in git |

**Test restore quarterly** — untested backup = wish.

---

## 3-2-1 rule

3 copies, 2 media types, 1 offsite.

---

## Disaster scenarios

| Event | Response |
|-------|----------|
| VPS dead | Terraform new VM + Ansible + restore DB |
| Bad deploy | Rollback image tag |
| Credential leak | Rotate keys, audit logs |

Template: [runbook.md](../templates/runbook.md)

Next: [Part 20 — Secrets & IAM](20-secrets-identity-iam.md)
