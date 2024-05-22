# apt-cacher-ng

## Variables

| name                                 | type                 | default                               | description                                 |
| ------------------------------------ | -------------------- | ------------------------------------- | ------------------------------------------- |
| `apt_cacher_ng_port`                 | int                  | `3142`                                | Port for apt-cacher-ng                      |
| `apt_cacher_ng_from_ip`              | list[str]            | _local_net_                           | List of IP that should access the apt proxy |
| `apt_cacher_ng_cache_dir`            | str                  | `/var/cache/apt-cacher-ng`            | CacheDir                                    |
| `apt_cacher_ng_log_dir`              | str                  | `/var/log/apt-cacher-ng`              | LogDir                                      |
| `apt_cacher_ng_support_dir`          | str                  | `/usr/lib/apt-cacher-ng`              | SupportDir                                  |
| `apt_cacher_ng_report_page`          | str                  | `acng-report.html`                    | ReportPage                                  |
| `apt_cacher_ng_network_timeout`      | int                  | `40`                                  | NetworkTimeout                              |
| `apt_cacher_ng_pass_through_pattern` | str                  | _see [defaults](./defaults/main.yml)_ | PassThroughPattern                          |
| `apt_cacher_ng_local_dirs`           | list[str] (optional) | -                                     | LocalDirs                                   |
| `apt_cacher_ng_proxy`                | list[str] (optional) | -                                     | Proxy                                       |
| `apt_cacher_ng_bind_address`         | list[str] (optional) | -                                     | BindAddress                                 |

## TODO

-   var to add athentication with AdminAuth
-   var MaxDlSpeed
