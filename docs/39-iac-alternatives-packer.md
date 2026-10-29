# Part 39 — Pulumi, CDK, CloudFormation, Bicep & Packer

---

## When Terraform vs alternatives

| Tool | Language | Best for |
|------|----------|----------|
| Terraform | HCL | Industry default, all clouds |
| Pulumi | TS/Python/Go | Devs who want real code |
| AWS CDK | TS/Python | AWS-heavy, L2 constructs |
| CloudFormation | YAML/JSON | AWS native, slow iteration |
| Bicep | Bicep | Azure native |

Concepts transfer: state, plan, apply, modules/stacks.

---

## Pulumi sketch (TypeScript)

```typescript
import * as hcloud from "@pulumi/hcloud";
const server = new hcloud.Server("web", {
  serverType: "cx22",
  image: "ubuntu-24.04",
});
export const ip = server.ipv4Address;
```

---

## Packer golden image

```hcl
# build.pkr.hcl
source "hcloud" "ubuntu" {
  image  = "ubuntu-24.04"
  location = "nbg1"
}
build {
  sources = ["source.hcloud.ubuntu"]
  provisioner "shell" {
    script = "scripts/harden.sh"
  }
}
```

Terraform launches from snapshot — faster, consistent bootstraps.

---

## cloud-init

`/etc/cloud/cloud.cfg.d/` or provider user-data:

```yaml
#cloud-config
package_update: true
packages: [nginx, docker.io]
users:
  - name: deploy
    ssh_authorized_keys: [ "ssh-ed25519 AAAA..." ]
```

First boot only; Ansible for drift after.

Next: [Part 40 — VPC & IAM](40-cloud-vpc-iam-storage.md)
