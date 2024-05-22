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

| name                              | type      | default                               | description                                       |
| --------------------------------- | --------- | ------------------------------------- | ------------------------------------------------- |
| `pass_max_days`                   | int       | `30`                                  | password expiry in days (not configured here)     |
| `pam_sshd_faillock_deny`          | int       | `6`                                   | SSH faillock configuration: `deny`                |
| `pam_sshd_faillock_fail_interval` | int       | `900` (15 min)                        | SSH faillock configuration: `fail_interval`       |
| `pam_sshd_faillock_unlock_time`   | int       | `600` (10 min)                        | SSH faillock configuration: `unlock_time`         |
| `pam_faildelay_delay`             | int       | `3000000` (microseconds)              | faildelay configuration: `delay`                  |
| `pam_pwquality_minlen`            | int       | `16`                                  | password quality min length                       |
| `pam_pwquality_dcredit`           | int       | `-1`                                  | password quality                                  |
| `pam_pwquality_ucredit`           | int       | `-1`                                  | password quality                                  |
| `pam_pwquality_ocredit`           | int       | `-1`                                  | password quality                                  |
| `pam_pwquality_lcredit`           | int       | `-1`                                  | password quality                                  |
| `pam_pwquality_gecoscheck`        | int       | `1`                                   | password quality gecos check                      |
| `pam_pwquality_maxrepeat`         | int       | `3`                                   | password quality max character repeat             |
| `pam_pwquality_badwords`          | list[str] | _see [defaults](./defaults/main.yml)_ | list of words that can't be used inside passwords |
| `pam_pwhistory_remember`          | int       | `10`                                  | number of old password kept in history            |

-   [man pam_faillock](https://linux.die.net/man/8/pam_faillock)
-   [man pam_faildelay](https://linux.die.net/man/8/pam_faildelay)
-   [man pam_pwquality](https://linux.die.net/man/8/pam_pwquality)

## Commands

To unlock a user account use `passwd -u $USER`.
