# Bastion

Configure SSH server to accept proxy jump. The bastion SSH interface should be on another port, example 2222 and should be only accessible from and administration network on a specific interface. Not to be confused with the bastion's SSH server which should be on port 22.

-   Configure SSH to allow tunneling
-   Configure UFW to allow tunneling to specified hosts

## Variables

| name                      | type      | default       | description |
| ------------------------- | --------- | ------------- | ----------- |
| `bastion_to_port`         | int       | `22`          |             |
| `bastion_to_ip`           | list[str] | **local_net** |             |
| `bastion_jump_users`      | list[str] | -             |             |
| `bastion_jump_group_gid`  | int       | -             |             |
| `bastion_jump_group_name` | str       | `sshjump`     |             |

## How to

1. Create a user for the bastion with an `authorized_keys`, `generate_ssh_key` set to true and `shell` set to `/bin/false`

```yaml
- name: bob
  generate_ssh_key: true
  authorized_keys: ssh-ed25519 user_key...
  shell: /bin/false
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

You can add `command='/bin/false'` at the beginning of each lines to be
absolutely sure that no user will be able to get a shell on the server.

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

## Links

-   https://engineering.fb.com/2016/09/12/security/scalable-and-secure-access-with-ssh/
-   https://www.syloe.com/rebonds-ssh/
-   https://serverfault.com/questions/1012205/how-to-properly-make-an-ssh-bastion-with-fail2ban-in-a-docker-container#1032094
-   https://stackoverflow.com/questions/41553511/can-ansible-deploy-docker-containers-remotely#41553682
-   https://www.golinuxcloud.com/ssh-proxy/

## TODO

-   Maybe change variables to be a dict containing IP and port so we can specify different ports for each servers
-   Start the SSH jump server on a docker container
-   Lock users in a chroot of their homes on the bastion server
-   Restrict users to only use SSH while connected
-   Generate unique certificates for each connections to remote servers
-   Setup RevokedKeys https://man.openbsd.org/OpenBSD-current/man5/sshd_config.5#RevokedKeys
