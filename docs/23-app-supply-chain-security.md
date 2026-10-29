# Part 23 — Application & Supply Chain Security

---

## SCA (dependencies)

```bash
npm audit
pip audit
trivy fs .
```

Dependabot/Renovate PRs — review, don't blind merge.

**Pin lockfiles** in CI: `npm ci`, not `npm install`.

---

## SAST (source)

- **Semgrep** — custom rules  
- **CodeQL** — GitHub native  
- **golangci-lint** with security tags  

Run on every PR; block only on agreed severity.

---

## Container image

```bash
docker build -t myapp:$GIT_SHA .
trivy image --severity CRITICAL,HIGH myapp:$GIT_SHA
```

Use minimal base (`-slim`, `alpine` with caution — musl quirks), non-root USER.

---

## SBOM

Generate CycloneDX/SPDX in CI — needed for enterprise customers increasingly.

```bash
# example with syft
syft packages dir:. -o cyclonedx-json > sbom.json
```

---

## Signing (advanced)

- **cosign** sign images  
- **SLSA** levels — aspirational for solo  

---

## Secrets in repo

- gitleaks, trufflehog pre-commit  
- If leak: rotate immediately, `git filter-repo` if needed  

Next: [Part 24 — Runtime security](24-runtime-zero-trust.md)
