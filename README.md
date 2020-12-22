docker avahi
============

[![](https://images.microbadger.com/badges/image/rittme/avahi.svg)](http://microbadger.com/images/rittme/avahi "Image badge") [![](https://images.microbadger.com/badges/commit/rittme/avahi.svg)](https://microbadger.com/images/rittme/avahi "Commit badge")

# Quickstart

## Get initialize configuration:

```bash
docker create --name avahi-config rittme/avahi:latest
docker cp avahi-config:/etc/avahi .
docker rm avahi-config
```

### Disable DBus for starting the container
Edit your `avahi-daemon.conf` and set the following line.

```bash
enable-dbus=no
```
# Start the container 

```bash
docker run -d --net=host -v $(pwd)/avahi:/etc/avahi rittme/avahi:latest
```

# Docker compose
```yml
  avahi:
    container_name: avahi
    image: rittme/avahi:latest
    network_mode: host
    volumes:
      - ./avahi:/etc/avahi:ro
    restart: unless-stopped
```
## Build the image

```bash
docker build --build-arg AVAHI_VERSION=$(cat VERSION) -t rittme/avahi:$(cat VERSION) .
```

## Issues

If you have any issues feel free to create an [issue on GitHub](https://github.com/rittme/docker-avahi/issues)


# Credits
This repository is a fork from [solidnerd/docker-avahi](https://github.com/solidnerd/docker-avahi)
