# oath

PAM oath setup.

## Generate QRcode

```bash
export SECRET=aaaa
export USER=user
export HOST=bastion
qrencode -t ansiutf8 <<< echo "otpauth://totp/$USER@$HOST?secret=$SECRET&period=30&digits=6&issuer=$HOST"
```

