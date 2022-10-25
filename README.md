# Ansible

## Usage

Run the playbook:

```bash
ansible-playbook --ask-vault-password -i inventory.yaml play.yaml
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

- If any package is not up to date update it and restart it
- Configure Bash to enable colors, history
- Add timeout to remote shell with `TMOUT`, will it break Tmux ?
- Add variable to change the SSH port
- Add configuration file for bash
- Add option to disable user instead of deleting
- Remove every file permissions for non root users on logs, or at least write
- Add auditd
- Remove debian_chroot from .bashrc
- Run app in docker on the server
- Restrict sudo usage to a group

