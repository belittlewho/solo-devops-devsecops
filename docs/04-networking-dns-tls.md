# Part 4 — Networking, DNS & TLS

---

## Layers you touch as DevOps

| Layer | You configure |
|-------|----------------|
| L3 IP | Cloud VPC, ufw |
| L4 TCP/UDP | Ports 22, 80, 443, app ports |
| L7 HTTP | nginx, headers, redirects |
| DNS | A/AAAA/CNAME records |
| TLS | Certificates (Let’s Encrypt) |

---

## IP, ports, localhost

- **0.0.0.0** — listen all interfaces  
- **127.0.0.1** — loopback only (safe bind for dev)  
- **Private RFC1918:** 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16  

```bash
ss -tlnp          # what's listening
curl -v http://127.0.0.1:8080
traceroute example.com
dig +short A example.com
```

---

## Firewalls

**ufw (Ubuntu simple):**

```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow OpenSSH
sudo ufw allow 'Nginx Full'
sudo ufw enable
sudo ufw status verbose
```

**Cloud:** security groups / firewall rules **also** required — ufw alone insufficient if provider exposes all ports.

Contrast **Windows:** Windows Defender Firewall + NSG on Azure.

---

## DNS records (minimum)

| Type | Use |
|------|-----|
| A | hostname → IPv4 |
| AAAA | → IPv6 |
| CNAME | alias → another name |
| TXT | SPF, DKIM, domain verify |

TTL: lower during migrations; higher steady state.

---

## TLS / HTTPS

1. User hits `https://app.example.com`  
2. Server presents cert chain  
3. Browser verifies CA + hostname  

**Let’s Encrypt:** free automated certs via **HTTP-01** (port 80) or **DNS-01**.

Tools: **certbot**, **Caddy** (auto HTTPS), **nginx + certbot**.

**DevSecOps:** TLS 1.2+ only, strong ciphers, HSTS after stable.

---

## Reverse proxy role

Internet → **nginx:443** → `127.0.0.1:3000` app

Benefits: TLS, rate limit, static files, multiple apps one IP.

Part 10 details.

---

## VPC concept (cloud)

- **Public subnet:** load balancer, NAT  
- **Private subnet:** app, DB — no direct internet  

Even on single VPS you mimic: DB listens localhost/docker network only.

Next: [Part 5 — systemd](05-systemd-services.md)
