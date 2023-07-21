# sudo

-   Install sudo
-   Configure sudo
-   Manager sudo permissions with group

## Variables

| name                  | type      | default                 | description         |
| --------------------- | --------- | ----------------------- | ------------------- |
| `sudo_group_name`     | str       | `sudo`                  |                     |
| `sudo_users`          | list[str] | **ansible_user**        |                     |
| `ansible_user`        | str       | `ansible`               |                     |
| `sudo_logfile`        | str       | `/var/log/sudo.log`     |                     |
| `sudo_custom_lecture` | bool      | `true`                  | Enable sudo lecture |
| `sudo_lecture`        | str       | _see defaults/main.yml_ | sudo lecture        |
