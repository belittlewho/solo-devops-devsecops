# SLO document — {{SERVICE_NAME}}

**Version:** 1.0  
**Review cadence:** Quarterly  
**Owner:**

---

## Service description



---

## User journeys in scope

1. 
2. 

---

## SLIs & SLOs

| ID | SLI definition | SLO target | Window | Measurement |
|----|----------------|------------|--------|-------------|
| SLI-1 | Availability: successful synthetic checks / total | 99.5% | 30d rolling | Better Stack / blackbox |
| SLI-2 | Latency: p95 GET /api/... | ≤ 500ms | 7d | Prometheus |

---

## Error budget policy

| Budget remaining | Action |
|------------------|--------|
| > 50% | Normal development |
| 10–50% | Prioritize reliability work |
| < 10% | Feature freeze until stable |

---

## Alerting

| Alert | Burn rate | Route |
|-------|-----------|-------|
| Fast burn | | Pager / phone |
| Slow burn | | Slack |

---

## Dependencies

| Dependency | Their SLO/SLA |
|------------|---------------|
| | |

---

## History

| Date | Change |
|------|--------|
| | Initial SLO |
