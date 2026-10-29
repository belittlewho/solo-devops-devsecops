# Part 44 — Observability Stack Lab (Prometheus, Grafana, Loki, OTel, Alertmanager)

Full install walkthrough: [Part 51](51-workshop-observability-install.md)

---

## docker-compose monitoring stack (sketch)

```yaml
services:
  prometheus:
    image: prom/prometheus:v2.54.0
    volumes:
      - ./prometheus.yml:/etc/prometheus/prometheus.yml
      - prom_data:/prometheus
    ports: ['127.0.0.1:9090:9090']
  grafana:
    image: grafana/grafana:11.1.0
    ports: ['127.0.0.1:3001:3000']
    environment:
      GF_SECURITY_ADMIN_PASSWORD: ${GRAFANA_ADMIN_PASSWORD}
  node_exporter:
    image: prom/node-exporter:v1.8.2
    network_mode: host
    pid: host
  loki:
    image: grafana/loki:3.0.0
    command: -config.file=/etc/loki/local-config.yaml
  promtail:
    image: grafana/promtail:3.0.0
    volumes:
      - /var/log:/var/log:ro
      - /var/lib/docker/containers:/var/lib/docker/containers:ro
```

Expose Grafana via nginx + auth; do not publish 9090 publicly.

---

## prometheus.yml scrape

```yaml
scrape_configs:
  - job_name: node
    static_configs:
      - targets: ['localhost:9100']
  - job_name: app
    metrics_path: /metrics
    static_configs:
      - targets: ['host.docker.internal:3000']
```

---

## Alertmanager

`alertmanager.yml` routes by severity; receiver PagerDuty/Slack/email.

Prometheus `rules.yml`:

```yaml
groups:
  - name: slo
    rules:
      - alert: HighErrorRate
        expr: rate(http_requests_total{status=~"5.."}[5m]) / rate(http_requests_total[5m]) > 0.05
        for: 10m
        labels: { severity: page }
        annotations:
          summary: "5xx rate above 5%"
```

---

## OpenTelemetry

Instrument app:

```javascript
// Node: @opentelemetry/sdk-node + auto-instrumentations
```

Export OTLP to Grafana Tempo or Jaeger — trace request across services.

---

## Dashboards as code

Grafonnet or Grafana provisioning:

```yaml
# provisioning/dashboards/default.yaml
apiVersion: 1
providers:
  - name: default
    folder: Ops
    options:
      path: /etc/grafana/dashboards
```

JSON dashboards in git; CI validates.

---

## Synthetic monitoring

Better Stack, Checkly, or Prometheus blackbox exporter probing `/health` from external regions.

---

## APM (managed)

Datadog, Honeycomb, New Relic — paid; faster setup than self-host. Export same RED metrics (Rate, Errors, Duration).

Next: [Part 45 — DevSecOps advanced](45-devsecops-advanced.md)
