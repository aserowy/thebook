---
title: Update container automatically
authors:
  - Alexander Serowy
---

## Tasks

[ ] <https://github.com/containrrr/watchtower/issues/710>: integrate watchtower alerts with mqtt

## Watchtower

Extend the docker-compose.yaml with Watchtower.

> With watchtower you can update the running version of your containerized app simply by pushing a new image to the Docker Hub or your own image registry. Watchtower will pull down your new image, gracefully shut down your existing container and restart it with the same options that were used when it was deployed initially.

```yaml
watchtower:
  image: containrrr/watchtower:latest
  container_name: watchtower
  restart: always
  volumes:
    - /var/run/docker.sock:/var/run/docker.sock
```
