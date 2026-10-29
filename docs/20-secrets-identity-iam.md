# Part 20 — Secrets, SSH & IAM

---

## SSH hardening (Linux)

`/etc/ssh/sshd_config`:

```
PermitRootLogin no
PasswordAuthentication no
PubkeyAuthentication yes
AllowUsers deploy
```

```bash
sudo systemctl reload sshd
```

Use **ssh-agent** locally; **hardware key** optional (YubiKey).

---

## sudo

- `visudo` — syntax safe  
- Grant specific commands, not blanket NOPASSWD unless CI user scoped  

---

## Secrets storage tiers

| Tier | Tool |
|------|------|
| Local dev | `.env` gitignored |
| CI | GitHub Secrets |
| Prod app | Env vars, Docker secrets |
| Team | HashiCorp Vault, AWS Secrets Manager |
| TLS private keys | On server or LB only |

Never: secrets in Terraform plain text, Slack, screenshots.

---

## Cloud IAM patterns

- **Human:** MFA, least privilege groups  
- **CI OIDC:** GitHub → AWS role (no AKIA keys)  
- **App on EC2:** instance profile  
- **K8s:** IRSA / workload identity  

---

## Rotation

Schedule: DB passwords, API keys, deploy keys — calendar reminder 90 days.

DevSecOps: detect leaks with **gitleaks** in CI.

Next: [Part 21 — DevSecOps](21-devsecops-shift-left.md)
