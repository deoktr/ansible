# Fail2ban

Fail2ban setup.

## Variables

| name                            | type       | default                                                                   | description |
| ---                             | ---        | ---                                                                       | ---         |
| `fail2ban_loglevel`             | str        | `INFO`                                                                    |             |
| `fail2ban_logtarget`            | str        | `SYSLOG`                                                                  |             |
| `fail2ban_syslogsocket`         | str        | `auto`                                                                    |             |
| `fail2ban_socket`               | str        | `/var/run/fail2ban/fail2ban.sock`                                         |             |
| `fail2ban_pidfile`              | str        | `/var/run/fail2ban/fail2ban.pid`                                          |             |
| `fail2ban_dbfile`               | str        | `/var/lib/fail2ban/fail2ban.sqlite3`                                      |             |
| `fail2ban_dbpurgeage`           | str        | `1d`                                                                      |             |
| `fail2ban_dbmaxmatches`         | int        | `10`                                                                      |             |
| `fail2ban_bantime_factor`       | int        | `1`                                                                       |             |
| `fail2ban_bantime_rndtime`      | int        | `64`                                                                      |             |
| `fail2ban_bantime_formula`      | str        | `ban.Time * math.exp(float(ban.Count+1)*banFactor)/math.exp(1*banFactor)` |             |
| `fail2ban_bantime_overalljails` | bool       | `false`                                                                   |             |
| `fail2ban_ignoreips`            | list[str]  | `[127.0.0.1/8, ::1]`                                                      |             |
| `fail2ban_bantime`              | str        | `10m`                                                                     |             |
| `fail2ban_findtime`             | str        | `10m`                                                                     |             |
| `fail2ban_maxretry`             | int        | `5`                                                                       |             |
| `fail2ban_backend`              | str        | `auto`                                                                    |             |
| `fail2ban_action`               | str        | `%(action_)s`                                                             |             |
| `fail2ban_services`             | list[dict] |                                                                           |             |

## Usage

```bash
fail2ban-client status sshd
```

```bash
fail2ban-client set sshd unbanip 10.0.1.9
```

## Links

- https://github.com/nbigot/ansible-fail2ban

## TODO

- Ensure logs are sent to syslog
- Use variable for jails
