# aide

Configure aide.

## Variables

| name                | type      | default                      | description                           |
| ---                 | ---       | ---                          | ---                                   |
| `aide_remove_rules` | list[str] | *see default/main.yml file* | List of default aide rules do disable |

## Usage

Check aide with:

```bash
aide --config /etc/aide/aide.conf --check
```

## TODO

- add ability to put back previously disabled rules
