# Solo DevOps & DevSecOps — From Scratch to Production Infrastructure

Learn **DevOps** (how software is built, shipped, and operated) and **DevSecOps** (security woven into that flow) with a **Linux-first** lens — and clear contrasts to Windows, cloud PaaS, serverless, and managed services.

Follow **[STUDY-PATH.md](STUDY-PATH.md)** for reading order (Phases A–G). **Topic index:** **[GAPS.md](GAPS.md)** maps every subject to Parts 29–52+.

**Repo:** practice commands on a Linux VM or WSL2; see [Part 2 — Linux vs other platforms](docs/02-linux-vs-other-infrastructure.md).

---

## Start here

| If you… | Open |
|---------|------|
| Need every term defined first | [Part 0 — Glossary & map](docs/00-glossary-and-map.md) |
| Want full curriculum order | [STUDY-PATH.md](STUDY-PATH.md) |
| Are on WSL2 (like many dev machines) | [Part 2 — Linux vs other infrastructure](docs/02-linux-vs-other-infrastructure.md) |
| Want a homelab / first server | [Part 11 — First Linux server workshop](docs/11-workshop-first-linux-server.md) |
| Need one-page rescue | [Part 99 — FAQ & cheat sheet](docs/99-faq-cheatsheet.md) |

---

## Table of contents

### Foundations

| Part | Topic | File |
|------|--------|------|
| 0 | Glossary & platform map | [docs/00-glossary-and-map.md](docs/00-glossary-and-map.md) |
| 1 | DevOps mindset & lifecycle | [docs/01-devops-mindset-lifecycle.md](docs/01-devops-mindset-lifecycle.md) |
| 2 | Linux vs Windows vs cloud vs containers | [docs/02-linux-vs-other-infrastructure.md](docs/02-linux-vs-other-infrastructure.md) |
| 3 | Linux essentials for operators | [docs/03-linux-essentials.md](docs/03-linux-essentials.md) |
| 4 | Networking for infrastructure | [docs/04-networking-dns-tls.md](docs/04-networking-dns-tls.md) |
| 5 | Processes, systemd & services | [docs/05-systemd-services.md](docs/05-systemd-services.md) |

### Build, ship, run

| Part | Topic | File |
|------|--------|------|
| 6 | Git, branches & CI fundamentals | [docs/06-git-and-ci-fundamentals.md](docs/06-git-and-ci-fundamentals.md) |
| 7 | CI/CD pipelines | [docs/07-cicd-pipelines.md](docs/07-cicd-pipelines.md) |
| 8 | Containers (Docker) & Compose | [docs/08-containers-docker-compose.md](docs/08-containers-docker-compose.md) |
| 9 | Kubernetes concepts (when & why) | [docs/09-kubernetes-concepts.md](docs/09-kubernetes-concepts.md) |
| 10 | Reverse proxy & web serving (nginx/Caddy) | [docs/10-reverse-proxy-web.md](docs/10-reverse-proxy-web.md) |

### Infrastructure as code & clouds

| Part | Topic | File |
|------|--------|------|
| 12 | Infrastructure models (IaaS/PaaS/SaaS) | [docs/12-iaas-paas-saas-models.md](docs/12-iaas-paas-saas-models.md) |
| 13 | Terraform & IaC basics | [docs/13-terraform-iac.md](docs/13-terraform-iac.md) |
| 14 | Ansible & configuration management | [docs/14-ansible-config-management.md](docs/14-ansible-config-management.md) |
| 15 | Cloud providers (AWS/GCP/Azure) — solo map | [docs/15-cloud-providers-map.md](docs/15-cloud-providers-map.md) |
| 16 | Bare metal, VMs, and Proxmox homelab | [docs/16-bare-metal-vms-homelab.md](docs/16-bare-metal-vms-homelab.md) |

### Operations

| Part | Topic | File |
|------|--------|------|
| 17 | Environments & promotion | [docs/17-environments-promotion.md](docs/17-environments-promotion.md) |
| 18 | Observability (logs, metrics, alerts) | [docs/18-observability.md](docs/18-observability.md) |
| 19 | Backups, DR & runbooks | [docs/19-backup-disaster-recovery.md](docs/19-backup-disaster-recovery.md) |
| 20 | Secrets & identity (SSH, vaults, IAM) | [docs/20-secrets-identity-iam.md](docs/20-secrets-identity-iam.md) |

### DevSecOps

| Part | Topic | File |
|------|--------|------|
| 21 | DevSecOps & shift left | [docs/21-devsecops-shift-left.md](docs/21-devsecops-shift-left.md) |
| 22 | Linux hardening & CIS baseline | [docs/22-linux-hardening.md](docs/22-linux-hardening.md) |
| 23 | App & supply chain security (SAST, deps, SBOM) | [docs/23-app-supply-chain-security.md](docs/23-app-supply-chain-security.md) |
| 24 | Runtime security & zero trust lite | [docs/24-runtime-zero-trust.md](docs/24-runtime-zero-trust.md) |
| 25 | Compliance hooks (SOC2-ish, logging) | [docs/25-compliance-logging-audit.md](docs/25-compliance-logging-audit.md) |

### Practice & reference

