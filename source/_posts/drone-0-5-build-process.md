title: drone-0.5-build-process
date: 2016-07-30 12:45:32
tags: [ci, drone]
---

# Drone 0.5 build process

All process build on ubuntu 16.04 and
[fish-shell](https://fishshell.com/)

## server

```bash
curl -sSL https://get.docker.com/ | sh

docker run \
  --env DRONE_GITHUB=true \
  --env DRONE_GITHUB_CLIENT=<your-github-client-id> \
  --env DRONE_GITHUB_SECRET=<your-github-client-secret> \
  --env DRONE_SECRET=<your-secret-that-nobody-know> \
  --env DRONE_OPEN=true \
  --env DRONE_ADMIN=nukr \
  --env DRONE_DEBUG=true \
  --volume /var/lib/drone:/var/lib/drone \
  --restart=always \
  --publish=80:8000 \
  --detach=true \
  --name=drone \
  drone/drone:0.5
```

## agent

```bash
docker run \
  --env DRONE_SERVER=http://<your-server-domain-or-ip> \
  --env DRONE_SECRET=<your-secret-that-nobody-know-as-you-set-before> \
  --volume /var/run/docker.sock:/var/run/docker.sock \
  --restart=always \
  --detach=true \
  --name=drone-agent \
  drone/drone:0.5 agent
```

## project

.drone.yml

```yml
pipeline:
  test:
    image: node:6.3.1
    commands:
      - echo hihi
  docker:
    repo: project/repo
    tag:
      - latest
      - ${DRONE_TAG##v}
    when:
      event: tag
```

put .drone.yml to your repo root then sign

```bash
drone sign account/repo
# create .drone.yml.sig
```

## client

```bash
# drone secret add --image=<image-your-want-limit> account/repo KEY VALUE

# docker login
set -x DRONE_TOKEN <your-token-copy-from-gui>
set -x DRONE_SERVER http://<your-drone-domain-or-ip>
drone secret add --image=docker account/repo DOCKER_REGISTRY asia.gcr.io
drone secret add --image=docker account/repo DOCKER_USERNAME _json_key

set -lx PASSWORD (cat credential.json)
drone secret add --image=docker account/repo DOCKER_PASSWORD "$PASSWORD"

```
