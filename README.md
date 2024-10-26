# Ansible

Linux hardening Ansible roles for Debian and Arch based Linux servers and workstations.

The main idea of those roles is to control everything that is going on the server, for example: not a single port should be opened if it's not needed and not in use, not a single package should be installed if it's not needed. Also, every role should work independently of each other, I should always be able to configure ONLY ONE package, for example if I only want to configure chrony I should be able to WITHOUT having to install other packages. Ansible managed files should have the appropriate header placed on top.

General roles:

- **Aide**, install, configure, and add cron
- **AppArmor**, install, and add to grub
- **apt**, configure for internet or local proxy and configure UFW
- **audit**, install, configure, start, and add to grub
- **chrony**, install, configure, and configure UFW
- **cron**, install, start, and secure
- **fail2ban**, install, configure, and start
- **grub**, secure
- **logrotate**, install, configure
- **motd**, configure
- **mount**, configure mount options
- **network**, disable IPv6 via grub
- **pam**, install, configure to ensure password quality
- **resolvconf**, install, configure DNS, and configure UFW
- **rsyslog**, install, configure as server or sender, start, and configure UFW
- **security**, apply security mitigations when a package is vulnerable
- **setup**, remove a list of package
- **shared**, reboot
- **sshd**, install, configure, start, and setup sshd allow group
- **sudo**, install, configure, setup allow grooup, secure
- **sysctl**, configure
- **systemd**, configure journald
- **ufw**, install, configure, and start
- **users**, manage users and ssh keys, configure login.defs, and add autologout script

Other specific roles:

- **apt-cacher-ng**, install, configure, start, and configure UFW
- **bastion**, set up an SSH proxy jump server
- **clean**, remove Ansible backups
- **pam_oath**, install, and configure pam totp
- **squid**, install, configure, start, and configure UFW
- **suricata**, install, configure, start, add rules, and update with via cron

## Usage

Run the playbook:

```bash
ansible-playbook --ask-vault-password -i inventory.yaml play.yml
```

Run locally:

```bash
sudo ansible-playbook --connection=local --inventory 127.0.0.1, --limit 127.0.0.1 play.yml
```

## Variables

To add variables create a file called `all` in `group_vars`:

```bash
mkdir group_vars
touch group_vars/all
```

## Create vaulted var

```bash
ansible-vault encrypt_string
```

Copy the output inside [group_vars/all](./group_vars/all).

## Lint playbooks

```bash
ansible-lint roles
```

Note that the configuration for the linter is located in [.config/ansible-lint.yaml](./.config/ansible-lint.yml).

### Clean

```bash
docker rm ubuntu_sshd_container
docker rmi ubuntu_sshd_image
```

## Tags

Use tags `I` with number going form `I0` to `I4`, 0 being the less impactfull and 4 the most.

Example: MOTD is set to `I0` because it's impact is non-existent. But UFW is set to `I4` because if set up without allowing network services (opening ports) this can break a server.

## Debian

On Debian there is a few things you'll need to do before starting the Ansible script, you'll need to install sudo, add it to the user, reboot for the change to take effect.

```bash
apt install sudo
usermod -aG sudo $USER
reboot
```

Then you can start the Ansible script, it will stop after changing the Ansible user password, update it in inventory and restart it.

Or you can directly start it from root user via SSH.

## Links

- [ANSSI Guide hardening GNU/Linux](https://www.ssi.gouv.fr/guide/recommandations-de-securite-relatives-a-un-systeme-gnulinux/)
- [NIST National Checklist for Red Hat Enterprise Linux](https://ncp.nist.gov/checklist/909)
- [OpenSCAP](https://github.com/OpenSCAP/openscap)
- [ANSSI Secure OpenSSH](https://www.ssi.gouv.fr/administration/guide/recommandations-pour-un-usage-securise-dopenssh/)

## TODO

- If any package is not up to date update it and restart it
- Add option to disable user instead of deleting
- Remove every file permissions for non-root users on logs, or at least write
- Remove debian_chroot from .bashrc
- Run app in docker on the server
- Kill all process of a user we want to delete
- Find a solution for when rebooting if the ssh port changes
- Maybe don't change the ssh port ?
- Control the presence of SSH server with a variable
- Add tag 'security'
- Variable to enable IPv6
- Add aide role
- Add logwatch role: https://github.com/robertdebock/ansible-role-logwatch
- Add zabbix role: https://github.com/robertdebock/ansible-playbook-zabbix
- Make reboot optional !
- Add scope to variables, PAM variables should all start with `pam_` for example.

## License

Ansible deoktr is licensed under [GPLv3](./LICENSE).
