# Known gaps & thin topics (honest audit)

The guide is **solo-oriented and Linux-first**. It gives breadth from zero to a production VPS + CI/CD + DevSecOps basics. It does **not** yet cover everything a mid-level platform/SRE role expects. Use this list to plan what to learn next outside or via future parts.

**Legend:** **Missing** = no dedicated part | **Thin** = mentioned only, not practice depth | **Partial** = basics only

---

## 1. Site reliability engineering (SRE)

| Topic | Status | Notes |
|-------|--------|-------|
| SLI / SLO / error budgets | **Thin** | Part 18 mentions SLO; no worked example or budget policy |
| Incident severity (SEV1–4) | **Missing** | |
| Blameless postmortems | **Thin** | Runbook mentions; no template or process |
| On-call rotation / paging | **Partial** | Solo “you are on-call”; no escalation tree |
| Toil measurement | **Thin** | Part 01 mentions toil |
| Capacity planning / load testing | **Missing** | k6/Locust not covered |
| Chaos engineering | **Missing** | |
| Game days / DR drills (structured) | **Partial** | Backup restore mentioned once |

---

## 2. Linux operations (depth)

| Topic | Status | Notes |
|-------|--------|-------|
| FHS, permissions, apt, basics | **Partial** | Part 03 — good start, not admin depth |
| Disk: LVM, `iostat`, inode exhaustion | **Missing** | |
| Performance: `strace`, `perf`, flamegraphs | **Missing** | |
| Advanced networking: `tcpdump`, conntrack | **Missing** | |
| nftables / iptables beyond ufw | **Thin** | ufw only |
| SELinux (RHEL) troubleshooting | **Thin** | Named in 22, not exercises |
| AppArmor profiles | **Thin** | |
| RHEL vs Debian family ops differences | **Partial** | Snippets only |
| Logrotate, `/var/log` hygiene | **Missing** | |
| NTP/chrony deep dive | **Thin** | |

---

## 3. Networking & edge

| Topic | Status | Notes |
|-------|--------|-------|
| DNS (A/AAAA/CNAME/TXT) | **Partial** | Part 04 |
| Email DNS (SPF, DKIM, DMARC) | **Missing** | |
| CDN (Cloudflare, CloudFront) | **Missing** | |
| IPv6 deployment | **Missing** | |
| VPN / WireGuard site-to-site | **Missing** | |
| Internal service discovery (Consul) | **Missing** | |
| HAProxy / cloud LB health checks | **Thin** | nginx focus |
| Web Application Firewall hands-on | **Thin** | Part 24 name-drop |
| Cloudflare Tunnel / Tailscale | **Thin** | One line in 24 |

---

## 4. CI/CD & version control

| Topic | Status | Notes |
|-------|--------|-------|
| GitHub Actions | **Partial** | Skeleton in 07 |
| GitLab CI, Jenkins, CircleCI | **Missing** | |
| Reusable workflows / pipeline templates | **Thin** | |
| Monorepo CI (Nx, Turborepo, paths) | **Missing** | |
| Artifact registries (GHCR, ECR) auth patterns | **Thin** | |
| Semantic release / conventional commits | **Missing** | |
| Database migration gates in CD | **Thin** | Part 26 brief |
| Feature flags in deploy pipeline | **Thin** | Part 17 mention |
| Mobile / desktop release pipelines | **Missing** | |

---

## 5. Containers & orchestration

| Topic | Status | Notes |
|-------|--------|-------|
| Dockerfile best practices | **Partial** | Part 08 |
| Docker Compose production patterns | **Partial** | Single-host pattern |
| Rootless Docker / Podman | **Missing** | |
| Image signing (cosign), provenance | **Thin** | Part 23 |
| Registry mirroring / air-gapped | **Missing** | |
| Kubernetes hands-on (kubectl, Helm) | **Thin** | Part 09 concepts only |
| Helm charts, Kustomize | **Missing** | |
| Ingress controllers (nginx, traefik) on K8s | **Missing** | |
| Service mesh (Istio, Linkerd) | **Missing** | |
| ECS/Fargate as AWS middle ground | **Missing** | |

---

## 6. Infrastructure as code & config

| Topic | Status | Notes |
|-------|--------|-------|
| Terraform basics | **Partial** | Part 13 — no full module lab |
| Remote state, locking, drift | **Thin** | |
| `terraform test`, policy (OPA/Sentinel) | **Missing** | |
| Pulumi, CDK, CloudFormation, Bicep | **Missing** | |
| Ansible vault + roles layout | **Partial** | Part 14 sketch |
| Packer golden images | **Missing** | |
| cloud-init only bootstrap | **Thin** | |
| Cross-cloud / multi-region IaC | **Missing** | |

---

## 7. Cloud platform depth

