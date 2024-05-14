# Users

## Variables

| name                   | type                              | default   | description                           |
| ---------------------- | --------------------------------- | --------- | ------------------------------------- |
| `pass_max_days`        | int                               | `365`     | login.defs PASS_MAX_DAYS              |
| `pass_min_days`        | int                               | `1`       | login.defs PASS_MIN_DAYS              |
| `pass_warn_age`        | int                               | `7`       | login.defs PASS_WARN_AGE              |
| `uid_min`              | int                               | `1000`    | login.defs UID_MIN                    |
| `users`                | list[dict] (see below) (optional) | -         | List of users to create               |
| `shell_timeout`        | int                               | `900`     | Shell TMOUT                           |
| `remove_users`         | list[str]                         | []        | List of users to remove               |
| `default_ssh_key_type` | str                               | `ed25519` | Default ssh key type (for generation) |

For each users:

| name                  | type            | default                               | description             |
| --------------------- | --------------- | ------------------------------------- | ----------------------- |
| `name`                | str             | -                                     | User name               |
| `password`            | str (optional)  | **generate and store in credentials** | user password           |
| `update_password`     | str (optional)  | `on_create`                           | when to update password |
| `password_expire_max` | int (optional)  | _pass_max_days_                       |                         |
| `password_expire_min` | int (optional)  | _pass_min_days_                       |                         |
| `uid`                 | int (optional)  | -                                     | uid                     |
| `authorized_keys`     | str (optional)  | -                                     | authorized_keys         |
| `comment`             | str (optional)  | -                                     | comment                 |
| `expires`             | int (optional)  | `-1`                                  | password expire         |
| `force`               | bool (optional) | `false`                               | ansible user force      |
| `generate_ssh_key`    | bool (optional) | `false`                               | generate ssh key        |
| `ssh_key_type`        | str (optional)  | _default_ssh_key_type_                |                         |
| `ssh_key_comment`     | str (optional)  | _user.name_                           |                         |
| `ssh_key_passphrase`  | str (optional)  | _omit_                                |                         |
| `expire_password`     | bool (optional) | -                                     | Expire password         |

Example:

```yaml
users:
    - name: jeff
      uid: 1003
      authorized_keys: ...
```

For more information on variables please check the [ansible doc](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/user_module.html).

## TODO

-   Apply password expiry to root automatically
-   Remove users home when removing them, because it will be an unused UID that could then be attributed to another user
