# Part 30 — Incidents, Postmortems, On-Call & Chaos

Templates: [postmortem](../templates/postmortem.md), [on-call-policy](../templates/on-call-policy.md), [game-day-checklist](../templates/game-day-checklist.md)

---

## Severity (SEV) levels

| Level | User impact | Response |
|-------|-------------|----------|
| **SEV1** | Total outage or data loss active | Drop everything; comms every 30 min |
| **SEV2** | Major degradation; no workaround | Fix same day |
| **SEV3** | Partial; workaround exists | Next business day |
| **SEV4** | Minor; cosmetic | Backlog |

Solo: you are SEV1–4 responder — document **who to notify** (customers, partner) in on-call policy.

---

## Incident timeline (roles = you, but wear hats)

1. **Detect** — alert or user report  
2. **Triage** — assign SEV, open channel/doc  
3. **Mitigate** — rollback, scale, disable feature flag  
4. **Resolve** — root fix or temp fix + follow-up ticket  
5. **Communicate** — status page or email for SEV1/2  
6. **Postmortem** — within 5 business days for SEV1/2  

---

## Blameless postmortem

Focus: **systems and process**, not “who clicked wrong.”

Required sections: Summary, Impact, Timeline, Root cause(s), What went well, What went wrong, Action items (owner + due).

---

## On-call (solo + future team)

- Primary: you  
- Secondary: trusted contractor or “wake spouse only SEV1”  
- Escalation: provider support ticket for cloud/network  
- **Runbook links** in every alert  

Rotation template matters when second engineer joins.

---

## Game days & DR drills

Quarterly scripted exercises:

| Drill | Success criteria |
|-------|------------------|
| Restore DB from backup | RTO met; app serves data |
| Failover DNS to backup VPS | Traffic moves in TTL |
| Kill container | Orchestrator or systemd restarts |

Use [game-day-checklist](../templates/game-day-checklist.md).

---

## Chaos engineering (intro)

**Principle:** inject failure in controlled env to find weaknesses.

| Tool | Use |
|------|-----|
| `chaos-mesh` | K8s |
| `toxiproxy` | Latency/partition |
| Manual | `docker kill`, `iptables DROP` on staging |

Never chaos in prod until staging drills pass. Start: reboot VPS in staging during load test.

---

## Toil measurement

Log hours/week on: manual deploy, SSH fixes, repeated tickets. Target: automate top toil item monthly (Part 01).

Next: [Part 31 — Load testing](31-load-testing-capacity.md)
