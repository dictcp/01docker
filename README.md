# 01docker

01docker is simple wrapper to setup Docker daemon on LIMA Debian VM, as a drop-in replacement for Docker for Mac.

## Getting started
```bash
brew install lima # or even docker (for docker-cli)
limactl start https://raw.githubusercontent.com/dictcp/01docker/master/01docker.yaml --tty=false
limactl stop 01docker && limactl start 01docker ## workaround on group membership refresh issue
docker context create 01docker --docker host="unix://$HOME/.lima/01docker/sock/docker.sock"
docker context use 01docker
docker run -it --rm dictcp/utils /bin/bash
```

## Daily use
```bash
limactl start 01docker
docker run -it --rm dictcp/utils /bin/bash
```

## Reference
- https://github.com/lima-vm/lima/tree/master/examples
- https://github.com/abiosoft/colima
