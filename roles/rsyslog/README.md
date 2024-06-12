# rsyslog

Configure rsyslog.

-   configure rsyslog
-   configure rsyslog to send to remote (optional with: rsyslog_server)

## Variables

| name                           | type      | default     | description    |
| ------------------------------ | --------- | ----------- | -------------- |
| `rsyslog_server_host`          | str       | -           |                |
| `rsyslog_server_port`          | int       | `514`       |                |
| `rsyslog_server_proto`         | str       | `tcp`       | `tcp` or `udp` |
| `rsyslog_enable_tcp_reception` | bool      | `false`     |                |
| `rsyslog_enable_udp_reception` | bool      | `false`     |                |
| `rsyslog_reception_from_ip`    | list[str] | _local_net_ |                |

# TODO

-   add a check when the rsyslog_server variable is not present so that the 00-remote file is removed if the variable is removed
-   add TLS support <https://rsyslog.readthedocs.io/en/latest/tutorials/tls.html>
