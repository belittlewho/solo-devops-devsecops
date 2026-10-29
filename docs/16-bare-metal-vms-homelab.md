# Part 16 — Bare Metal, VMs & Homelab

Learn infra without cloud bills — **Proxmox**, **Multipass**, **UTM**, **VirtualBox**.

---

## Layers

| Layer | Example |
|-------|---------|
| Bare metal | Old PC, Intel NUC |
| Type 1 hypervisor | Proxmox, ESXi |
| Type 2 hypervisor | VirtualBox on laptop |
| Cloud | Provider hypervisor (you rent) |

---

## Proxmox (popular homelab)

- Web UI for VMs and LXC containers  
- Snapshots before risky changes  
- VLANs for network practice  

**Use case:** staging cluster, Kubernetes lab, Windows + Linux side by side.

---

## Multipass (quick Ubuntu VMs)

```bash
multipass launch 24.04 --name dev --cpus 2 --memory 2G
multipass shell dev
```

Good for Ansible/Terraform local tests.

---

## Contrast: VM vs container vs bare metal app

| | Bare metal process | VM | Container |
|--|-------------------|-----|-----------|
| Isolation | Weak | Strong | Medium |
| Boot time | n/a | minutes | seconds |
| Density | low | medium | high |
| Use | DB perf niche | multi-tenant | microservices |

Production solo: **one Linux VM + Docker** beats homelab unless learning K8s.

---

## Physical server considerations

- UPS / power  
- RAID or backup strategy  
- Offsite backup (Part 19)  

Next: [Part 17 — Environments](17-environments-promotion.md)
