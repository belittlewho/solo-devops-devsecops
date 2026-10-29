# Part 5 — systemd & Services

**systemd** is PID 1 on most Linux servers — manages boot, services, timers, logs.

---

## Unit types

| Type | Example |
|------|---------|
| `.service` | nginx, your app |
| `.timer` | scheduled jobs |
| `.socket` | socket activation |

---

## Service lifecycle

```bash
sudo systemctl status nginx
sudo systemctl start nginx
sudo systemctl stop nginx
sudo systemctl restart nginx
sudo systemctl enable nginx    # boot start
sudo systemctl disable nginx
sudo systemctl daemon-reload   # after unit file edit
```

---

## Minimal custom service

`/etc/systemd/system/myapp.service`:

```ini
[Unit]
Description=My App
After=network.target

[Service]
Type=simple
User=deploy
WorkingDirectory=/opt/myapp
Environment=NODE_ENV=production
ExecStart=/usr/bin/node dist/server.js
Restart=on-failure
RestartSec=5

[Install]
WantedBy=multi-user.target
```

```bash
sudo systemctl daemon-reload
sudo systemctl enable --now myapp
journalctl -u myapp -f
```

**DevSecOps:** run as non-root `User=`; `ProtectSystem=strict` etc. for hardening (Part 22).

---

## journald

```bash
journalctl -u myapp --since "1 hour ago"
journalctl -p err -b
```

Persist logs: `/etc/systemd/journald.conf` — `SystemMaxUse=500M`.

Contrast **Windows:** Event Log + Services.msc.

---

## systemd vs Docker

| systemd service | Container |
|-----------------|-----------|
| One binary on host | Packaged image |
| Host libraries | Image libs |
| Good simple apps | Good reproducibility |

Often: **Docker** for app, **systemd** only for docker daemon or compose plugin.

Next: [Part 6 — Git & CI](06-git-and-ci-fundamentals.md)
