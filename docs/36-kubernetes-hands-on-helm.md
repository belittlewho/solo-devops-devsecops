# Part 36 — Kubernetes Hands-On (kubectl, Helm, Kustomize, Ingress)

Assumes **k3s** homelab or managed cluster (Part 52).

---

## kubectl essentials

```bash
kubectl get nodes,pods,svc,ingress -A
kubectl describe pod POD -n app
kubectl logs -f deploy/web -n app
kubectl apply -f manifest.yaml
kubectl rollout status deploy/web -n app
kubectl rollout undo deploy/web -n app
```

Contexts: `kubectl config use-context`.

---

## Minimal Deployment + Service

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: web
  namespace: app
spec:
  replicas: 2
  selector:
    matchLabels: { app: web }
  template:
    metadata:
      labels: { app: web }
    spec:
      securityContext:
        runAsNonRoot: true
      containers:
        - name: web
          image: ghcr.io/org/app:1.0.0
          ports: [{ containerPort: 3000 }]
          resources:
            requests: { memory: "128Mi", cpu: "100m" }
            limits: { memory: "512Mi", cpu: "500m" }
          livenessProbe:
            httpGet: { path: /health, port: 3000 }
          readinessProbe:
            httpGet: { path: /health, port: 3000 }
---
apiVersion: v1
kind: Service
metadata:
  name: web
  namespace: app
spec:
  selector: { app: web }
  ports:
    - port: 80
      targetPort: 3000
```

---

## Ingress (nginx ingress controller)

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: web
  annotations:
    cert-manager.io/cluster-issuer: letsencrypt
spec:
  tls:
    - hosts: [app.example.com]
      secretName: app-tls
  rules:
    - host: app.example.com
      http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: web
                port: { number: 80 }
```

Traefik: built into k3s as default ingress.

---

## Helm

```bash
helm repo add bitnami https://charts.bitnami.com/bitnami
helm install redis bitnami/redis -f values-prod.yaml
helm upgrade --install myapp ./charts/myapp -n app --create-namespace
```

Chart structure: `Chart.yaml`, `values.yaml`, `templates/`.

---

## Kustomize

```bash
kubectl apply -k overlays/staging
```

Base + overlay patches for staging/prod without copy-paste YAML.

---

## EKS/GKE/AKS setup (outline)

1. IaC: VPC + cluster module (Part 40/50)  
2. `aws eks update-kubeconfig`  
3. Install ingress + cert-manager  
4. CI deploys with OIDC role  

Managed control plane; you own nodes (or Fargate profiles).

Next: [Part 37 — Service mesh](37-service-mesh-ecs-notes.md)
