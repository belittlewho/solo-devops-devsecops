# Part 31 — Load Testing & Capacity Planning

---

## Why load test

Find limits **before** users do: CPU, DB connections, memory, rate limits.

---

## k6 (recommended)

```javascript
// script.js
import http from 'k6/http';
import { check, sleep } from 'k6';

export const options = {
  stages: [
    { duration: '2m', target: 50 },
    { duration: '5m', target: 50 },
    { duration: '2m', target: 0 },
  ],
  thresholds: {
    http_req_duration: ['p(95)<500'],
    http_req_failed: ['rate<0.01'],
  },
};

export default function () {
  const res = http.get('https://staging.example.com/health');
  check(res, { 'status 200': (r) => r.status === 200 });
  sleep(1);
}
```

```bash
k6 run script.js
```

Run against **staging** only; notify if shared infra.

---

## Locust (Python)

Good for complex user flows; UI for ramp-up.

---

## What to watch during test

| Resource | Command |
|----------|---------|
| CPU/RAM | `htop`, node_exporter |
| Disk I/O | `iostat -xz 1` |
| Network | `ss -s` |
| DB | `pg_stat_activity`, connections |

---

## Capacity model (back-of-envelope)

```
requests/sec * latency_sec ≈ concurrent requests
```

Each app worker handles N concurrent → workers needed = concurrent / N.

Add 30% headroom; plan scale trigger at 70% sustained CPU.

---

## Tie to SLO

Load test must validate **latency SLO** at expected peak (Part 29).

Next: [Part 32 — Linux deep dive](32-linux-operations-deep-dive.md)
