# Suricata

-   Install Suricata
-   Configure Surcicata
-   Add custom Suricata rules

## Variables

| name                           | type             | default                      |
| ------------------------------ | ---------------- | ---------------------------- |
| `ssh_port`                     | int              | _ansible_port or 22_         |
| `suricata_user`                | str              | `root`                       |
| `suricata_group`               | str              | `root`                       |
| `suricata_home_net`            | str or list[str] | _local_net_                  |
| `suricata_external_net`        | str              | `!$HOME_NET`                 |
| `suricata_http_servers`        | str              | `$HOME_NET`                  |
| `suricata_smtp_servers`        | str              | `$HOME_NET`                  |
| `suricata_sql_servers`         | str              | `$HOME_NET`                  |
| `suricata_dns_servers`         | str              | `$HOME_NET`                  |
| `suricata_telnet_servers`      | str              | `$HOME_NET`                  |
| `suricata_aim_servers`         | str              | `$EXTERNAL_NET`              |
| `suricata_dc_servers`          | str              | `$HOME_NET`                  |
| `suricata_dnp3_server`         | str              | `$HOME_NET`                  |
| `suricata_dnp3_client`         | str              | `$HOME_NET`                  |
| `suricata_modbus_client`       | str              | `$HOME_NET`                  |
| `suricata_modbus_server`       | str              | `$HOME_NET`                  |
| `suricata_enip_client`         | str              | `$HOME_NET`                  |
| `suricata_enip_server`         | str              | `$HOME_NET`                  |
| `suricata_http_ports`          | str              | `80`                         |
| `suricata_shellcode_ports`     | str              | `!80`                        |
| `suricata_oracle_ports`        | str              | `1521`                       |
| `suricata_ssh_ports`           | str              | `22`                         |
| `suricata_dnp3_ports`          | str              | `20000`                      |
| `suricata_modbus_ports`        | str              | `502`                        |
| `suricata_file_data_ports`     | str              | `[$HTTP_PORTS,110,143]`      |
| `suricata_ftp_ports`           | str              | `21`                         |
| `suricata_geneve_ports`        | str              | `6081`                       |
| `suricata_vxlan_ports`         | str              | `4789`                       |
| `suricata_teredo_ports`        | str              | `3544`                       |
| `suricata_eve_log_filetype`    | str              | `regular`                    |
| `suricata_default_interface`   | str              | `eth0`                       |
| `suricata_af_packet_interface` | str              | _suricata_default_interface_ |
| `suricata_pcap_interface`      | str              | _suricata_default_interface_ |
| `suricata_netmap_interface`    | str              | _suricata_default_interface_ |
| `suricata_pfring_interface`    | str              | _suricata_default_interface_ |
| `suricata_rfb_enabled`         | str              | `yes`                        |
| `suricata_mqtt_enabled`        | str              | `no`                         |
| `suricata_krb5_enabled`        | str              | `yes`                        |
| `suricata_snmp_enabled`        | str              | `yes`                        |
| `suricata_ikev2_enabled`       | str              | `yes`                        |
| `suricata_tls_enabled`         | str              | `yes`                        |
| `suricata_dcerpc_enabled`      | str              | `yes`                        |
| `suricata_ftp_enabled`         | str              | `yes`                        |
| `suricata_rdp_enabled`         | str              | `yes`                        |
| `suricata_ssh_enabled`         | str              | `yes`                        |
| `suricata_http2_enabled`       | str              | `yes`                        |
| `suricata_smtp_enabled`        | str              | `yes`                        |
| `suricata_imap_enabled`        | str              | `detection-only`             |
| `suricata_smb_enabled`         | str              | `yes`                        |
| `suricata_nfs_enabled`         | str              | `yes`                        |
| `suricata_tftp_enabled`        | str              | `yes`                        |
| `suricata_dns_tcp_enabled`     | str              | `yes`                        |
| `suricata_dns_udp_enabled`     | str              | `yes`                        |
| `suricata_http_enabled`        | str              | `yes`                        |
| `suricata_modbus_enabled`      | str              | `no`                         |
| `suricata_dnp3_enabled`        | str              | `no`                         |
| `suricata_enip_enabled`        | str              | `no`                         |
| `suricata_ntp_enabled`         | str              | `yes`                        |
| `suricata_dhcp_enabled`        | str              | `yes`                        |
| `suricata_sip_enabled`         | str              | `no`                         |

## Problem

Currently if we run this role for the first time, surciata try to start and then we reload it, this will cause suricata to fail with this message: `suricata.service: Start request repeated too quickly.`.

To do `suricata-update` the server need to be connected to the internet (allow out 443) to collect new rules.

## TODO

-   Add configuration for GeoIP
-   Check if Ansible trigger any Suricata rules by mistake
