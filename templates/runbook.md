# Runbook — {{SERVICE_NAME}}

**Owner:** {{YOU}}  
**Last updated:** {{DATE}}  
**On-call:** {{CONTACT}}

---

## Service overview

| Item | Value |
|------|--------|
| Production URL | |
| Staging URL | |
| Repo | |
| Host / cluster | |
| Criticality | P0 / P1 |

---

## Architecture (one paragraph)

---

## Health checks

```bash
curl -fsS https://app.example.com/health
```

Expected: `200` body `{"status":"ok"}`

---

## Common operations

### Restart app

```bash
ssh deploy@HOST 'cd /opt/myapp && docker compose restart web'
```

### View logs

```bash
ssh deploy@HOST 'cd /opt/myapp && docker compose logs -f --tail=200 web'
```

### Rollback deploy

```bash
# Previous image tag
ssh deploy@HOST 'cd /opt/myapp && export IMAGE=ghcr.io/org/app:PREVIOUS && docker compose up -d'
```

---

## Incidents

| Symptom | Likely cause | Steps |
|---------|--------------|-------|
| 502 Bad Gateway | App down | Check compose, restart |
| Disk full | Logs | `df -h`, vacuum journal, rotate |
| SSL error | Cert expiry | `certbot renew` |

---

## Dependencies

| Dependency | Contact / dashboard |
|------------|---------------------|
| DNS | |
| Payment | |
| Email | |

---

## Post-incident

- [ ] Timeline written  
- [ ] Runbook updated  
- [ ] Follow-up issue filed  
