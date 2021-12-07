# 01docker

## Getting started
```
brew install lima
limactl start https://raw.githubusercontent.com/dictcp/01docker/master/01docker.yaml --tty=false
limactl stop 01docker && limactl start 01docker ## workaround on group membership refresh issue
docker context create 01docker --docker host="unix://$HOME/.lima/01docker/sock/docker.sock"
docker context use 01docker
docker run -it --rm dictcp/utils /bin/bash
```
