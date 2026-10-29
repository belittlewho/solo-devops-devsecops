# Complete study path — DevOps & DevSecOps

Practice on **real Linux**: VPS, homelab VM, or WSL2 for CLI (deploy to VPS for real infra).  
**Gap index (all parts mapped):** [GAPS.md](GAPS.md)

---

## Phase A — Mental models (Days 1–3)

| Order | Part | Outcome |
|-------|------|---------|
| A0 | [00 Glossary](docs/00-glossary-and-map.md) | Terms & platform map |
| A1 | [01 Mindset](docs/01-devops-mindset-lifecycle.md) | SDLC, CALMS, DORA |
| A2 | [02 Linux vs other](docs/02-linux-vs-other-infrastructure.md) | Platform choice |
| A3 | [12 IaaS/PaaS/SaaS](docs/12-iaas-paas-saas-models.md) | Shared responsibility |

---

## Phase B — Linux operator (Days 4–12)

| Order | Part | Outcome |
|-------|------|---------|
| B1 | [03 Linux essentials](docs/03-linux-essentials.md) | CLI baseline |
| B2 | [32 Linux deep dive](docs/32-linux-operations-deep-dive.md) | LVM, debug, SELinux |
| B3 | [04 Networking](docs/04-networking-dns-tls.md) | DNS, TLS, ufw |
| B4 | [33 Edge & CDN](docs/33-edge-networking-cdn-vpn.md) | Cloudflare, WireGuard |
| B5 | [05 systemd](docs/05-systemd-services.md) | Services |
| B6 | [20 Secrets & SSH](docs/20-secrets-identity-iam.md) | Keys, IAM |
| B7 | [11 Workshop VPS](docs/11-workshop-first-linux-server.md) | First server |

---

## Phase C — Delivery (Days 13–20)

| Order | Part | Outcome |
|-------|------|---------|
| C1 | [06–07 Git & CI/CD](docs/06-git-and-ci-fundamentals.md) | Pipelines |
| C2 | [34 CI/CD advanced](docs/34-cicd-advanced-platforms.md) | Monorepo, GHCR |
| C3 | [08–35 Containers](docs/08-containers-docker-compose.md) | Docker prod patterns |
| C4 | [10 Reverse proxy](docs/10-reverse-proxy-web.md) | nginx TLS |
| C5 | [17 Environments](docs/17-environments-promotion.md) | staging/prod |
| C6 | [26 GitOps & deploy](docs/26-gitops-deployment-strategies.md) | Strategies |

---

## Phase D — IaC & cloud (Days 21–28)

| Order | Part | Outcome |
|-------|------|---------|
| D1 | [13–38 Terraform](docs/13-terraform-iac.md) | State, policy |
| D2 | [39 Packer & alt IaC](docs/39-iac-alternatives-packer.md) | Pulumi/CDK |
| D3 | [14–50 Ansible workshop](docs/50-workshop-terraform-ansible.md) | TF + Ansible |
| D4 | [40–41 Cloud VPC & services](docs/40-cloud-vpc-iam-storage.md) | AWS patterns |
| D5 | [15 Cloud map](docs/15-cloud-providers-map.md) | Multi-cloud names |
| D6 | [16 Homelab](docs/16-bare-metal-vms-homelab.md) | VMs |

---

## Phase E — Data & K8s (Days 29–38)

| Order | Part | Outcome |
|-------|------|---------|
| E1 | [42–43 Data & queues](docs/42-postgresql-operations.md) | Postgres, Redis |
| E2 | [09–36 K8s](docs/36-kubernetes-hands-on-helm.md) | Helm, Ingress |
| E3 | [52 k3s workshop](docs/52-workshop-k3s-deploy.md) | Cluster lab |
| E4 | [37 Service mesh / ECS](docs/37-service-mesh-ecs-notes.md) | Optional |

---

## Phase F — SRE & observability (Days 39–45)

| Order | Part | Outcome |
|-------|------|---------|
| F1 | [29 SLO](docs/29-sre-slo-error-budgets.md) + [SLO template](templates/slo-document.md) | Error budgets |
| F2 | [30 Incidents & chaos](docs/30-incidents-postmortems-oncall-chaos.md) | SEV, postmortem |
| F3 | [31 Load testing](docs/31-load-testing-capacity.md) | k6 |
| F4 | [18 + 44 + 51 Observability](docs/51-workshop-observability-install.md) | Prometheus stack |
| F5 | [19 Backup & DR](docs/19-backup-disaster-recovery.md) + game day template | Restore drill |

---

## Phase G — Security & scale (Days 46–55)

| Order | Part | Outcome |
|-------|------|---------|
| G1 | [21–23 DevSecOps base](docs/21-devsecops-shift-left.md) | Shift left |
| G2 | [45–46 Advanced sec & compliance](docs/45-devsecops-advanced.md) | DAST, SOC2 |
| G3 | [22 Hardening](docs/22-linux-hardening.md) | CIS style |
| G4 | [48 HA & autoscaling](docs/48-high-availability-autoscaling.md) | HPA, multi-AZ |
| G5 | [47 Platform / IDP](docs/47-platform-engineering-idp.md) | Golden paths |
| G6 | [49 Platforms](docs/49-platforms-arm-serverless-mobile.md) | ARM, serverless |
| G7 | [27 Windows](docs/27-windows-infra-contrast.md) | Contrast |
| G8 | [28 FinOps](docs/28-finops-solo-constraints.md) | Cost |
| G9 | [99 FAQ](docs/99-faq-cheatsheet.md) | Cheat sheet |

---

## Concept coverage matrix

See [GAPS.md](GAPS.md) for topic → part mapping (complete).
