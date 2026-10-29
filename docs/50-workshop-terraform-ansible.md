# Part 50 — Workshop: Terraform + Ansible End-to-End

**Goal:** Provision Ubuntu VPS with Terraform; configure with Ansible; deploy Compose app.

**Time:** 4–6 hours.

---

## Prerequisites

- Hetzner/DigitalOcean/AWS account + API token  
- Local: terraform, ansible, ssh key  
- Optional: S3 bucket for remote state  

---

## Step 1 — Terraform module

```
infra/
  modules/vps/
  env/staging/
    main.tf
    terraform.tfvars   # gitignored
    backend.tf
```

`main.tf`:

```hcl
module "vps" {
  source = "../../modules/vps"
  name   = "staging-web"
  type   = "cx22"
  ssh_key_ids = [var.ssh_key_id]
}
output "ip" { value = module.vps.ipv4 }
```

```bash
cd env/staging
terraform init
terraform apply
```

Save IP to `ansible/inventory/staging.ini`.

---

## Step 2 — Ansible role structure

```
ansible/
  inventory/staging.ini
  roles/common/tasks/main.yml      # ufw, fail2ban, docker
  roles/app/tasks/main.yml         # compose deploy
  site.yml
```

`site.yml`:

```yaml
- hosts: web
  become: true
  roles: [common, app]
```

```bash
ansible-playbook -i inventory/staging.ini site.yml
```

Vault secrets: `ansible-vault encrypt group_vars/web/vault.yml`

---

## Step 3 — CI integration

GitHub Actions:

- PR: `terraform plan` comment  
- Merge main: `terraform apply` then `ansible-playbook`  
- OIDC to cloud if AWS  

---

## Step 4 — Drift check

Nightly `terraform plan` workflow; alert on diff.

---

## Step 5 — Verify

HTTPS health check; update runbook with Terraform + Ansible commands.

**Checkpoint:** destroy with `terraform destroy` only in staging; prod requires approval gate.

Next: [Part 51 — Observability workshop](51-workshop-observability-install.md)