| Part | Topic | File |
|------|--------|------|
| 11 | Workshop: first Linux server | [docs/11-workshop-first-linux-server.md](docs/11-workshop-first-linux-server.md) |
| 26 | GitOps & deployment strategies | [docs/26-gitops-deployment-strategies.md](docs/26-gitops-deployment-strategies.md) |
| 27 | Windows / .NET ops contrast | [docs/27-windows-infra-contrast.md](docs/27-windows-infra-contrast.md) |
| 28 | Cost, FinOps & solo constraints | [docs/28-finops-solo-constraints.md](docs/28-finops-solo-constraints.md) |
| 99 | FAQ & cheat sheet | [docs/99-faq-cheatsheet.md](docs/99-faq-cheatsheet.md) |

### Extended (SRE, depth, cloud, workshops)

| Part | Topic | File |
|------|--------|------|
| 29 | SLI, SLO & error budgets | [docs/29-sre-slo-error-budgets.md](docs/29-sre-slo-error-budgets.md) |
| 30 | Incidents, postmortems, on-call, chaos | [docs/30-incidents-postmortems-oncall-chaos.md](docs/30-incidents-postmortems-oncall-chaos.md) |
| 31 | Load testing & capacity | [docs/31-load-testing-capacity.md](docs/31-load-testing-capacity.md) |
| 32 | Linux operations deep dive | [docs/32-linux-operations-deep-dive.md](docs/32-linux-operations-deep-dive.md) |
| 33 | CDN, email DNS, VPN, WAF, HAProxy | [docs/33-edge-networking-cdn-vpn.md](docs/33-edge-networking-cdn-vpn.md) |
| 34 | CI/CD advanced (GitLab, monorepo, GHCR) | [docs/34-cicd-advanced-platforms.md](docs/34-cicd-advanced-platforms.md) |
| 35 | Containers production & ECS | [docs/35-containers-production-advanced.md](docs/35-containers-production-advanced.md) |
| 36 | Kubernetes hands-on (Helm, Ingress) | [docs/36-kubernetes-hands-on-helm.md](docs/36-kubernetes-hands-on-helm.md) |
| 37 | Service mesh & ECS notes | [docs/37-service-mesh-ecs-notes.md](docs/37-service-mesh-ecs-notes.md) |
| 38 | Terraform advanced & policy | [docs/38-terraform-advanced-policy.md](docs/38-terraform-advanced-policy.md) |
| 39 | Pulumi, CDK, Packer, cloud-init | [docs/39-iac-alternatives-packer.md](docs/39-iac-alternatives-packer.md) |
| 40 | VPC, IAM, S3, landing zone | [docs/40-cloud-vpc-iam-storage.md](docs/40-cloud-vpc-iam-storage.md) |
| 41 | RDS, Redis, SQS, Lambda, CloudFront | [docs/41-cloud-managed-services-serverless.md](docs/41-cloud-managed-services-serverless.md) |
| 42 | PostgreSQL operations & PITR | [docs/42-postgresql-operations.md](docs/42-postgresql-operations.md) |
| 43 | Redis, queues, Kafka, OpenSearch | [docs/43-redis-queues-search.md](docs/43-redis-queues-search.md) |
| 44 | Observability stack (Prometheus, Loki, OTel) | [docs/44-observability-stack-lab.md](docs/44-observability-stack-lab.md) |
| 45 | DevSecOps advanced (DAST, Falco, PKI) | [docs/45-devsecops-advanced.md](docs/45-devsecops-advanced.md) |
| 46 | SOC2, PCI, HIPAA (ops mapping) | [docs/46-compliance-frameworks.md](docs/46-compliance-frameworks.md) |
| 47 | Platform engineering & IDP | [docs/47-platform-engineering-idp.md](docs/47-platform-engineering-idp.md) |
| 48 | HA, multi-region, autoscaling | [docs/48-high-availability-autoscaling.md](docs/48-high-availability-autoscaling.md) |
| 49 | ARM64, macOS, BSD, serverless lab | [docs/49-platforms-arm-serverless-mobile.md](docs/49-platforms-arm-serverless-mobile.md) |
| 50 | **Workshop:** Terraform + Ansible | [docs/50-workshop-terraform-ansible.md](docs/50-workshop-terraform-ansible.md) |
| 51 | **Workshop:** Observability install | [docs/51-workshop-observability-install.md](docs/51-workshop-observability-install.md) |
| 52 | **Workshop:** k3s deploy | [docs/52-workshop-k3s-deploy.md](docs/52-workshop-k3s-deploy.md) |

---

## Templates

| Template | Purpose |
|----------|---------|
| [runbook.md](templates/runbook.md) | Operate & incident response |
| [server-baseline.md](templates/server-baseline.md) | New Linux server checklist |
| [cicd-pipeline-spec.md](templates/cicd-pipeline-spec.md) | Pipeline design doc |
| [threat-model-lite.md](templates/threat-model-lite.md) | DevSecOps sketch |
| [infra-decision-record.md](templates/infra-decision-record.md) | ADR for infra choices |
| [slo-document.md](templates/slo-document.md) | SLI/SLO & error budget policy |
| [postmortem.md](templates/postmortem.md) | Blameless incident review |
| [on-call-policy.md](templates/on-call-policy.md) | Rotation & escalation |
| [game-day-checklist.md](templates/game-day-checklist.md) | DR / game day drill |

## Examples

| Path | Purpose |
|------|---------|
| [examples/monitoring/](examples/monitoring/) | Prometheus/Grafana/Loki Compose starter |

---

## Related guide

- [Solo software project management & requirements](https://github.com/belittlewho/solo-software-project-management) — breakdown, RTM, release NFRs

---

## License

MIT
