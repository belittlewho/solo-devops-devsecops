# Part 9 — Kubernetes Concepts (When & Why)

Kubernetes (K8s) orchestrates containers across **many** nodes. Powerful; expensive in complexity.

---

## Use K8s when

- Many microservices (10+) with independent scaling  
- Need self-healing, rolling updates at scale  
- Team knows YAML ops or uses managed K8s  

## Skip K8s when (solo/small)

- Single VPS + Compose suffices  
- MVP on PaaS  
- You lack time for cluster upgrades  

**Rule:** Compose until pain proves K8s — not resume-driven.

---

## Core objects (vocabulary)

| Object | Role |
|--------|------|
| Pod | 1+ containers, smallest deploy unit |
| Deployment | Desired replicas, rolling update |
| Service | Stable network to pods |
| Ingress | HTTP routing + TLS |
| ConfigMap / Secret | Config & secrets (base64 not encryption!) |
| Namespace | Isolation boundary |

---

## Managed vs self-hosted

| | EKS/GKE/AKS | k3s on VPS |
|--|-------------|------------|
| Control plane | Provider | You |
| Cost | $$$ | $ + your time |
| Upgrades | Easier | Your problem |

---

## DevSecOps on K8s

- RBAC least privilege  
- NetworkPolicies  
- Pod Security Standards  
- Scan images in CI  
- Sealed Secrets / External Secrets Operator  

Part 24 touches runtime.

Next: [Part 10 — Reverse proxy](10-reverse-proxy-web.md)
