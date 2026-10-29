# Part 18 — Observability (Logs, Metrics, Alerts)

Three pillars: **logs**, **metrics**, **traces**.

---

## Logs

| Level | Linux default | Centralized |
|-------|---------------|-------------|
| App | stdout → docker logs | Loki, CloudWatch |
| System | journald | journald + ship |
| Web | nginx access.log | same |

**Structured JSON logs** from app — searchable fields (`request_id`, `user_id` hash).

```bash
docker compose logs -f --tail=100 web
journalctl -u nginx -f
```

---

## Metrics

- **Prometheus** scrapes `/metrics`  
- **Grafana** dashboards  
- Host: node_exporter (CPU, RAM, disk)  

Alert when disk > 85%, 5xx rate up, cert expiring.

---

## Traces (optional)

OpenTelemetry → Jaeger/Tempo — debug latency across services.

---

## SLO example

**Availability:** 99.5% monthly — error budget = downtime allowed.  
**Latency:** p95 < 500ms.

Page yourself only on SLO burn — avoid alert fatigue.

**Hands-on:** [Part 44](44-observability-stack-lab.md), [Part 51 workshop](51-workshop-observability-install.md), [examples/monitoring/](../examples/monitoring/).

---

## Contrast PaaS

Vercel/Render provide built-in metrics — still add external uptime check (UptimeRobot, Better Stack).

Next: [Part 19 — Backup & DR](19-backup-disaster-recovery.md)
