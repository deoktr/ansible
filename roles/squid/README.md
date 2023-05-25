# Squid

Install and configure Squid proxy server.

## Variables

| name                     | type      | default | description |
| ---                      | ---       | ---     | ---         |
| `squid_http_port`        | int       | `3128`  |             |
| `squid_allow_localnet`   | bool      | `true`  |             |
| `squid_domain_blacklist` | list[str] | -       |             |
| `squid_domain_whitelist` | list[str] | -       |             |

## Clients

Clients must be configured to connect to the proxy ip and port on their local
firewall. Example:

```bash
ufw allow out to 10.0.2.6 port 3128 proto tcp comment 'http proxy'
```

`10.0.2.6` being the IP of the squid server.

## Usage

With curl:

```bash
curl -v -x http://10.0.2.6:3128 http://www.google.com/
```

With pip:

```bash
pip --proxy http://10.0.2.6:3128 install package
```

## Links

- https://www.digitalocean.com/community/tutorials/how-to-set-up-squid-proxy-on-ubuntu-20-04

## TODO

- Better ACL
- Add password authentication
- Configure to use syslog
