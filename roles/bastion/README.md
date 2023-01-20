# Bastion

Configure SSH server to accept tunneling.

- Configure SSH to allow tunneling
- Configure UFW to allow tunneling to specified hosts

## Varialbes

- `bastion_to_port` port that are allowed to be tunneling, default: `22`
- `bastion_to_ip` a list of IP or IP ranges thtat will be allowed to be tunneling, default: `local_net`

## How to

1. Create a user for the bastion with an `authorized_keys` and `generate_ssh_key` set to true

```yaml
  - name: bob
    generate_ssh_key: true
    authorized_keys: ssh-ed25519 user_key...
```

2. Create users on the bastion with the users role
3. Download the bastion user's pub key with the bastion role
4. Create a user for internal servers with an `authorized_keys` containing both the user's pub key and the bastion pub key, example:

```yaml
  - name: bob
    authorized_keys: |
      {{ lookup('file', 'credentials/bastion/ssh_pub_keys/bob') }}
      ssh-ed25519 user_key...
```

5. Set other users authorized_keys with the users role
6. Autorize users to connect to SSH by adding them to the `sshd_users` group and running the sshd role

```yaml
sshd_users:
  - bob
```

7. Add the `ssh_from_ip` with has value the local net bastion's IP and run the sshd role to update the firewall
8. Try connecting in SSH to the internal server, example:

```
ssh -J bob@bastion bob@internal
```

## TODO

- Make it dependant of sshd, ufw and users role
- Configure fail2ban
- Maybe change variables to be a dict containing IP and port so we can specify different ports for each servers
