# Shared handlers

## Handlers

The `Reboot` handler allow us to reboot systems. It's separated into 2 separate
tasks, the first to reboot all hosts except the bastion, and the last one to
reboot the bastion. This is done because (obviously) if we reboot the bastion
while we reboot all other machine this would break the ssh proxy jump.
