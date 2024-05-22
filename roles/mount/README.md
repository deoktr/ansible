# mount

Manage partition mount options.

## Variables

| name                   | type                   | default                               | description                    |
| ---------------------- | ---------------------- | ------------------------------------- | ------------------------------ |
| `mount_state_default`  | str                    | `present`                             | Default value for state        |
| `mount_passno_default` | int                    | `2`                                   | Default valut for passno       |
| `mounts`               | list[dict] (see below) | _see [defaults](./defaults/main.yml)_ | List of partition with options |

For each partition _mounts_:

| name      | type           | default                | description    |
| --------- | -------------- | ---------------------- | -------------- |
| `path`    | str            | -                      | Partition path |
| `options` | str            | -                      | Options        |
| `state`   | str (optional) | _mount_state_default_  |                |
| `passno`  | int (optional) | _mount_passno_default_ |                |

Example:

```yaml
mounts:
    - path: /
      options: "errors=remount-ro"
      passno: 0
    - path: /boot
      options: "nodev,nosuid,noexec,noauto"
      state: present
```

For more information on variables please check the [ansible doc](https://docs.ansible.com/ansible/latest/collections/ansible/posix/mount_module.html).
