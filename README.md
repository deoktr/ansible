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

## Lint playbooks

```bash
ansible-lint playbook.yaml
```

Note that the configuration for the linter is located in [.config/ansible-lint.yaml](./.config/ansible-lint.yml).

## TODO

- If any required package is not install, install and configure it
- If any package is not up to date update it and restart it
- Check for UFW configuration
- Setup and configure SSH
- Add crontab to update suricata rules
- Update suricata rules during the script
- Restart suricata if the config changes

