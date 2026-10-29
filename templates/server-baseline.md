# Linux server baseline checklist — {{HOSTNAME}}

**OS:** Ubuntu 24.04 LTS  
**Date applied:**  
**Applied by:**

---

## Identity & access

- [ ] Non-root deploy user with sudo
- [ ] SSH key auth only (`PasswordAuthentication no`)
- [ ] `PermitRootLogin no`
- [ ] `AllowUsers deploy` (or team list)
- [ ] Local admin uses ssh-agent; keys not on server

---

## Network

- [ ] ufw enabled: allow 22, 80, 443 only (adjust if needed)
- [ ] Cloud security group matches ufw
- [ ] fail2ban enabled for sshd
- [ ] App binds 127.0.0.1 unless public static/nginx

---

## Patching

- [ ] `unattended-upgrades` for security
- [ ] Reboot plan documented for kernel updates

---

## Time & locale

- [ ] `timedatectl set-timezone UTC`
- [ ] NTP synced (`timedatectl status`)

---

## Docker (if used)

- [ ] Docker CE or distro package updated
- [ ] Deploy user in `docker` group
- [ ] Compose file: no `:latest` in prod without pin
- [ ] `.env` mode 600, not in git

---

## Web / TLS

- [ ] nginx/Caddy configured
- [ ] certbot or Caddy auto TLS
- [ ] HTTP → HTTPS redirect

---

## Logging & monitoring

- [ ] journald size limit configured
- [ ] External uptime check on /health
- [ ] Disk alert threshold documented

---

## Backup

- [ ] DB backup cron → offsite encrypted
- [ ] Restore tested (date: )

---

## DevSecOps

- [ ] No secrets in world-readable files
- [ ] Image scan policy if CI deploys containers
- [ ] SSH known_hosts verified on first connect

---

## Sign-off

Server ready for production traffic: **Yes / No**
