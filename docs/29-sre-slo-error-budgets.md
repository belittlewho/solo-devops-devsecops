# Part 29 — SLI, SLO & Error Budgets

Template: [templates/slo-document.md](../templates/slo-document.md)

---

## Definitions

| Term | Meaning |
|------|---------|
| **SLI** | Service Level Indicator — measurable signal (availability, latency) |
| **SLO** | Service Level Objective — target range for SLI (99.5% / 30d) |
| **SLA** | Contract with customer; penalties — rarely for solo |
| **Error budget** | Allowed unreliability: `1 - SLO` |

If SLO is 99.9% monthly, budget ≈ 43 minutes downtime/month.

---

## Worked example: API on VPS

**SLI (availability):** ratio of successful health checks  
**Measurement:** synthetic probe every 60s from Better Stack + app `/health` returns 200  

**SLO:** 99.5% of checks succeed over 30 rolling days  

**Error budget:** 0.5% → ~3.6 hours/month bad probes allowed  

**Policy:**

- Budget > 50%: ship features normally  
- Budget 10–50%: slow releases; fix reliability first  
- Budget < 10%: freeze features; incident review  

---

## Latency SLO example

**SLI:** p95 latency of `GET /api/orders`  
**SLO:** p95 ≤ 500ms over 7 days  
**Tool:** Prometheus histogram or APM  

---

## Multi-window alerting (Google SRE book pattern)

Alert on **fast burn** (budget gone in hours) and **slow burn** (projected miss this month).

Example PromQL concept (Part 44):

```promql
# Simplified availability burn
1 - (sum(rate(http_requests_total{status=~"5.."}[1h])) / sum(rate(http_requests_total[1h])))
```

---

## SLO ≠ monitoring everything

Pick **2–4 user-journey SLOs** per service. Instrument those paths first.

---

## Link to product requirements

Map SLO to REQ-NFR in [project management guide](https://github.com/belittlewho/solo-software-project-management).

Next: [Part 30 — Incidents & chaos](30-incidents-postmortems-oncall-chaos.md)
