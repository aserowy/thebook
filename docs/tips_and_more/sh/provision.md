---
title: Provision Raspbian with Home Assistant
authors:
  - Alexander Serowy
---

## Install raspbian

## Install docker

## Install docker-compose

## Setup container

### Home Assistant

```yaml
home-assistant:
  image: homeassistant/home-assistant:stable
  container_name: home-assistant
  restart: always
  depends_on:
    - zigbee2mqtt
  network_mode: "host"
  devices:
    - /dev/serial/by-id/usb-EnOcean_GmbH_EnOcean_USB_300_DC_FT50B8B0-if00-port0:/dev/serial/by-id/usb-EnOcean_GmbH_EnOcean_USB_300_DC_FT50B8B0-if00-port0
  volumes:
    - ~/docker/home-assistant:/config
    - /etc/localtime:/etc/localtime:ro
```

### Mosquitto

```yaml
mosquitto:
  image: eclipse-mosquitto:latest
  container_name: mosquitto
  restart: always
  ports:
    - "1883:1883"
    - "9001:9001"
  volumes:
    - ~/docker/mosquitto/config:/mosquitto/config
    - ~/docker/mosquitto/data:/mosquitto/data
    - ~/docker/mosquitto/log:/mosquitto/log
```

### Zigbee2mqtt

```yaml
zigbee2mqtt:
  image: koenkk/zigbee2mqtt:latest
  container_name: zigbee2mqtt
  restart: always
  depends_on:
    - mosquitto
  volumes:
    - ~/docker/zigbee2mqtt:/app/data
    - /run/udev:/run/udev:ro
  devices:
    - /dev/ttyAMA0:/dev/ttyAMA0
  restart: always
  environment:
    - TZ=Europe/Berlin
```
