# aide

Configure aide.

## Variables

| name                | type      | default                      | description                           |
| ---                 | ---       | ---                          | ---                                   |
| `aide_remove_rules` | list[str] | *see defualts/main.yml file* | List of defualt aide rules do disable |

## Usage

Check aide with:

```bash
aide --check --config /etc/aide/aide.conf
```

## TODO

- add ability to put back previously disabled rules
