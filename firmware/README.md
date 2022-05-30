# Firmware

## Pre-requisites

install [docker](https://docs.docker.com/get-docker/)

and `docker-compose`

```bash
python3 -m pip install docker-compose
```

## Setup

```
git submodule update --init
git -C micropython-microbit-v2 submodule update --init
```

## Compile

```
make
```

## Flash

1. Plug in microbit (USB)
1. Mount microbit as mass storage device (like a USB stick)
1. Copy `MICROBIT.hex` to the microbit.