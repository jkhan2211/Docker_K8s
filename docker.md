## Containers with Docker Intro

### Containers with Docker
- Docker: founded in 2013
- Shared Kernel: The container runtime makes a used of shared Linux kernel between container
- Uses Namespaces and Cgroups: Utilises Linux kernel technologies, to provide isolated environments with their own users, hostnames, IP Address, mount points and resource allocation
- Simplicity: The success of Docker can be attributed to the ease of use for adoption. Docker brought containerisation with simple CLI


What is a Container Image? 
- Portable: Self contained bundle of software and dependencies 
- Versatile: Allowing use to run Software consistently across Compute environments

Container Image - bundle of software (nginx)
Container - instances of container image (bunch of nginx container image)

Container Image Tags:
Labels: Used to distinguish version of a Container Images
Flexible: You can use tags to satisfy your container image requirements

Container image is a stack of container layers
[Writable layer]
{layer 2}
{layer 1}
{layer 0}


### Running Containers

##### Container Networking and Volumes

```
-P, --publish-all
publish all exposed ports to random ports
```

##### Building Container Image - Part 01
```
vim Dockerfile


## Dockerfile
FROM alpine

LABEL org.opencontainers.image.authors="Junaid Khan"
```

Command:
```
docker pull alpine
sudo docker run --rm -it jkhandockerlab420/cmatrix
```

```
   0 hostname
   1 git clone https://github.com/spurin/cmatrix.git
   2 apk add git
   3 git clone https://github.com/spurin/cmatrix.git
   4 history
```

Current Dockerfile:
```
FROM alpine

LABEL org.opencontainers.image.authors="Junaid Khan"
LABEL org.opencontainers.image.description="Container image"

WORKDIR cmatrix

RUN apk update
RUN apk add git
RUN git clone https://github.com/spurin/cmatrix.git .
# RUN cd cmatrix/

RUN apk add autoconf
RUN apk add automake
RUN autoreconf -i

RUN apk add alpine-sdk
RUN apk add ncurses-dev ncurses-static
RUN mkdir -p /usr/lib/kbd/consolefonts /usr/share/consolefonts
RUN ./configure LDFLAGS="-static"
RUN make

CMD ["./cmatrix"]
```

##### Building Container Image - Part 02

##### Building Container Image - Part 03


### Containers Runtime


