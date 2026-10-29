# Part 24 — Runtime Security & Zero Trust (Lite)

**Zero trust:** never assume safe network — verify every request.

---

## Linux VPS runtime

| Control | Implementation |
|---------|----------------|
| Network segmentation | Docker networks; DB not public |
| mTLS | service mesh (advanced) or Cloudflare Tunnel |
| WAF | Cloudflare, AWS WAF in front |
| Rate limit | nginx `limit_req` |
| App auth | OAuth2, session hardening |

---

## Container runtime

- Don't mount `/var/run/docker.sock` in app container  
- Read-only root filesystem where possible  
- Drop capabilities (`cap_drop: ALL`)  

---

## Kubernetes runtime

- NetworkPolicy deny-all default  
- Pod Security: restricted  
- OPA/Gatekeeper policies  

---

## Incident response (solo)

1. Detect (alert)  
2. Contain (block IP, disable key)  
3. Eradicate (patch, redeploy clean image)  
4. Recover (restore backup)  
5. Learn (runbook update)  

Log retention Part 25.

Next: [Part 25 — Compliance & audit logging](25-compliance-logging-audit.md)
