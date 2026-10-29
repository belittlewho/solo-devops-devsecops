# Part 12 — IaaS, PaaS & SaaS Models

---

## Stack diagram

```mermaid
flowchart TB
  subgraph you [Your responsibility]
    App[Application code]
    Data[Data classification]
    IAM[IAM policies]
  end
  subgraph paas [PaaS boundary]
    Runtime[Runtime/buildpack]
  end
  subgraph iaas [IaaS boundary]
    OS[Guest OS patching]
    FW[Host firewall config]
  end
  subgraph cloud [Provider]
    Hypervisor[Hypervisor/network]
    Physical[Physical DC]
  end
  App --> Runtime
  App --> OS
  Runtime --> Hypervisor
  OS --> Hypervisor
```

---

## Shared responsibility (AWS-style)

| Area | You | Provider |
|------|-----|----------|
| Physical | | ✅ |
| Hypervisor | | ✅ |
| Network config | ✅ | partial |
| OS on EC2 | ✅ | |
| App | ✅ | |
| Managed RDS | patches DB engine | you: SQL, users |
| Lambda | code | runtime patch |

**DevSecOps:** your side includes identity, secrets, app vulns, data encryption choices.

---

## When to pick each

| Need | Pick |
|------|------|
| Learn Linux ops | IaaS VPS |
| Ship fast, low traffic | PaaS |
| Email/calendar | SaaS (Google) |
| Custom kernel modules | IaaS bare metal |
| Compliance data residency | IaaS region choice + your controls |

---

## Vendor lock-in vs velocity

PaaS speeds MVP; export strategy = containers + Postgres dumps + IaC modules.

Document in infra ADR.

Next: [Part 13 — Terraform](13-terraform-iac.md)
