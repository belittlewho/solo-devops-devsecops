# Part 11 — Workshop: First Linux Server (End-to-End)

**Goal:** Ubuntu VPS serving HTTPS app via Docker Compose + nginx, SSH hardening, CI deploy.

**Time:** 4–8 hours first time.

---

## 0. Prerequisites

- Domain you control (DNS)  
- VPS provider (Hetzner CX22, DO droplet, etc.) — **Ubuntu 24.04**  
- Local WSL2 or laptop with `ssh`  

---

## 1. Create VPS & DNS

1. Create droplet — SSH key only at create (no password).  
2. DNS A record: `app.yourdomain.com` → VPS IP.  
3. Wait propagation: `dig +short app.yourdomain.com`.

---

## 2. First login & baseline

```bash
ssh root@VPS_IP
adduser deploy
usermod -aG sudo deploy
rsync --archive --chown=deploy:deploy ~/.ssh /home/deploy
```

From local, test: `ssh deploy@VPS_IP`.

Use [templates/server-baseline.md](../templates/server-baseline.md) — disable root SSH, ufw, fail2ban, unattended-upgrades.

---

## 3. Install stack

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y docker.io docker-compose-v2 nginx certbot python3-certbot-nginx ufw fail2ban
sudo usermod -aG docker deploy
```

Log out/in for docker group.

---

## 4. Deploy app (Compose)

On server `/opt/myapp/docker-compose.yml` — app on `127.0.0.1:3000`.

```bash
cd /opt/myapp
docker compose pull   # or build
docker compose up -d
curl -s http://127.0.0.1:3000/health
```

---

## 5. nginx + TLS

Configure site (Part 10), `certbot --nginx`.

Verify: `https://app.yourdomain.com/health`

---

## 6. CI deploy (rsync or SSH)

GitHub Actions on tag:

```yaml
- name: Deploy
  env:
    SSH_KEY: ${{ secrets.VPS_SSH_KEY }}
  run: |
    echo "$SSH_KEY" > key && chmod 600 key
    ssh -i key deploy@$HOST 'cd /opt/myapp && git pull && docker compose up -d --build'
```

Prefer **pull image from registry** over git pull on server for immutability.

---

## 7. DevSecOps minimum on server

- [ ] SSH key only, `PasswordAuthentication no`  
- [ ] ufw allow 22, 80, 443  
- [ ] fail2ban sshd jail  
- [ ] auto security updates  
- [ ] `.env` not in git; permissions 600  

---

## 8. Operate

Create [runbook](../templates/runbook.md): restart, logs, rollback tag.

**Checkpoint passed** when friend can hit HTTPS URL and you can redeploy from CI.

Next: [Part 12 — IaaS/PaaS/SaaS](12-iaas-paas-saas-models.md)
