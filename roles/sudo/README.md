# sudo

-   Install sudo
-   Configure sudo
-   Manager sudo permissions with group

## Variables

| name                  | type      | default                               | description         |
| --------------------- | --------- | ------------------------------------- | ------------------- |
| `sudo_group_name`     | str       | `sudo`                                |                     |
| `sudo_users`          | list[str] | _ansible_user_                        |                     |
| `ansible_user`        | str       | `ansible`                             |                     |
| `sudo_logfile`        | str       | `/var/log/sudo.log`                   |                     |
| `sudo_custom_lecture` | bool      | `true`                                | Enable sudo lecture |
| `sudo_lecture`        | str       | _see [defaults](./defaults/main.yml)_ | sudo lecture        |
