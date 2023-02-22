# chrony

NTP client setup.

## Variables

| name                        | type      | default                   | description |
| ---                         | ---       | ---                       | ---         |
| `ntp_pools`                 | list[str] | `[2.debian.pool.ntp.org]` |             |
| `ntp_servers`               | list[str] | -                         |             |
| `chrony_as_server_networks` | str       | -                         |             |
