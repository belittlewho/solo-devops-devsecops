# Part 37 — Service Mesh (Istio / Linkerd)

Use when **many internal services** need mTLS, traffic splitting, observability without app code changes.

---

## Linkerd (lighter solo/homelab)

```bash
linkerd install | kubectl apply -f -
linkerd inject deployment.yaml | kubectl apply -f -
linkerd viz dashboard
```

Automatic mTLS between meshed pods.

---

## Istio (heavier)

VirtualService, DestinationRule for canaries:

```yaml
# 90% v1, 10% v2 traffic split concept
```

Install via `istioctl`; resource hungry — not for tiny clusters.

---

## When skip mesh

Single monolith or 2 services behind nginx — mesh adds ops cost without benefit.

---

## ECS/Fargate recap

Task networking awsvpc; service connect for service mesh lite on AWS — alternative to self-managed Istio.

Next: [Part 38 — Terraform advanced](38-terraform-advanced-policy.md)
