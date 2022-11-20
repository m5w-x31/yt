(2022.11.19)

# Docker Setup on Ubuntu 22.04

## ref.

- https://docs.docker.com/engine/install/ubuntu/
- https://zenn.dev/shimakaze_soft/articles/02aebaedeb43b6

---

## Environment

### Server

- Ubutntu 22.04 Server
  - user: m5w

### Client

- Visual Studio Code (macOS Ventura)
  - Remote SSH

---

(Remote SSH : m5w@u22)

## Install docker

### install packages

```
$ sudo apt-get update
$ sudo apt-get install ca-certificates curl gnupg lsb-release

$ sudo mkdir -p /etc/apt/keyrings
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
$ ls -l /etc/apt/keyrings/

$ echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
$ ls -l /etc/apt/sources.list.d/
$ cat /etc/apt/sources.list.d/docker.list

$ sudo apt-get update

$ sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

### check

```
$ docker --version
---
Docker version 20.10.21, build baeda1f
```

### add user on "docker" group

```
$ docker ps
---
Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get "http://%2Fvar%2Frun%2Fdocker.sock/v1.24/containers/json": dial unix /var/run/docker.sock: connect: permission denied
```

```
$ sudo usermod -a -G docker $USER

(re-login)

$ docker ps
---
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```

### docker hello-world

```
$ docker run hello-world
---
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
2db29710123e: Pull complete 
Digest: sha256:faa03e786c97f07ef34423fccceeec2398ec8a5759259f94d99078f264e9d7af
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```


### docker ubuntu

```
$ docker run -it ubuntu bash
---
Unable to find image 'ubuntu:latest' locally
latest: Pulling from library/ubuntu
e96e057aae67: Pull complete 
Digest: sha256:4b1d0c4a2d2aaf63b37111f34eb9fa89fa1bf53dd6e4ca954d47caebca4005c2
Status: Downloaded newer image for ubuntu:latest
```


## Install docker-compose

### download

- GitHub(releases): https://github.com/docker/compose/releases

```
$ sudo curl -SL https://github.com/docker/compose/releases/download/v2.12.2/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose
$ sudo chmod +x /usr/local/bin/docker-compose
```

### check

```
$ docker-compose --version
---
Docker Compose version v2.12.2
```

### docker-compose hello-world

```
$ vi docker-compose.yml
---
version: "3.9"
services:
  hello:
    image: hello-world:latest
```

```
$ docker-compose up
```

### docker-compse ubuntu

```
$ vi docker-compose.yml
---
version: "3.9"
services:
  ubuntu:
    image: ubuntu:latest
    tty: true
```

### delete container

```
$ docker container prune
```
