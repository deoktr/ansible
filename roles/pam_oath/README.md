# oath

PAM oath setup.

## Generate QRcode

```bash
export SECRET=aaaa
export USER=user
export HOST=bastion
qrencode -t ansiutf8 <<< echo "otpauth://totp/$USER@$HOST?secret=$SECRET&period=30&digits=6&issuer=$HOST"
```

## Links

-   https://www.nongnu.org/oath-toolkit/pam_oath.html
-   https://linux.die.net/man/8/pam_access
-   https://packages.debian.org/source/sid/oath-toolkit
-   https://wiki.archlinux.org/title/Pam_oath
-   https://spod.cx/blog/two-factor-ssh-auth-with-pam_oath-google-authenticator.shtml
