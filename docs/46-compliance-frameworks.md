# Part 46 — SOC 2, PCI-DSS & HIPAA Mapping (Ops View)

Not legal advice — **control areas** DevOps engineers implement.

---

## SOC 2 Trust Services Criteria (common)

| Criteria | DevOps evidence |
|----------|-----------------|
| Security | IAM, MFA, patching, vuln scan |
| Availability | SLO, backups, DR drill logs |
| Confidentiality | Encryption at rest/transit |
| Processing integrity | CI tests, change management |
| Privacy | PII handling (if applicable) |

Auditors ask for: policies, access lists, ticket history, sample deploy logs.

---

## PCI-DSS (if you touch cards)

**Goal:** never store PAN; use Stripe/Adyen hosted fields.

Ops controls: network segmentation, file integrity monitoring, logging, quarterly scans, ASV external scan.

---

## HIPAA (health data)

BAA with cloud vendor; encryption; audit logs; minimum necessary access. Often **avoid** self-host until compliance advisor engaged.

---

## Mapping template

| Control ID | Requirement | Implementation | Evidence location |
|------------|-------------|----------------|-------------------|
| CC6.1 | Logical access | SSO+MFA | IdP export |
| A1.2 | Backup | pg_dump cron | S3 lifecycle + restore ticket |

Extend Part 25 audit logging for retention periods auditors expect (often 1 year).

Next: [Part 47 — Platform engineering](47-platform-engineering-idp.md)
