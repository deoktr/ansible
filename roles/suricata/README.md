# Suricata

- Install Suricata
- Configure Surcicata
- Add custom Suricata rules

## Problem

Currently if we run this role for the first time, surciata try to start and
then we reload it, this will cause suricata to fail with this message:
`suricata.service: Start request repeated too quickly.`.

To do `suricata-update` the server need to be connected to the internet (allow
out 443) to collect new rules.

## TODO

- Add configuration for GeoIP
- Check if Ansible trigger any suricata rules by mistake
