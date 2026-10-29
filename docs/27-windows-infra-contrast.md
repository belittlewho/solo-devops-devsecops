# Part 27 — Windows Infrastructure Contrast

When your stack is .NET/IIS/AD, ops diverges from Linux — map equivalents.

---

## Side-by-side ops map

| Task | Linux | Windows Server |
|------|-------|----------------|
| Remote admin | SSH | RDP / WinRM |
| Package manager | apt/dnf | winget / Chocolatey (dev); Windows Update (OS) |
| Service manager | systemd | Services.msc / sc.exe |
| Web server | nginx | IIS |
| Firewall | ufw/nftables | Windows Firewall |
| Logs | journald, files | Event Viewer |
| Config mgmt | Ansible SSH | Ansible WinRM, DSC |
| Containers | Docker (Linux VM) | Linux containers on WCOW optional |
| Scripting | bash | PowerShell |

---

## IIS deployment pattern

- Site bindings, app pools (.NET version)  
- Cert in Windows cert store or ARR reverse proxy  
- Deploy via MSDeploy or CI artifact zip  

**DevSecOps:** same SAST/SCA in CI; Defender for Endpoint on server.

---

## Active Directory

- Central identity for corp laptops/servers  
- Group Policy hardening  
- DevSecOps: privileged access management, tiered admins  

Most greenfield web startups stay **Linux + cloud IAM** — AD when enterprise IT requires it.

---

## WSL2 + Windows host

- Dev in WSL2 Linux  
- Prod still Linux VPS or Azure App Service (Windows or Linux plan)  

Pick **Linux App Service plan** unless legacy Framework dependency.

---

## Hybrid org reality

Frontend Windows laptops, backend Linux in AWS — common. Document boundaries in threat model.

Next: [Part 28 — FinOps](28-finops-solo-constraints.md)
