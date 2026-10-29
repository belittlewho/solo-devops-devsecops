# CI/CD pipeline specification — {{PROJECT}}

**Version:** 1.0  
**Date:**

---

## Triggers

| Event | Workflow |
|-------|----------|
| PR to main | ci.yml — lint, test, scan |
| Push main | ci.yml + deploy-staging.yml |
| Tag v* | deploy-prod.yml |

---

## Stages

| Stage | Tool | Pass criteria | Fail action |
|-------|------|---------------|-------------|
| Lint | eslint/ruff | zero errors | block merge |
| Unit test | jest/pytest | 100% pass | block |
| SCA | npm audit/trivy fs | no critical* | block |
| Secret scan | gitleaks | clean | block |
| Build | docker/npm | artifact produced | block |
| Image scan | trivy image | no critical* | block deploy |
| Deploy staging | SSH/helm | smoke 200 | alert |
| Deploy prod | manual approval | smoke 200 | rollback |

*Waivers documented in issue.

---

## Environments

| Env | URL | Deploy method | Secrets source |
|-----|-----|---------------|----------------|
| staging | | | GitHub env staging |
| prod | | | GitHub env production |

---

## Artifacts

| Artifact | Registry | Tag scheme |
|----------|----------|------------|
| Container | ghcr.io/org/app | git sha + semver |

---

## Rollback

Procedure:  
1.  
2.

---

## Observability hooks

- Post-deploy smoke:  
- Metrics dashboard:  
