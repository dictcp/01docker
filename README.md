# 01docker

01docker is simple wrapper to setup Docker daemon on LIMA Debian VM, as a drop-in replacement for Docker for Mac.
The Docker socket is exposed via SSH forwarding.

## Getting started
```bash
## Install package
brew install lima 
## or brew install docker (for docker-cli, if Docker for mac is not installed)

# Setup VM
limactl start https://raw.githubusercontent.com/dictcp/01docker/master/01docker.yaml --tty=false
limactl stop 01docker && limactl start 01docker ## workaround on group membership refresh issue

# Setup Docker to use the VM, via socket
docker context create 01docker --docker host="unix://$HOME/.lima/01docker/sock/docker.sock"
docker context use 01docker

# Enjoy
docker run -it --rm dictcp/utils /bin/bash
```

## Daily use
```bash
# remember to start the VM first, or you will get error
limactl start 01docker

# Enjoy in your daily work
docker run -it --rm dictcp/utils /bin/bash

# Want to switch back to Docker for Mac?
docker context use desktop-linux
limactl stop 01docker
```

## Known issue
- `/Users` is mounted as read-only
- Extra VM restart is required for the first launch
- no GUI (yet)

## Reference
- https://github.com/lima-vm/lima/tree/master/examples
- https://github.com/abiosoft/colima