| Topic | Status | Notes |
|-------|--------|-------|
| AWS/GCP/Azure service map | **Partial** | Part 15 table |
| VPC design (subnets, NAT, peering) | **Missing** | |
| IAM policy writing (JSON) | **Thin** | Part 20 concepts |
| S3/GCS bucket policies, public access block | **Missing** | |
| Managed Kubernetes (EKS/GKE/AKS) setup lab | **Missing** | |
| Serverless (Lambda/Cloud Functions) ops | **Thin** | Part 02 table |
| CloudFront + S3 static hosting pattern | **Missing** | |
| RDS/Cloud SQL ops (params, failover) | **Missing** | |
| ElastiCache / Redis managed | **Missing** | |
| SQS/SNS/EventBridge patterns | **Missing** | |
| Landing zone / org accounts | **Thin** | Part 15 |

---

## 8. Data layer & messaging (ops)

| Topic | Status | Notes |
|-------|--------|-------|
| PostgreSQL admin (roles, extensions, vacuum) | **Missing** | |
| Backups (`pg_dump`, PITR, WAL) | **Thin** | Part 19 generic |
| Replication / failover | **Missing** | |
| Redis ops ( persistence, eviction) | **Missing** | |
| Connection pooling (PgBouncer) | **Missing** | |
| Message queues (RabbitMQ, SQS, Kafka intro) | **Missing** | |
| Search (OpenSearch/Elasticsearch ops) | **Missing** | |

---

## 9. Observability (hands-on)

| Topic | Status | Notes |
|-------|--------|-------|
| Logs/metrics/traces concepts | **Partial** | Part 18 |
| Install Prometheus + Grafana + node_exporter | **Missing** | |
| Loki or ELK stack | **Missing** | |
| OpenTelemetry instrumentation | **Missing** | |
| Alertmanager rules & routing | **Missing** | |
| Dashboards as code | **Missing** | |
| APM (Datadog, Honeycomb) | **Missing** | |
| Synthetic monitoring | **Thin** | UptimeRobot mention |

---

## 10. DevSecOps (depth)

| Topic | Status | Notes |
|-------|--------|-------|
| Shift-left map, gitleaks, Trivy, Semgrep | **Partial** | Parts 21–23 |
| DAST (ZAP, Burp automation) | **Missing** | |
| Penetration testing / bug bounty process | **Missing** | |
| IAM policy as code, least-privilege reviews | **Thin** | |
| CSPM (cloud misconfig scanners) | **Missing** | |
| Secrets rotation automation | **Thin** | |
| PKI / internal CA / mTLS setup lab | **Missing** | |
| Container runtime security (Falco) | **Missing** | |
| PCI-DSS / HIPAA control mapping | **Thin** | Part 25 high level |
| SOC2 trust services criteria walkthrough | **Missing** | |
| Security incident response playbooks | **Partial** | Part 24 list |

---

## 11. Platform engineering & org patterns

| Topic | Status | Notes |
|-------|--------|-------|
| Internal developer platforms (IDP) | **Missing** | |
| Backstage / service catalog | **Missing** | |
| Golden paths | **Missing** | |
| Multi-team tenancy on K8s | **Missing** | |

---

## 12. High availability & scale

| Topic | Status | Notes |
|-------|--------|-------|
| Multi-AZ / multi-region | **Missing** | |
| Active-active vs active-passive | **Thin** | Part 26 strategies |
| Global load balancing | **Missing** | |
| Session affinity / sticky sessions | **Missing** | |
| Autoscaling (HPA, cluster autoscaler) | **Missing** | |

---

## 13. Workshops & templates

| Item | Status |
|------|--------|
| First Linux VPS workshop | **Present** | Part 11 |
| Second lab (Terraform + Ansible end-to-end) | **Missing** |
| Third lab (observability stack) | **Missing** |
| Fourth lab (EKS or k3s deploy) | **Missing** |
| Postmortem template | **Missing** |
| SLO document template | **Missing** |
| On-call policy template | **Missing** |

---

## 14. Contrasts & platforms (still light)

| Topic | Status | Notes |
|-------|--------|-------|
| Linux vs Windows Server | **Partial** | Parts 02, 27 |
| WSL2 vs prod Linux | **Partial** | Part 02 |
| macOS as dev host | **Thin** | |
| FreeBSD / OpenBSD | **Missing** | |
| ARM64 (Graviton, Apple Silicon builds) | **Missing** | |
| Serverless vs container vs VM decision lab | **Partial** | |

---

## 15. Cross-links

| Related skill | Where today |
|---------------|-------------|
| Release requirements, RTM, NFRs | [solo-software-project-management](https://github.com/belittlewho/solo-software-project-management) |
| Application architecture | Not in this repo |

---

## Suggested order to close gaps (solo)

1. **SRE basics** — SLO doc + postmortem template + one load test  
2. **Data ops** — Postgres backup/restore lab on same VPS  
3. **Observability lab** — Prometheus + Grafana on VPS  
4. **Terraform lab** — module for VPS + remote state  
5. **CDN + DNS** — Cloudflare in front of Part 11 server  
6. **K8s** — only if Compose hurts; k3s homelab (Part 16)  

Open a GitHub issue on this repo to vote for the next part number (29+).
