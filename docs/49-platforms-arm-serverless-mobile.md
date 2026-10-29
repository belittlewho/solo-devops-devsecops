# Part 49 — ARM64, macOS Dev, BSD & Serverless Decision Lab

---

## ARM64 (Graviton, Apple Silicon)

| Context | Notes |
|---------|-------|
| AWS Graviton | Cheaper EC2/RDS; build multi-arch images |
| Apple Silicon Mac | Dev native arm64; CI `runs-on: macos-14` or Linux arm runners |
| Docker | `docker buildx build --platform linux/amd64,linux/arm64` |

Test both arches in CI if users deploy to Graviton.

---

## macOS as dev host

- Docker Desktop / Colima / OrbStack  
- Production still Linux — use CI Linux job as truth  
- File system case-insensitivity pitfalls in Node tools  

---

## FreeBSD / OpenBSD (niche servers)

- FreeBSD: ZFS, jails, some hosting providers  
- OpenBSD: security-focused, pf firewall  
- Linux dominates job market; learn BSD if provider or interest dictates  

---

## Serverless vs container vs VM lab

Decision worksheet:

| Criterion | Weight | Serverless score | Container score | VM score |
|-----------|--------|------------------|-----------------|----------|
| Traffic spikiness | | | | |
| Long-running connections | | | | |
| Custom kernel needs | | | | |
| Ops time budget | | | | |
| Cost at current scale | | | | |

Highest weighted score wins **for next 6 months** — revisit quarterly.

---

## Mobile release pipelines (summary)

- **iOS:** macOS runner, Xcode, certificates in secure vault, Fastlane `beta` → TestFlight  
- **Android:** Linux, keystore secret, Play API service account  
- **OTA updates:** Expo EAS, CodePush (legacy)  

Separate from web deploy; shared versioning scheme optional.

Next: Workshops [50](50-workshop-terraform-ansible.md), [51](51-workshop-observability-install.md), [52](52-workshop-k3s-deploy.md)
