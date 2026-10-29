# Part 38 — Terraform Advanced: State, Drift, Tests, Policy

Workshop steps: [Part 50](50-workshop-terraform-ansible.md)

---

## Remote state (S3 + DynamoDB lock)

```hcl
terraform {
  backend "s3" {
    bucket         = "myorg-tfstate"
    key            = "prod/vps/terraform.tfstate"
    region         = "eu-central-1"
    dynamodb_table = "terraform-locks"
    encrypt        = true
  }
}
```

Never commit state with secrets unencrypted.

---

## Drift detection

```bash
terraform plan   # shows manual console changes
```

Schedule `terraform plan` in CI nightly; fail on drift in prod workspaces.

---

## Module layout

```
modules/
  vps/
    main.tf variables.tf outputs.tf
env/
  staging/main.tf  # module "vps" { source = "../../modules/vps" }
  prod/main.tf
```

---

## terraform test (1.6+)

```hcl
# tests/vps.tftest.hcl
run "valid_plan" {
  command = plan
  assert {
    condition     = hcloud_server.web.name == "web-01"
    error_message = "wrong name"
  }
}
```

---

## Policy as code

| Tool | Cloud |
|------|-------|
| `checkov` | Multi |
| `tfsec` | Multi |
| OPA / Conftest | Custom |
| Sentinel | Terraform Cloud |

CI: `checkov -d .` block on CRITICAL.

---

## Cross-region / multi-env

Separate state per env; same modules; `tfvars` for sizing. Peering in Part 40.

Next: [Part 39 — IaC alternatives & Packer](39-iac-alternatives-packer.md)
