# Part 48 — High Availability, Multi-Region & Autoscaling

---

## Active-passive vs active-active

| Pattern | Description |
|---------|-------------|
| **Active-passive** | Standby DB/VPS; DNS failover |
| **Active-active** | Multi-region writes (hard); read replicas easier |

Solo MVP: single region + good backups; add passive when SLO demands.

---

## Multi-AZ (cloud)

RDS Multi-AZ, ALB across AZs, ECS tasks spread `distinctInstance`.

---

## Multi-region

Route53 latency routing or GeoDNS; replicate data async (conflict resolution hard). Static assets on global CDN first step.

---

## Global load balancing

Anycast CDN (Cloudflare) or cloud GLB fronting regional origins.

---

## Session affinity (sticky sessions)

ALB sticky cookie; prefer **stateless JWT** + Redis session store for horizontal scale.

---

## Horizontal Pod Autoscaler (K8s)

```yaml
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: web
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: web
  minReplicas: 2
  maxReplicas: 10
  metrics:
    - type: Resource
      resource:
        name: cpu
        target:
          type: Utilization
          averageUtilization: 70
```

**Cluster autoscaler:** adds nodes when pods pending.

---

## VPS scale-up path

Vertical: bigger instance. Horizontal: load balancer + N identical Compose hosts + shared DB.

Next: [Part 49 — ARM, macOS, BSD, serverless lab](49-platforms-arm-serverless-mobile.md)
