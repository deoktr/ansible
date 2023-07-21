# aide

Configure aide.

## Variables

| name                | type      | default                     | description                           |
| ------------------- | --------- | --------------------------- | ------------------------------------- |
| `aide_remove_rules` | list[str] | _see default/main.yml file_ | List of default aide rules do disable |

## Usage

Check aide with:

```bash
aide --config /etc/aide/aide.conf --check
```

## TODO

-   Add ability to put back previously disabled rules
