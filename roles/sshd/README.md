# SSH

Configure OpenSSH.

-   Install OpenSSH
-   Configure OpenSSH
-   Manager SSH permissions with group

## Variables

| name              | type      | default       | description                                             |
| ----------------- | --------- | ------------- | ------------------------------------------------------- |
| `sshd_port`       | int       | `22`          |                                                         |
| `sshd_users`      | list[str] | `[]`          |                                                         |
| `sshd_group_name` | str       | `sshusers`    |                                                         |
| `sshd_from_ip`    | list[str] | **local_net** | list of IP or IP ranges that will be able to access SSH |

## TODO

-   Deal with removing of an IP from the `ssh_from_ip` list
-   Ensure the directory `/etc/ssh/sshd_config.d/` exists
