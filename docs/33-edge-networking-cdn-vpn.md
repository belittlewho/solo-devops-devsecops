# Part 33 — Edge: CDN, Email DNS, IPv6, VPN, LB, WAF

---

## CDN (Cloudflare pattern)

1. Point domain NS to Cloudflare (or CNAME flattening)  
2. Origin = your VPS IP; **orange cloud** proxy ON  
3. SSL mode: **Full (strict)** with origin cert or Let’s Encrypt  
4. Cache static assets; bypass cache for `/api/*`  

**Benefits:** DDoS absorption, edge TLS, HTTP/3, WAF rules.

---

## CloudFront + S3 (AWS static)

Origin access control (OAC); bucket **block all public access**; CloudFront OAI/OAC only.

See Part 41 for full pattern.

---

## Email DNS (operational)

| Record | Purpose |
|--------|---------|
| **SPF** TXT | Who may send mail `@yourdomain` |
| **DKIM** TXT/CNAME | Sign outbound |
| **DMARC** TXT | Policy for fail SPF/DKIM |

Use provider wizard (Resend, SendGrid, Google Workspace). Misconfig → spam folder, not app outage.

---

## IPv6

```bash
ip -6 addr
```

DNS **AAAA** record; ufw allow 443 on v6; certbot `--nginx` v6. Test `curl -6 https://[...]`.

---

## WireGuard site-to-site / admin VPN

```bash
sudo apt install wireguard
wg genkey | tee privatekey | wg pubkey > publickey
```

`/etc/wireguard/wg0.conf` — peers for laptop → access private DB subnet without public DB port.

**Contrast Tailscale:** mesh VPN zero-config; good solo; WireGuard raw = more control.

---

## Cloudflare Tunnel (no open inbound ports)

`cloudflared tunnel` → outbound only to Cloudflare; origin never exposes 443 publicly.

---

## HAProxy (when nginx isn’t enough)

TCP + HTTP balancing, health checks:

```
backend app
  option httpchk GET /health
  server app1 127.0.0.1:3001 check
  server app2 127.0.0.1:3002 check
```

Cloud LB: configure health check path, interval, unhealthy threshold.

---

## WAF hands-on (Cloudflare)

- OWASP core ruleset managed  
- Rate limit `/login`  
- Geo block if abuse region (careful false positives)  

---

## Consul (service discovery intro)

Agents register services; DNS `service.consul`. Use when multiple nodes — overkill single VPS.

Next: [Part 34 — CI/CD advanced](34-cicd-advanced-platforms.md)
