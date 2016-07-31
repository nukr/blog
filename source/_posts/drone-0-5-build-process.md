title: drone-0.5-build-process
date: 2016-07-30 12:45:32
tags: [ci, drone]
---

# Drone 0.5 build process

All process build on ubuntu 16.04 and fish-shell

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

put .drone.yml to your repo root

## client

```bash
# docker login
begin
  set -lx DRONE_TOKEN <your-token-copy-from-gui>
  set -lx DRONE_SERVER http://<your-drone-domain-or-ip>
  drone secret add --image=docker account/repo DOCKER_REGISTRY asia.gcr.io
end

begin
  set -lx DRONE_TOKEN <your-token-copy-from-gui>
  set -lx DRONE_SERVER http://<your-drone-domain-or-ip>
  drone secret add --image=docker account/repo DOCKER_USERNAME _json_key
end

begin
  set -lx DRONE_TOKEN <your-token-copy-from-gui>
  set -lx DRONE_SERVER http://<your-drone-domain-or-ip>
  set -lx PASSWORD "(cat credential.json)"
  drone secret add --image=docker account/repo DOCKER_PASSWORD $PASSWORD
end

# no need to set other secret normally
begin
  set -lx DRONE_TOKEN <your-token-copy-from-gui>
  set -lx DRONE_SERVER http://<your-drone-domain-or-ip>
  drone secret add --image=<image-your-want-limit> account/repo KEY VALUE
end

# sign in your repo root
begin
  set -lx DRONE_TOKEN <your-token-copy-from-gui>
  set -lx DRONE_SERVER http://<your-drone-domain-or-ip>
  drone sign account/repo
end
```
