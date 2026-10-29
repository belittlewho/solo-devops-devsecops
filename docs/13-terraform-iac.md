# Part 13 — Terraform & Infrastructure as Code

**IaC:** desired state in files; `terraform apply` reconciles cloud.

---

## Why not clickops

| Clickops | Terraform |
|----------|-----------|
| Undocumented | Git history |
| Drift | Plan shows diff |
| Hard reproduce | Same module = staging/prod |

---

## Core workflow

```bash
terraform init
terraform plan
terraform apply
terraform destroy   # careful
```

Files:

- `main.tf` — resources  
- `variables.tf` — inputs  
- `outputs.tf` — IPs, endpoints  
- `terraform.tfvars` — **gitignore** secrets  

---

## Minimal VPS pattern (concept)

Use provider module for Hetzner/DO/AWS:

```hcl
terraform {
  required_providers {
    hcloud = { source = "hetznercloud/hcloud" }
  }
}
variable "ssh_key_id" { type = number }
resource "hcloud_server" "web" {
  name        = "web-01"
  image       = "ubuntu-24.04"
  server_type = "cx22"
  ssh_keys    = [var.ssh_key_id]
}
output "ipv4" { value = hcloud_server.web.ipv4_address }
```

---

## State

- **Remote state** (S3 + DynamoDB lock) for teams  
- Solo: local ok initially; backup `terraform.tfstate`  

Never commit secrets in state — use sensitive outputs carefully.

---

## Modules & environments

```
infra/
  modules/vps/
  env/staging/main.tf
  env/prod/main.tf
```

Same module, different `tfvars`.

---

## DevSecOps

- `terraform plan` in CI on PR  
- Policy as code (OPA/Sentinel) optional  
- Least privilege IAM for apply role  

Contrast: **Ansible** configures OS **after** VM exists (Part 14) — often used together.

Next: [Part 14 — Ansible](14-ansible-config-management.md)
