# Part 8 — Containers (Docker) & Compose

Containers package **app + runtime deps**; Linux host shares one kernel.

---

## Core concepts

| Concept | Meaning |
|---------|---------|
| **Image** | Read-only layers (Dockerfile) |
| **Container** | Running instance |
| **Volume** | Persistent data |
| **Network** | Bridge between containers |
| **Registry** | Store images (GHCR, ECR) |

---

## Dockerfile basics

```dockerfile
FROM node:22-bookworm-slim
WORKDIR /app
COPY package*.json ./
RUN npm ci --omit=dev
COPY . .
RUN npm run build
USER node
EXPOSE 3000
CMD ["node", "dist/server.js"]
```

**DevSecOps:** non-root `USER`, slim base, pin digests `@sha256:...`, scan with Trivy.

---

## Compose (multi-service on one Linux host)

```yaml
services:
  web:
    build: .
    ports:
      - "127.0.0.1:3000:3000"
    env_file: .env
    depends_on:
      - db
  db:
    image: postgres:16-alpine
    volumes:
      - pgdata:/var/lib/postgresql/data
    environment:
      POSTGRES_PASSWORD: ${DB_PASSWORD}
volumes:
  pgdata:
```

```bash
docker compose up -d
docker compose logs -f web
```

**Prod pattern:** bind app to **127.0.0.1**; nginx on host for TLS (Part 10).

---

## Linux vs Windows containers

| | Linux container | Windows container |
|--|-----------------|-------------------|
| Host | Linux | Windows Server |
| Typical stack | Node, Go, Python | .NET Framework |
| Solo default | ✅ | Rare |

Docker Desktop on Windows runs Linux VMs under the hood for Linux images.

---

## When not to Docker

- Simple static site → nginx files only  
- Fully managed PaaS → provider builds image  

Next: [Part 9 — Kubernetes](09-kubernetes-concepts.md)
