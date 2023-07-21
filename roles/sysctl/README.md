# sysctl

Configure sysctl in `/etc/sysctl.d/`.

## Variables

| name                  | type | default | description                        |
| --------------------- | ---- | ------- | ---------------------------------- |
| `sysctl_disable_ipv6` | bool | `true`  | Disable IPv6 with sysctl variables |

## Problems

Sysctl can be configured from many different directories (see man), and on new Debian 11 installs there is for example a default file at `/usr/lib/sysctl.d/protect-links.conf` containing variables that change the value of fifos `fs.protected_fifos = 1`, the problem is that we edit the file `/etc/sysctl.d/10-fs.conf` that also chaneg the value of `protected_fifos` but to the value `2`. So we have a default file located outside `/etc/sysctl.d/` that change a variable we are trying to edit.

Possible solution: maybe use the Ansible sysctl builtin to edit sysctl config.
