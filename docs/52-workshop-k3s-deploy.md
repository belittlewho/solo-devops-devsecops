# Part 52 — Workshop: k3s Deploy Application

**Goal:** Single-node k3s (homelab or VPS 4GB+); deploy app with Helm; Ingress TLS.

---

## Step 1 — Install k3s

```bash
curl -sfL https://get.k3s.io | sh -
sudo kubectl get nodes
```

kubeconfig: `/etc/rancher/k3s/k3s.yaml`

---

## Step 2 — Namespaces & basics

```bash
kubectl create namespace app
kubectl config set-context --current --namespace=app
```

---

## Step 3 — Deploy app

Use manifests from [Part 36](36-kubernetes-hands-on-helm.md) or Helm chart `./charts/myapp`.

```bash
helm upgrade --install myapp ./charts/myapp -n app -f values-staging.yaml
kubectl rollout status deploy/web
```

---

## Step 4 — Ingress + cert-manager

```bash
kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.15.0/cert-manager.yaml
# ClusterIssuer letsencrypt-prod
kubectl apply -f clusterissuer.yaml
kubectl apply -f ingress.yaml
```

k3s includes Traefik; or install nginx ingress controller.

---

## Step 5 — CI deploy

GitHub Actions with `KUBECONFIG` secret (staging only) or GitOps Argo CD:

```bash
argocd app create myapp --repo https://github.com/org/repo --path charts/myapp --dest-server https://kubernetes.default.svc --dest-namespace app
```

---

## Step 6 — Observability add-on

```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm install kube-prom prometheus-community/kube-prometheus-stack -n monitoring --create-namespace
```

---

## Step 7 — Cleanup lab

```bash
/usr/local/bin/k3s-uninstall.sh   # destroys cluster — staging only
```

**Checkpoint:** HTTPS URL serves app; `kubectl top pods` shows metrics after metrics-server enabled.

Return to [README](../README.md).
