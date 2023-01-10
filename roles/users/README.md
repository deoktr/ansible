# Users

## Variables

- `pass_min_days` minimum days between password changes, default: 1
- `pass_warn_age` password expiry warning, default: 7
- `shell_timeout` shell timeout in seconds, default: 900
- `user` list of user objects, example:

```
  - name: jeff
    uid: 1003
    authorized_keys: ...
```
