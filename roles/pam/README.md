# PAM

Configure PAM:

-   common-account
-   common-password
-   common-auth
-   common-session
-   login
-   sshd
-   su-l
-   su

## Variables

| name                         | type      | default                | description                                       |
| ---------------------------- | --------- | ---------------------- | ------------------------------------------------- |
| `pam_faillock_deny`          | int       | `4`                    | faillock configuration: `deny`                    |
| `pam_faillock_fail_interval` | int       | `900`                  | faillock configuration: `fail_interval`           |
| `pam_faillock_unlock_time`   | int       | `600`                  | faillock configuration: `unlock_time`             |
| `pam_pwquality_minlen`       | int       | `16`                   | password quality min length                       |
| `pam_pwquality_dcredit`      | int       | `-1`                   | password quality                                  |
| `pam_pwquality_ucredit`      | int       | `-1`                   | password quality                                  |
| `pam_pwquality_ocredit`      | int       | `-1`                   | password quality                                  |
| `pam_pwquality_lcredit`      | int       | `-1`                   | password quality                                  |
| `pam_pwquality_gecoscheck`   | int       | `1`                    | password quality gecos check                      |
| `pam_pwquality_maxrepeat`    | int       | `3`                    | password quality max character repeat             |
| `pam_pwquality_badwords`     | list[str] | _see default/main.yml_ | list of words that can't be used inside passwords |

## Commands

To unlock a user account use `passwd -u $USER`.

## TODO

-   Make pwquality configuration editable
