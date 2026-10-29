# Part 22 — Linux Hardening & CIS Baseline

Use [server-baseline](../templates/server-baseline.md) as checklist. Aligns with **CIS Ubuntu Benchmark** spirit (read summary, don't obsess every line solo).

---

## Essential controls

| Control | Action |
|---------|--------|
| Patch management | `unattended-upgrades` security |
| SSH | Keys only, no root |
| Firewall | ufw or cloud SG default deny |
| Brute force | fail2ban sshd |
| Least privilege | separate deploy user, no daily sudo |
| File perms | 600 secrets, no world-writable |
| Audit | auth.log monitoring |

---

## unattended-upgrades (Debian/Ubuntu)

```bash
sudo apt install -y unattended-upgrades
sudo dpkg-reconfigure -plow unattended-upgrades
```

Reboot strategy: `needrestart` or maintenance window for kernel updates.

---

## fail2ban

```bash
sudo apt install -y fail2ban
sudo systemctl enable --now fail2ban
sudo fail2ban-client status sshd
```

---

## Kernel / sysctl (selected)

```bash
# /etc/sysctl.d/99-hardening.conf
net.ipv4.conf.all.rp_filter = 1
net.ipv4.tcp_syncookies = 1
```

Apply: `sudo sysctl --system`

---

## AppArmor / SELinux

- Ubuntu: AppArmor profiles for nginx, docker (default partial)  
- RHEL: SELinux enforcing — learn before disabling  

---

## Contrast Windows hardening

- Windows Update, Defender, RDP restrictions, LAPS for admin passwords  
- Group Policy baselines  

Part 27.

Next: [Part 23 — Supply chain security](23-app-supply-chain-security.md)
