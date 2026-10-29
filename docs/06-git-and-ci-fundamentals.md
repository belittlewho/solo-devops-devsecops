# Part 6 — Git & CI Fundamentals

---

## Trunk-based vs GitFlow (solo)

| Model | Solo recommendation |
|-------|---------------------|
| **Trunk-based** | Short-lived branches → PR → `main` | ✅ Default |
| GitFlow | long-lived develop/release | Overkill unless enterprise |

Protect `main`: require CI pass before merge.

---

## Branch protections

- Require status checks (lint, test, security scan)  
- No force push to main  
- Signed commits (optional, advanced)

---

## What CI must do (minimum)

1. Checkout  
2. Install deps (cached)  
3. Lint + unit tests  
4. Build artifact or image  
5. (Optional) push image on tag  

**DevSecOps add:** secret scan, SCA, SAST (Part 23).

---

## Secrets in CI

- Never commit `.env`  
- Use GitHub **Secrets** / GitLab variables  
- Mask in logs  
- OIDC to cloud (no long-lived AWS keys in CI) — Part 20  

---

## Pre-commit locally

```bash
# Example tools
pre-commit install
# hooks: gitleaks, eslint, black
```

Shift left: catch before CI burns minutes.

Next: [Part 7 — CI/CD pipelines](07-cicd-pipelines.md)
