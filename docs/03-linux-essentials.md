# Part 3 — Linux Essentials for Operators

Assumes Ubuntu/Debian 24.04 (adjust package names for RHEL: `dnf`, `firewalld`).

---

## Filesystem hierarchy (FHS) — must know

| Path | Purpose |
|------|---------|
| `/` | Root |
| `/etc` | Config (sshd, nginx) |
| `/var` | Logs, spool, variable data |
| `/home` | User homes |
| `/tmp` | Temp (cleared on reboot) |
| `/usr/bin` | User commands |
| `/opt` | Optional third-party apps |
| `/proc`, `/sys` | Kernel interfaces |

**Rule:** config in `/etc`, not random home dirs, for production services.

---

## Essential commands (practice daily)

```bash
# Navigation & inspection
pwd; ls -la; cd; less; head; tail -f
find /var/log -name "*.log"
du -sh /var/*

# Files
cp mv rm mkdir touch
chmod 640 file; chown user:group file
ln -s target link

# Text
grep -r pattern /etc/nginx
sed -n '1,20p' file
cat /etc/os-release

# Processes
ps aux; top; htop
kill; kill -9  # last resort

# Users
whoami; id; sudo -i
useradd; usermod -aG sudo user
```

---

## Permissions model

```
rwx rwx rwx  = user group other
4+2+1 = 7
```

- **644** file — owner rw, world r  
- **600** secrets — owner only  
- **755** dir — traverse + list  
- **Never 777** on prod  

Directories need `x` to enter.

---

## Package management

```bash
sudo apt update
sudo apt install -y nginx curl git ufw fail2ban
apt search foo
apt show nginx
sudo apt upgrade -y   # security patches — schedule weekly
```

RHEL family: `dnf install`, `dnf update`.

---

## Editors & SSH

- Learn `nano` minimum; `vim` or IDE remote optional  
- SSH config `~/.ssh/config` for host aliases  
- **Ed25519 keys:** `ssh-keygen -t ed25519 -C "you@host"`

---

## Files worth reading on any new server

```bash
cat /etc/os-release
uname -a
free -h
df -h
ip a
ss -tlnp   # listening ports
```

---

## cron vs systemd timers

Prefer **systemd timers** for new work (Part 5). Legacy: `crontab -e`.

---

## Logs (before observability stack)

```bash
journalctl -u nginx -f
journalctl -xe
tail -f /var/log/auth.log   # Debian; RHEL: secure
```

---

## Common pitfalls

| Pitfall | Fix |
|---------|-----|
| Edit as root in home | Config under `/etc`, deploy user separate |
| No timezone set | `timedatectl set-timezone UTC` |
| Disk full | Log rotation, `journalctl --vacuum-time=7d` |
| Locale issues in scripts | `export LC_ALL=C.UTF-8` |

Next: [Part 4 — Networking](04-networking-dns-tls.md)
