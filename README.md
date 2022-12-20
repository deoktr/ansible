# Ansible

Linux hardening ansible roles for Debian based Linux server.

- [ANSSI Guide hardening GNU/Linux](https://www.ssi.gouv.fr/guide/recommandations-de-securite-relatives-a-un-systeme-gnulinux/)
- [NIST National Checklist for Red Hat Enterprise Linux](https://ncp.nist.gov/checklist/909)
- [OpenSCAP](https://github.com/OpenSCAP/openscap)
- [ANSSI Secure OpenSSH](https://www.ssi.gouv.fr/administration/guide/recommandations-pour-un-usage-securise-dopenssh/)

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
ansible-lint roles
```

Note that the configuration for the linter is located in [.config/ansible-lint.yaml](./.config/ansible-lint.yml).

## Docker

### Build

```bash
docker build -t ubuntu_sshd_image .
docker run -d -P --add-host=host.docker.internal:host-gateway --name ubuntu_sshd_container ubuntu_sshd_image
docker inspect --format='{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' ubuntu_sshd_container
ssh-keygen -f "~/.ssh/known_hosts" -R "172.17.0.2"
ssh-copy-id root@172.17.0.2
```

The password is `root`.

You will be able to ping the host with:

```bash
ping host.docker.internal
```

### Clean

```bash
docker rm ubuntu_sshd_container
docker rmi ubuntu_sshd_image
```


## TODO

- If any package is not up to date update it and restart it
- Add timeout to remote shell with `TMOUT`, will it break Tmux ?
- Add variable to change the SSH port
- Add option to disable user instead of deleting
- Remove every file permissions for non root users on logs, or at least write
- Remove debian_chroot from .bashrc
- Run app in docker on the server
- Kill all process of a user we want to delete
- Find a solution for when rebooting if the ssh port changes
    Maybe don't change the ssh port ?
- Control the presence of SSH server with a variable

## Debian

On Debian there is a few things you'll need to do before starting the Ansible
script, you'll need to install sudo, add it to the user, reboot for the change
to take effect.

```
apt install sudo
usermod -aG sudo $USER
reboot
```

Then you can start the ansible script.

Or you can directly start it from root user via SSH.

