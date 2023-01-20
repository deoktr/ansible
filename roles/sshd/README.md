# SSH

Configure OpenSSH.

- Install OpenSSH
- Configure OpenSSH
- Manager SSH permissions with group

## Varialbes

- `sshd_port` SSH port, default: `ansible_port` or 22
- `sshd_users` list of users that should have access to SSH
- `sshd_group_name` SSH group name, default: `sshusers`
- `sshd_group_gid` SSH group gid, default: `1700`
- `sshd_from_ip` a list of IP or IP ranges that will be able to access SSH, default: `local_net`

## TODO

- Deal with removing of an IP from the `ssh_from_ip` list
