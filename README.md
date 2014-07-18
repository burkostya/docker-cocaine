# Contents
- [Introduction](#introduction)
    - [Version](#version)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Configuration](#configuration)
    - [Data Store](#data-store)

# Introduction
Dockerfile to build image with cocaine.

For now this image is just experiment

## Version
Current Version: 0.11.2.5

# Installation

Pull the latest or specific version of the image from the docker index.
This is the recommended method of installation as it is easier to update image
in the future.
These builds are performed by the **Docker Trusted Build** service.

```bash
docker pull burkostya/cocaine:0.11.2.5
```

Alternately you can build the image yourself.

```bash
git clone https://github.com/burkostya/docker-cocaine.git
cd docker-cocaine
docker build -t '<user>/cocaine' .
```

# Quick Start
Run container

```bash
docker run --name cocaine -it --rm \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -e "ELLIPTICS_HOSTNAME=${ELLIPTICS_HOSTNAME}" \
  --net host \
  burkostya/cocaine:0.11.2.5
```

- mounting of docker socket is needed if you plan using docker
for isolation of applications
- `ELLIPTICS_HOSTNAME` must be provided
- `--net host` binds container network to host.
Problem is that cocaine randomly expose ports for services
so we do not know which port to bind to host until container is running

# Configuration

## Data Store

Only elliptics storage available
You must provide environment variable `ELLIPTICS_HOSTNAME`
