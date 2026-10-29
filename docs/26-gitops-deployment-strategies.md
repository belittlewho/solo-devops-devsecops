# Part 26 — GitOps & Deployment Strategies

---

## GitOps

Desired state in git (manifests, Helm charts) → controller (Argo CD, Flux) syncs cluster.

Benefits: auditable deploys, easy rollback (`git revert`).

**Solo:** overkill before K8s; for VPS use git + CI deploy script first.

---

## Deployment strategies

| Strategy | Downtime | Complexity | Solo fit |
|----------|----------|------------|----------|
| Recreate | yes brief | low | dev |
| Rolling | minimal | medium | Compose, K8s default |
| Blue/green | none | high | two env swap |
| Canary | none | high | traffic split |

---

## Database migrations

- Backward compatible migrations for zero-downtime  
- Run migrate job **before** traffic shift  
- Backup before prod migrate  

---

## Rollback

| Layer | Rollback |
|-------|----------|
| App | previous container tag |
| Config | git revert + redeploy |
| DB | restore dump (last resort) |

Always test rollback in staging.

Next: [Part 27 — Windows contrast](27-windows-infra-contrast.md)
