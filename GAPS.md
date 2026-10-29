# Gap audit — status (filled)

Previously missing topics from the original audit are now covered in **Parts 29–52**, additional **templates**, **examples/monitoring/**, and workshops **50–52**.

Use this file as an **index** from old gap category → new part.

---

## 1. Site reliability engineering (SRE)

| Topic | Part |
|-------|------|
| SLI / SLO / error budgets | [29](docs/29-sre-slo-error-budgets.md) + [slo-document template](templates/slo-document.md) |
| Incident severity SEV1–4 | [30](docs/30-incidents-postmortems-oncall-chaos.md) |
| Blameless postmortems | [30](docs/30-incidents-postmortems-oncall-chaos.md) + [postmortem template](templates/postmortem.md) |
| On-call / escalation | [30](docs/30-incidents-postmortems-oncall-chaos.md) + [on-call-policy](templates/on-call-policy.md) |
| Toil measurement | [30](docs/30-incidents-postmortems-oncall-chaos.md), [01](docs/01-devops-mindset-lifecycle.md) |
| Load testing / capacity | [31](docs/31-load-testing-capacity.md) |
| Chaos engineering | [30](docs/30-incidents-postmortems-oncall-chaos.md) |
| Game days / DR drills | [30](docs/30-incidents-postmortems-oncall-chaos.md) + [game-day-checklist](templates/game-day-checklist.md) |

---

## 2. Linux operations (depth)

| Topic | Part |
|-------|------|
| LVM, iostat, inodes, strace, perf, tcpdump | [32](docs/32-linux-operations-deep-dive.md) |
| nftables, logrotate, chrony | [32](docs/32-linux-operations-deep-dive.md) |
| SELinux / AppArmor exercises | [32](docs/32-linux-operations-deep-dive.md) |
| RHEL vs Debian | [32](docs/32-linux-operations-deep-dive.md) |

---

## 3. Networking & edge

| Topic | Part |
|-------|------|
| CDN, CloudFront, email DNS, IPv6 | [33](docs/33-edge-networking-cdn-vpn.md) |
| WireGuard, Tailscale, Cloudflare Tunnel | [33](docs/33-edge-networking-cdn-vpn.md) |
| HAProxy, WAF, Consul intro | [33](docs/33-edge-networking-cdn-vpn.md) |

---

## 4. CI/CD

| Topic | Part |
|-------|------|
| GitHub Actions reusable workflows, GHCR/ECR | [34](docs/34-cicd-advanced-platforms.md) |
| GitLab CI, Jenkins | [34](docs/34-cicd-advanced-platforms.md) |
| Monorepo, semantic release | [34](docs/34-cicd-advanced-platforms.md) |
| Migration gates, feature flags | [34](docs/34-cicd-advanced-platforms.md) |
| Mobile/desktop pipelines | [34](docs/34-cicd-advanced-platforms.md), [49](docs/49-platforms-arm-serverless-mobile.md) |

---

## 5. Containers & orchestration

| Topic | Part |
|-------|------|
| Production Compose, rootless, Podman | [35](docs/35-containers-production-advanced.md) |
| cosign, registry mirror | [35](docs/35-containers-production-advanced.md) |
| kubectl, Helm, Kustomize, Ingress | [36](docs/36-kubernetes-hands-on-helm.md) |
| Service mesh | [37](docs/37-service-mesh-ecs-notes.md) |
| ECS Fargate | [35](docs/35-containers-production-advanced.md), [37](docs/37-service-mesh-ecs-notes.md) |

---

## 6. IaC & config

| Topic | Part |
|-------|------|
| Remote state, drift, modules, terraform test | [38](docs/38-terraform-advanced-policy.md), [50](docs/50-workshop-terraform-ansible.md) |
| Pulumi, CDK, CFN, Bicep, Packer, cloud-init | [39](docs/39-iac-alternatives-packer.md) |
| Ansible vault + roles | [50](docs/50-workshop-terraform-ansible.md), [14](docs/14-ansible-config-management.md) |
| OPA/checkov policy | [38](docs/38-terraform-advanced-policy.md) |

---

## 7. Cloud depth

| Topic | Part |
|-------|------|
| VPC, NAT, peering | [40](docs/40-cloud-vpc-iam-storage.md) |
| IAM JSON policies, S3 hardening | [40](docs/40-cloud-vpc-iam-storage.md) |
| RDS, Redis, SQS, Lambda, CloudFront, EKS outline | [41](docs/41-cloud-managed-services-serverless.md) |
| Landing zone | [40](docs/40-cloud-vpc-iam-storage.md) |

---

## 8. Data & messaging

| Topic | Part |
|-------|------|
| PostgreSQL admin, pg_dump, PITR, replication | [42](docs/42-postgresql-operations.md) |
| Redis, PgBouncer | [42](docs/42-postgresql-operations.md), [43](docs/43-redis-queues-search.md) |
| RabbitMQ, SQS, Kafka intro, OpenSearch | [43](docs/43-redis-queues-search.md) |

---

## 9. Observability (hands-on)

| Topic | Part |
|-------|------|
| Prometheus, Grafana, Loki, Alertmanager, OTel | [44](docs/44-observability-stack-lab.md), [51](docs/51-workshop-observability-install.md) |
| Dashboards as code, synthetic, APM | [44](docs/44-observability-stack-lab.md) |
| Example compose | [examples/monitoring/](examples/monitoring/) |

---

## 10. DevSecOps depth

| Topic | Part |
|-------|------|
| DAST, pentest, bug bounty | [45](docs/45-devsecops-advanced.md) |
| CSPM, IAM reviews, rotation | [45](docs/45-devsecops-advanced.md) |
| PKI/mTLS, Falco, sec IR | [45](docs/45-devsecops-advanced.md) |
| SOC2, PCI, HIPAA mapping | [46](docs/46-compliance-frameworks.md) |

---

## 11. Platform engineering

| Topic | Part |
|-------|------|
| IDP, Backstage, golden paths, multi-tenant K8s | [47](docs/47-platform-engineering-idp.md) |

---

## 12. HA & scale

| Topic | Part |
|-------|------|
| Multi-AZ/region, GLB, sticky sessions, HPA | [48](docs/48-high-availability-autoscaling.md) |

---

## 13. Workshops & templates

| Item | Location |
|------|----------|
| Linux VPS | [11](docs/11-workshop-first-linux-server.md) |
| Terraform + Ansible | [50](docs/50-workshop-terraform-ansible.md) |
| Observability install | [51](docs/51-workshop-observability-install.md) |
| k3s | [52](docs/52-workshop-k3s-deploy.md) |
| Postmortem / SLO / on-call / game day | [templates/](templates/) |

---

## 14. Platform contrasts

| Topic | Part |
|-------|------|
| ARM64, macOS dev, BSD, serverless decision lab | [49](docs/49-platforms-arm-serverless-mobile.md) |
| Windows | [27](docs/27-windows-infra-contrast.md) |

---

## Remaining reality check

No written guide replaces **hours of hands-on**. Certifications, employer-specific stacks, and proprietary tools will always vary. If something is still thin for you, open a GitHub issue naming the part to expand.

**Full curriculum:** [STUDY-PATH.md](STUDY-PATH.md) · **TOC:** [README.md](README.md)
