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

| name                         | type | default                | description                             |
| ---                          | ---  | ---                    | ---                                     |
| `pam_good_password_template` | str  | `good-password.txt.j2` | Template for good password message      |
| `pam_faillock_deny`          | int  | `4`                    | faillock configuration: `deny`          |
| `pam_faillock_fail_interval` | int  | `900`                  | faillock configuration: `fail_interval` |
| `pam_faillock_unlock_time`   | int  | `600`                  | faillock configuration: `unlock_time`   |

## TODO

- Make pwquality config editable
