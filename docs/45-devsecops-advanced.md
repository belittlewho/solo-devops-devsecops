# Part 45 — DevSecOps Advanced (DAST, CSPM, Falco, PKI, IR)

---

## DAST (OWASP ZAP)

CI staging job:

```bash
docker run -t ghcr.io/zaproxy/zaproxy:stable zap-baseline.py \
  -t https://staging.example.com -r zap-report.html
```

Fail on HIGH after triage. Not replacement for unit tests.

---

## Penetration testing & bug bounty

| Stage | Action |
|-------|--------|
| Pre-launch | Fixed-scope pentest firm or OWASP ASVS self-audit |
| Ongoing | HackerOne/Bugcrowd program when revenue justifies |

Document scope and safe harbor.

---

## CSPM (cloud misconfig)

| Tool | Notes |
|------|-------|
| Prowler | AWS CIS checks CLI |
| ScoutSuite | Multi-cloud |
| Wiz / Orca | SaaS |

Schedule weekly; fix public S3, open SG 0.0.0.0/0.

---

## IAM access reviews

Quarterly CSV: users, keys age, admin policies. Remove stale keys; enforce MFA.

Policy as code: OPA on Terraform plans.

---

## Secrets rotation automation

AWS Secrets Manager rotation Lambda; Vault dynamic DB creds; GitHub org secret rotation schedule.

---

## PKI / mTLS lab (smallstep)

```bash
curl -fLO https://github.com/smallstep/cli/releases/download/v0.27.2/step_linux_amd64.tar.gz
step ca init
step ca certificate service.internal svc.crt svc.key
```

Internal services trust private CA; public users still use Let's Encrypt at edge.

---

## Falco (runtime K8s/Linux)

Detect shell in container, unexpected outbound connections. Rules from Falco community.

---

## Security incident response playbook

1. Contain (isolate instance, revoke keys)  
2. Preserve logs/imaging  
3. Eradicate  
4. Recover from clean backup  
5. Notify if PII (legal)  
6. Postmortem (Part 30)  

Separate from availability incidents.

Next: [Part 46 — Compliance](46-compliance-frameworks.md)
