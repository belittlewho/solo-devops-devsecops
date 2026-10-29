# Part 25 — Compliance Hooks & Audit Logging

Not legal advice — **operational patterns** for SOC2-ish readiness.

---

## Audit log properties

- **Who** did **what** **when** on **which** resource  
- Append-only or WORM storage for sensitive domains  
- Tamper-evident (ship to central SIEM)  

App events: login, permission change, payment, data export.

---

## Linux auth audit

`/var/log/auth.log` — SSH successes/failures  
Ship with **Vector**, **Fluent Bit**, or cloud agent.

---

## Retention

Define policy: 90 days hot, 1 year cold — cost in object storage lifecycle rules.

---

## Access reviews

Quarterly: who has SSH, cloud admin, DB superuser — document in spreadsheet.

---

## GDPR/privacy ops

- Data export/delete endpoints if you store PII  
- DPA with processors (hosting, email)  

Pair with your [requirements guide](https://github.com/belittlewho/solo-software-project-management) NFR catalog.

Next: [Part 26 — GitOps & deployment](26-gitops-deployment-strategies.md)
