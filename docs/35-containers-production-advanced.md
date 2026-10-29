# Part 35 — Containers: Production Patterns, Rootless, Podman, ECS

---

## Production Compose patterns

```yaml
services:
  web:
    image: ghcr.io/org/app:${APP_VERSION:?set}
    restart: unless-stopped
    read_only: true
    tmpfs: [/tmp]
    security_opt: [no-new-privileges:true]
    cap_drop: [ALL]
    deploy:
      resources:
        limits:
          cpus: '1.0'
          memory: 512M
    healthcheck:
      test: ['CMD', 'curl', '-f', 'http://127.0.0.1:3000/health']
      interval: 30s
      timeout: 5s
      retries: 3
    logging:
      driver: json-file
      options:
        max-size: '10m'
        max-file: '3'
```

Bind app to `127.0.0.1`; secrets via env file mode 600, not in image.

---

## Rootless Docker / Podman

```bash
# Podman (daemonless)
podman run -d -p 8080:80 docker.io/nginx
podman compose up -d
```

Rootless reduces container escape → root on host. Tradeoff: low port binding needs `sysctl` or reverse proxy.

---

## cosign sign & verify

```bash
cosign generate-key-pair
cosign sign --key cosign.key ghcr.io/org/app:1.2.3
cosign verify --key cosign.pub ghcr.io/org/app:1.2.3
```

CI signs on release; prod pull verifies.

---

## Registry mirror / air-gap

Harbor or pull-through cache; `registry-mirrors` in `/etc/docker/daemon.json` for restricted networks.

---

## AWS ECS Fargate (middle ground)

No EC2 SSH; task definition = CPU/mem + container image; ALB → service. Less ops than EKS; more than raw VPS.

| | VPS+Compose | ECS Fargate | EKS |
|--|-------------|-------------|-----|
| Ops load | you patch OS | AWS patches Fargate | high |
| Cost low traffic | $ | $$ | $$$ |

Next: [Part 36 — K8s hands-on](36-kubernetes-hands-on-helm.md)
