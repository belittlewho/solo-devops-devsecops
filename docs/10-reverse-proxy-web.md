# Part 10 — Reverse Proxy & Web Serving (nginx / Caddy)

---

## Why reverse proxy on Linux VPS

| Without | With nginx/Caddy |
|---------|------------------|
| App handles TLS | Central TLS |
| Port 3000 exposed | Only 443 public |
| One app per IP | Many vhosts |

---

## nginx minimal site

`/etc/nginx/sites-available/myapp`:

```nginx
server {
    listen 80;
    server_name app.example.com;
    location / {
        proxy_pass http://127.0.0.1:3000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```

```bash
sudo ln -s /etc/nginx/sites-available/myapp /etc/nginx/sites-enabled/
sudo nginx -t && sudo systemctl reload nginx
sudo certbot --nginx -d app.example.com
```

---

## Caddy alternative

Auto HTTPS:

```
app.example.com {
    reverse_proxy 127.0.0.1:3000
}
```

Good solo DX; nginx more universal in enterprises.

---

## Static files

```nginx
root /var/www/html;
location / { try_files $uri $uri/ /index.html; }
```

PaaS/CDN often replaces this layer for frontends.

---

## Security headers (DevSecOps)

```nginx
add_header X-Frame-Options "SAMEORIGIN" always;
add_header X-Content-Type-Options "nosniff" always;
add_header Referrer-Policy "strict-origin-when-cross-origin" always;
# HSTS after HTTPS stable:
# add_header Strict-Transport-Security "max-age=31536000" always;
```

Next: [Part 11 — Workshop](11-workshop-first-linux-server.md)
