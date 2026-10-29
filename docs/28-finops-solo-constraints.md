# Part 28 — FinOps & Solo Constraints

---

## Cost hierarchy (cheap → expensive)

1. Static site on CDN free tier  
2. Single small VPS + Compose  
3. Managed DB add-on  
4. Multi-AZ + K8s + observability stack  

Match spend to **revenue or learning budget**.

---

## Alerts

- AWS/GCP/Azure budget 50/80/100%  
- Monitor egress (S3/API) surprises  

---

## Right-sizing

- Start CX22/2GB RAM; scale on metrics not guesses  
- Stop dev VMs nights (homelab)  

---

## Reserved vs spot

- **Reserved** stable prod  
- **Spot** batch jobs tolerant to kill  

---

## Free tier traps

- Expiring credits → billing shock — calendar reminder  

---

## Time vs money

PaaS costs more $, less hours. Raw Linux costs less $, more learning (this guide).

Document choice in infra ADR.

Next: [Part 99 — FAQ](99-faq-cheatsheet.md)
