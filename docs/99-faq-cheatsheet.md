# Part 99 — FAQ & Cheat Sheet

---

## FAQ

**Q: Do I need Linux if I use Vercel?**  
A: Learn concepts anyway; backend/workers/DB often still Linux somewhere. WSL2 enough for CLI learning.

**Q: Docker vs VM?**  
A: VM = whole OS; container = app isolation on shared Linux kernel. Prod: VM hosts containers.

**Q: Terraform vs Ansible?**  
A: Terraform creates cloud resources; Ansible configures OS inside them. Often both.

**Q: When Kubernetes?**  
A: When Compose on 2–3 VMs hurts — not day one.

**Q: Is WSL2 production?**  
A: No — dev only.

**Q: Windows Server for Node app?**  
A: Possible but uncommon — prefer Linux unless policy requires Windows.

**Q: First cert for job?**  
A: Not required to start — projects + this lab beat cert cramming for juniors.

**Q: DevOps vs DevSecOps?**  
A: DevSecOps = DevOps + automated security gates (Part 21+).

**Q: How patch production?**  
A: Unattended security updates on VM; rebuild container images on base image CVE; avoid manual SSH drift.

**Q: Where secrets live?**  
A: CI secrets + server env + vault — never git.

---

## Cheat sheet — new Linux server

```bash
# Update & tools
sudo apt update && sudo apt upgrade -y
sudo apt install -y ufw fail2ban nginx certbot

# User & SSH (after key copied)
sudo ufw allow OpenSSH && sudo ufw enable
# sshd: PermitRootLogin no, PasswordAuthentication no

# Docker
sudo apt install -y docker.io docker-compose-v2
sudo usermod -aG docker $USER

# Check
ss -tlnp; df -h; free -h; systemctl --failed
```

---

## Cheat sheet — debug outage

1. `curl -v` health URL  
2. `systemctl status` / `docker compose ps`  
3. `journalctl` / `docker compose logs`  
4. Disk full? `df -h`  
5. Cert expired? `certbot certificates`  
6. Recent deploy? rollback image  
7. Update runbook  

---

## Cheat sheet — CI security minimum

- gitleaks  
- lockfile audit  
- Trivy image scan  
- branch protection  

---

## Related learning

- [Solo software project management](https://github.com/belittlewho/solo-software-project-management) — release, RTM, NFRs  

Return to [README](../README.md).
