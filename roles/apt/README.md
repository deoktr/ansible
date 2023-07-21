# apt

Either allow apt from the internet or setup a proxy to get packages.

To use the apt proxy server, 2 variables must be set: `use_apt_proxy` must be set to `true` and `apt_proxy_addr` must be set.

## Variables

| name             | type      | default | description |
| ---------------- | --------- | ------- | ----------- |
| `use_apt_proxy`  | bool      | `false` |             |
| `apt_proxy_list` | list[str] | []      |             |

## TODO

-   configure sources.list
-   configure sources.list to use tor only: https://wiki.debian.org/SourcesList#Using_Tor_with_Apt
