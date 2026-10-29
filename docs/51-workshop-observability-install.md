# Part 51 — Workshop: Install Observability Stack on VPS

**Goal:** Prometheus + node_exporter + Grafana + Loki/Promtail + one alert → email/Slack.

---

## Step 1 — Directory on VPS

```bash
sudo mkdir -p /opt/obs && sudo chown deploy:deploy /opt/obs
cd /opt/obs
```

Copy compose from [Part 44](44-observability-stack-lab.md); add `.env` for Grafana password.

---

## Step 2 — Bind to localhost

All services `127.0.0.1` ports; nginx vhost `grafana.internal.example.com` with basic auth or SSO.

---

## Step 3 — Scrape app metrics

Instrument `/metrics` (Prometheus client). Reload prometheus.

---

## Step 4 — Import dashboards

Grafana dashboard ID **1860** (node exporter full); save JSON to git (dashboards as code).

---

## Step 5 — Alertmanager

Configure Slack webhook; test with `amtool alert add`.

Fire test alert by stopping nginx briefly in staging.

---

## Step 6 — Loki query

Grafana Explore → LogQL: `{job="varlogs"} |= "error"`

---

## Step 7 — Document

Link Grafana panels in runbook; define SLO dashboard (Part 29).

**Checkpoint:** intentional fail deploy triggers alert within 15 minutes.

Next: [Part 52 — k3s workshop](52-workshop-k3s-deploy.md)
