# Ansible

## Usage

Run the playbook:

```bash
ansible-playbook --ask-vault-password -i inventory.yaml playbook.yaml
```

## Create vaulted var

```bash
ansible-vault encrypt_string
```

Copy the output inside [group_vars/all](./group_vars/all).
