# apt

Either allow apt from the internet or setup a proxy to get packages.

To use the apt proxy server, 2 variables must be set: `use_apt_proxy` must be
set to `true` and `apt_proxy_addr` must be set.

## Variables

- `use_apt_proxy` whether to use the apt proxy or not, default: `true`
- `apt_proxy_addr` IP or FQDN, example: `192.168.1.242`
- `apt_proxy_port` default: `3142`
