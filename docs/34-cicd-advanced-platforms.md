# Part 34 — CI/CD Advanced (GitLab, Jenkins, Monorepos)

---

## GitHub Actions depth

**Reusable workflow** `.github/workflows/reusable-test.yml`:

```yaml
on:
  workflow_call:
    inputs:
      node-version:
        required: true
        type: string
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: ${{ inputs.node-version }}
      - run: npm ci && npm test
```

Caller: `uses: ./.github/workflows/reusable-test.yml` with `secrets: inherit`.

---

## GHCR / ECR auth

**GHCR:**

```yaml
- uses: docker/login-action@v3
  with:
    registry: ghcr.io
    username: ${{ github.actor }}
    password: ${{ secrets.GITHUB_TOKEN }}
```

**ECR:** `aws ecr get-login-password` or OIDC role `amazon-ecr-login`.

Tag: `ghcr.io/org/app:${{ github.sha }}`.

---

## GitLab CI (equivalent mental model)

`.gitlab-ci.yml`:

```yaml
stages: [test, build, deploy]
test:
  stage: test
  script: npm ci && npm test
deploy_staging:
  stage: deploy
  script: ./deploy.sh staging
  environment: staging
  only: [main]
```

Runners: shared or self-hosted on Linux.

---

## Jenkins (legacy but common)

Pipeline as `Jenkinsfile` (declarative). Self-host on Linux VM; plugins for Docker, credentials. Prefer Actions/GitLab for greenfield solo.

---

## Monorepo CI (path filters)

GitHub Actions:

```yaml
on:
  push:
    paths:
      - 'apps/storefront/**'
      - 'packages/shared/**'
```

Turborepo/Nx: remote cache + affected graph — run tests only for changed packages.

---

## Semantic release

Conventional commits (`feat:`, `fix:`) → automated semver + changelog + git tag → triggers prod deploy.

Tools: `semantic-release`, `release-please`.

---

## DB migration gates

Pipeline order:

1. Deploy new code **backward compatible**  
2. Run migrations job (`flyway`, `prisma migrate`, `alembic`)  
3. Smoke test  
4. Enable feature flag  

Rollback: reversible migrations only, or backup before migrate.

---

## Feature flags in CD

LaunchDarkly, Unleash (self-host), or env `FEATURE_X=0`. Deploy ≠ release.

---

## Mobile / desktop (brief)

| Platform | CI notes |
|----------|----------|
| iOS | macOS runner; Fastlane; TestFlight |
| Android | Linux; Gradle; Play upload key in secrets |
| Electron | Same as web + code sign certs |

Use separate workflow files; not slower web pipeline.

Next: [Part 35 — Containers advanced](35-containers-production-advanced.md)
