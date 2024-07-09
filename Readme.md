# unifi quick setup

automate provisioning for  [docker-unifi-network-application](https://github.com/linuxserver/docker-unifi-network-application)
using plain ssh with [taskfile](https://taskfile.dev/) as a convenient wrapper.

## Setup of a new instance

Adapt 
- `CLIENT_NAME`
- `CLIENT_DOMAIN`
in Taskfile.yaml with your client's address.

```bash
# create certificate and copy the id to the client for an uninterrupted provisioning later on
task ssh:setup

# test connection with a shell on the client
task ssh:client

# one time provisioning of folders and tools
task raspberry:provision

# deploy docker-compose.yaml and start service
task raspberry:deploy
```

After a config change simply rerun


```bash
task raspberry:deploy
```

## Remarks

- The DB credentials are hardcoded in docker-compose.yaml `MONGO_PASS`. This is considered bad practice. I might automated a randomized value here in future.
    >  For now make sure to change to password on your installation.