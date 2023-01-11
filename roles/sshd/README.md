# SSH

- Install OpenSSH
- COnfigure OpenSSH
- Manager SSH permissions with group

## Varialbes

- `ansible_port` Anssible/SSH port, default: 22
- `ssh_users` list of users that should have access to SSH
- `ssh_group_name` SSH group name, default: sshusers
- `ssh_group_gid` SSH group gid, default: 1700
- `ssh_from_ip` a list of IP or IP ranges that will be able to access SSH, default: any

## TODO

- Deal with removing of an IP from the `ssh_from_ip` list
