# On-call policy — {{TEAM_OR_SOLO}}

**Effective:** {{DATE}}

---

## Scope

Services covered:

- 
- 

Out of scope (business hours only):

- 

---

## Rotation

| Week | Primary | Secondary |
|------|---------|-----------|
| | | |

Solo: Primary = you; Secondary = {{backup person or "none — document risk"}}

---

## Severity & response times

| SEV | Response | Update cadence |
|-----|----------|----------------|
| SEV1 | 15 min | 30 min |
| SEV2 | 1 h | 2 h |
| SEV3 | Next business day | Daily |
| SEV4 | Best effort | — |

---

## Escalation

1. Primary on-call  
2. Secondary  
3. Vendor support (AWS/Hetzner) ticket  
4. {{Domain/DNS provider}}

---

## Channels

| Purpose | Channel |
|---------|---------|
| Alerts | PagerDuty / Grafana / phone |
| Coordination | Slack #incidents |
| User comms | Status page / email template |

---

## Runbook index

| Service | Runbook link |
|---------|--------------|
| | templates/runbook.md |

---

## Compensation / time off (team)

{{Policy when team grows}}

---

## Post-incident

SEV1/2 require postmortem within 5 business days — [postmortem.md](postmortem.md)
