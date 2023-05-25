# mount

Manage partition mount options.

## Variables

| name                   | type                    | default                | description                    |
| ---                    | ---                     | ---                    | ---                            |
| `mount_state_default`  | str                     | `present`              | Default value for state        |
| `mount_passno_default` | int                     | `2`                    | Default valut for passno       |
| `mounts`               | list[dict] (see bellow) | *see default/main.yml* | List of partition with options |

For each partition *mounts*:

| name      | type           | default                | description    |
| ---       | ---            | ---                    | ---            |
| `path`    | str            | -                      | Partition path |
| `options` | str            | -                      | Options        |
| `state`   | str (optional) | *mount_state_default*  |                |
| `passno`  | int (optional) | *mount_passno_default* |                |

Example:

```
mounts:
  - path: /
    options: "errors=remount-ro"
    passno: 0
  - path: /boot
    options: "nodev,nosuid,noexec,noauto"
    state: present
```

For more information on variables please check the [ansible doc](https://docs.ansible.com/ansible/latest/collections/ansible/posix/mount_module.html).
