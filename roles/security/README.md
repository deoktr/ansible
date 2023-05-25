# Security

Security measures to patch certain vulnerabilities when you can't always update the system.

## Mitigation

### CVE-2023-22809

Affecting sudo versions 1.8.0 through 1.9.12p1. https://www.synacktiv.com/sites/default/files/2023-01/sudo-CVE-2023-22809.pdf

Mitigation: put the following in sudo configuration.

```
Defaults!SUDOEDIT	env_delete+="SUDO_EDITOR VISUAL EDITOR"
```

## TODO

- Remove specific measures when they are not needed anymore.
