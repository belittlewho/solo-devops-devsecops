# Part 47 — Platform Engineering & Internal Developer Platforms

---

## What is an IDP

**Internal Developer Platform:** self-service layer on top of K8s/cloud — devs deploy without filing infra tickets for every env var.

---

## Golden paths

Opinionated templates:

- `service-node-api` → repo scaffold + CI + Helm + observability wired  
- `service-static-site` → CDN + CI  

Document in Backstage catalog or internal docs site.

---

## Backstage (Spotify OSS)

Software catalog YAML:

```yaml
apiVersion: backstage.io/v1alpha1
kind: Component
metadata:
  name: my-api
spec:
  type: service
  lifecycle: production
  owner: team-a
```

Plugins: scaffolder creates repos from templates; TechDocs hosts runbooks.

Solo: lightweight catalog markdown in monorepo until team grows.

---

## Multi-team tenancy on Kubernetes

- Namespace per team  
- ResourceQuota + LimitRange  
- RBAC RoleBinding per namespace  
- NetworkPolicy deny cross-namespace  
- Cost allocation labels  

Policy engines: Kyverno, OPA Gatekeeper.

---

## Platform team metrics

Developer satisfaction surveys; deployment frequency per team; lead time vs golden path adoption.

Next: [Part 48 — HA & autoscaling](48-high-availability-autoscaling.md)
