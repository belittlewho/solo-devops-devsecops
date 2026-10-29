# Part 32 — Linux Operations Deep Dive

Extends Part 03 for production troubleshooting.

---

## Disk & LVM

```bash
lsblk
df -h
df -i                    # inode exhaustion
sudo vgs; sudo lvs; sudo pvs
sudo lvextend -L +10G /dev/vg0/root
sudo resize2fs /dev/vg0/root   # ext4
```

**Symptom:** disk 100% but few files → check `df -i`.

---

## I/O performance

```bash
sudo apt install sysstat
iostat -xz 1
iotop -o
```

---

## CPU / process debugging

```bash
htop
pidstat 1
strace -p PID -f -e trace=network,file   # short bursts only
perf top                               # needs linux-tools
```

Flamegraphs: `perf record` + Brendan Gregg scripts — use on staging.

---

## Networking debug

```bash
sudo apt install tcpdump
sudo tcpdump -i any port 443 -n
ss -tunap
conntrack -L | head   # if nf_conntrack
```

---

## nftables (below ufw)

ufw is frontend to iptables/nftables. Raw rules:

```bash
sudo nft list ruleset
```

For custom rules ufw cannot express, use `/etc/nftables.conf` — document in runbook.

---

## logrotate

`/etc/logrotate.d/myapp`:

```
/var/log/myapp/*.log {
    daily
    rotate 14
    compress
    delaycompress
    missingok
    notifempty
    copytruncate
}
```

Plus `journalctl --vacuum-size=500M`.

---

## chrony (NTP)

```bash
timedatectl status
chronyc sources -v
```

Breakage breaks TLS and distributed logs correlation.

---

## SELinux (RHEL/Alma)

```bash
getenforce
sudo ausearch -m avc -ts recent
sudo semanage port -l | grep http
```

Fix with correct context (`httpd_sys_content_t`), not permanent `setenforce 0`.

---

## AppArmor (Ubuntu)

```bash
sudo aa-status
sudo journalctl | grep apparmor
```

Custom profile for nginx/php if needed.

---

## Debian vs RHEL cheat

| Task | Debian/Ubuntu | RHEL/Alma |
|------|---------------|-----------|
| Packages | apt | dnf |
| Firewall | ufw | firewalld |
| SELinux | optional | enforcing common |
| Service logs | journald | journald |
| Web root | `/var/www` | `/usr/share/nginx/html` |

Next: [Part 33 — Edge & networking](33-edge-networking-cdn-vpn.md)
