# Clean

Remove Ansible configuration backups, this can be useful to clean after test.

Warning: This feature is experimental, this could break things !

## Variables

| name          | type      | default                     | description                                  |
| ------------- | --------- | --------------------------- | -------------------------------------------- |
| `config_list` | list[str] | _see default/main.yml file_ | List of configuration file to delete backups |

## TODO

-   Remove the ansible_managed file header
