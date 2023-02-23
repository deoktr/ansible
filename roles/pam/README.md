# PAM

- Configure PAM
  - common-account
  - common-password
  - common-auth
  - common-session
  - login
  - sshd
  - su-l
  - su

## Variables

| name                         | type | default                | description                        |
| ---                          | ---  | ---                    | ---                                |
| `pam_good_password_template` | str  | `good-password.txt.j2` | Template for good password message |
