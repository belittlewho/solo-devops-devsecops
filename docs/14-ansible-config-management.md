# Part 14 — Ansible & Configuration Management

Ansible pushes **desired configuration** to Linux hosts over SSH.

---

## When Ansible vs user-data vs golden image

| Tool | Best for |
|------|----------|
| cloud-init / user-data | First boot only |
| Ansible | Ongoing config, many servers |
| Packer | Build golden AMI once |

---

## Inventory

`inventory.ini`:

```ini
[web]
staging ansible_host=staging.example.com
prod ansible_host=prod.example.com

[web:vars]
ansible_user=deploy
```

---

## Playbook sketch

```yaml
- hosts: web
  become: true
  tasks:
    - name: Ensure nginx
      apt:
        name: nginx
        state: present
    - name: Copy site config
      template:
        src: templates/nginx-site.j2
        dest: /etc/nginx/sites-available/myapp
      notify: reload nginx
  handlers:
    - name: reload nginx
      service:
        name: nginx
        state: reloaded
```

```bash
ansible-playbook -i inventory.ini site.yml --check
ansible-playbook -i inventory.ini site.yml
```

---

## Idempotency

Running twice should not break — Ansible checks state.

---

## Secrets

Use **Ansible Vault** for encrypted vars — not plaintext in git.

---

## Windows note

Ansible supports `winrm` — see Part 27.

Next: [Part 15 — Cloud providers map](15-cloud-providers-map.md)
