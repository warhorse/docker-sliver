# [warhorse/sliver](https://github.com/war-horse/docker-sliver)
[![GitHub Release](https://img.shields.io/github/release/war-horse/docker-sliver.svg?style=flat-square&color=E68523)](https://github.com/war-horse/docker-sliver/releases)
[![MicroBadger Layers](https://img.shields.io/microbadger/layers/warhorse/sliver.svg?style=flat-square&color=E68523)](https://microbadger.com/images/warhorse/sliver "Get your own version badge on microbadger.com")
[![MicroBadger Size](https://img.shields.io/microbadger/image-size/warhorse/sliver.svg?style=flat-square&color=E68523)](https://microbadger.com/images/warhorse/sliver "Get your own version badge on microbadger.com")
[![Docker Pulls](https://img.shields.io/docker/pulls/warhorse/sliver.svg?style=flat-square&color=E68523)](https://hub.docker.com/r/warhorse/sliver)
[![Docker Stars](https://img.shields.io/docker/stars/warhorse/sliver.svg?style=flat-square&color=E68523)](https://hub.docker.com/r/warhorse/sliver)

[sliver](https://github.com/BishopFox/sliver) - Sliver is an open source, cross-platform adversary simulation/red team platform, it can be used by organizations of all sizes to perform security testing. Sliver's implants support C2 over Mutual TLS (mTLS), WireGuard, HTTP(S), and DNS. Implants are dynamically compiled with unique X.509 certificates signed by a per-instance certificate authority generated when you first run the binary.


![sliver]()

## Usage

Here are some example snippets to help you get started creating a container.

### docker

```
docker create \
  --name=sliver \
  -e TZ=Europe/London \
  -p 443:443 \
  -p 80:80 \
  -p 31337:31337 \
  --restart unless-stopped \
  warhorse/sliver
```

### docker-compose

Compatible with docker-compose v2 schemas.

```
---
version: "2"
services:
  sliver:
    image: warhorse/sliver
    container_name: sliver
    environment:
      - TZ=Europe/London
    volumes:
      - <path to data>:/config
      - <path to data>:/phishlets
    ports:
      - 443:443
      - 80:80
    restart: unless-stopped
```

## Parameters

Container images are configured using parameters passed at runtime (such as those above). These parameters are separated by a colon and indicate `<external>:<internal>` respectively. For example, `-p 8080:80` would expose port `80` from inside the container to be accessible from the host's IP on port `8080` outside the container.

| Parameter | Function |
| :----: | --- |
| `-p 80` | The port for HTTP traffic |
| `-p 443` | The port for HTTPS traffic |
| `-e TZ=Europe/London` | Specify a timezone to use EG Europe/London|
| `-v /config` | sliver configs |
| `-v /phishlets` | sliver phishlets |

&nbsp;
## Application Setup

Access the webui at `<your-ip>:7443`, for more information check out [sliver](https://github.com/BishopFox/sliver).



## Support Info

* Shell access whilst the container is running: `docker exec -it sliver /bin/bash`
* To monitor the logs of the container in realtime: `docker logs -f sliver`

## Building locally

If you want to make local modifications to these images for development purposes or just to customize the logic:
```
git clone https://github.com/warhorse/docker-sliver.git
cd docker-sliver
docker build \
  --no-cache \
  --pull \
  -t warhorse/sliver:latest .
```
## Versions

* **04.19.21:** - First Push