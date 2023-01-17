# SSH forward

Configure SSH server to accept forwarding.

- Configure SSH to allow TCP forwarding
- Configure UFW to allow forwarding to specified hosts

## Varialbes

- `ssh_fwd_port` port that are allowed to be forwarded, default: 22
- `ssh_fwd_ip` a list of IP or IP ranges thtat will be allowed to be forwarded, default: 192.168.0.0/16
