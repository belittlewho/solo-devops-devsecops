# Complete study path — DevOps & DevSecOps (no knowledge gaps)

Practice on **real Linux**: cheap VPS (Hetzner, DigitalOcean, Linode), local VM (Multipass, UTM), or **WSL2** for learning commands — deploy targets should be Linux or containers unless Part 27 applies.

---

## Phase A — Mental models (Days 1–3)

| Order | Part | Outcome |
|-------|------|---------|
| A0 | [00 Glossary](docs/00-glossary-and-map.md) | DevOps vs SRE vs platform; Linux role |
| A1 | [01 Mindset & lifecycle](docs/01-devops-mindset-lifecycle.md) | Plan → code → build → test → release → deploy → operate → monitor |
| A2 | [02 Linux vs other infra](docs/02-linux-vs-other-infrastructure.md) | When Linux, when PaaS, when K8s |
| A3 | [12 IaaS/PaaS/SaaS](docs/12-iaas-paas-saas-models.md) | Shared responsibility model |

**Checkpoint:** Explain to yourself who owns patching for EC2 vs RDS vs Vercel.

---

## Phase B — Linux operator skills (Days 4–10)

| Order | Part | Outcome |
|-------|------|---------|
| B1 | [03 Linux essentials](docs/03-linux-essentials.md) | FS, users, permissions, packages |
| B2 | [04 Networking](docs/04-networking-dns-tls.md) | IP, ports, DNS, TLS, firewalls |
| B3 | [05 systemd](docs/05-systemd-services.md) | Services, logs, boot |
| B4 | [20 Secrets & SSH](docs/20-secrets-identity-iam.md) | Keys, sudo, least privilege |
| B5 | [11 Workshop](docs/11-workshop-first-linux-server.md) | Hardened VPS + deploy static site |

**Checkpoint:** SSH key-only login, ufw, nginx serving HTTPS, `systemctl status` clean.

---

## Phase C — Delivery pipeline (Days 11–17)

| Order | Part | Outcome |
|-------|------|---------|
| C1 | [06 Git & CI basics](docs/06-git-and-ci-fundamentals.md) | Trunk, PR checks |
| C2 | [07 CI/CD](docs/07-cicd-pipelines.md) | Build, test, deploy stages |
| C3 | [08 Docker & Compose](docs/08-containers-docker-compose.md) | Images, volumes, compose stack |
| C4 | [10 Reverse proxy](docs/10-reverse-proxy-web.md) | TLS termination, routing |
| C5 | [17 Environments](docs/17-environments-promotion.md) | dev/staging/prod |
| C6 | [26 GitOps & strategies](docs/26-gitops-deployment-strategies.md) | Rolling, blue/green |

**Checkpoint:** Push to main → CI green → deploy to staging automatically.

---

## Phase D — Infrastructure at scale (Days 18–24)

| Order | Part | Outcome |
|-------|------|---------|
| D1 | [13 Terraform](docs/13-terraform-iac.md) | Declarative cloud resources |
| D2 | [14 Ansible](docs/14-ansible-config-management.md) | Repeatable server config |
| D3 | [15 Cloud map](docs/15-cloud-providers-map.md) | VPC, IAM, object storage |
| D4 | [16 Homelab / VMs](docs/16-bare-metal-vms-homelab.md) | Proxmox, libvirt concepts |
| D5 | [09 Kubernetes](docs/09-kubernetes-concepts.md) | When K8s is worth it |

**Checkpoint:** One Terraform module + Ansible role for same server profile.

---

## Phase E — Operate & secure (Days 25–35)

| Order | Part | Outcome |
|-------|------|---------|
| E1 | [18 Observability](docs/18-observability.md) | Logs, metrics, alerts |
| E2 | [19 Backup & DR](docs/19-backup-disaster-recovery.md) | RPO/RTO, restore drill |
| E3 | [21 DevSecOps](docs/21-devsecops-shift-left.md) | Shift left map |
| E4 | [22 Linux hardening](docs/22-linux-hardening.md) | sshd, fail2ban, updates |
| E5 | [23 Supply chain](docs/23-app-supply-chain-security.md) | SCA, SAST, SBOM |
| E6 | [24 Runtime security](docs/24-runtime-zero-trust.md) | Network policy lite |
| E7 | [25 Compliance logging](docs/25-compliance-logging-audit.md) | Audit trail |
| E8 | [27 Windows contrast](docs/27-windows-infra-contrast.md) | If you touch .NET/IIS |
| E9 | [28 FinOps](docs/28-finops-solo-constraints.md) | Cost caps |
| E10 | [99 FAQ](docs/99-faq-cheatsheet.md) | Reference |

**Checkpoint:** Runbook + on-call playbook for yourself; restore from backup once.

---

## Concept coverage matrix

| Topic | Part |
|-------|------|
| DevOps culture & CALMS | 01 |
| SDLC / DORA metrics | 01, 07 |
| Linux CLI & FHS | 03 |
| Windows vs Linux ops | 02, 27 |
| WSL2 vs prod Linux | 02 |
| macOS dev / Linux prod | 02 |
| TCP/IP, DNS, HTTP/S | 04 |
| systemd, journald | 05 |
| GitHub Actions / CI | 06, 07 |
| Docker, Compose | 08 |
| Kubernetes | 09 |
| nginx, Caddy | 10 |
| First server lab | 11 |
| IaaS/PaaS/SaaS | 12 |
| Terraform | 13 |
| Ansible | 14 |
| AWS/GCP/Azure concepts | 15 |
| Bare metal / Proxmox | 16 |
| Staging/prod | 17 |
| Prometheus/Grafana/Loki (concepts) | 18 |
| Backups | 19 |
| SSH, Vault, IAM | 20 |
| DevSecOps pipeline | 21 |
| CIS hardening | 22 |
| Dependabot, Trivy, Semgrep | 23 |
| WAF, mTLS (intro) | 24 |
| Audit logs | 25 |
| GitOps, Argo (intro) | 26 |
| Cost control | 28 |
