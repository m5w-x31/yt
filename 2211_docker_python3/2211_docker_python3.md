(2022.11.21)

# Docker Python3 Environment Setup

## ref.

- https://qiita.com/jhorikawa_err/items/fb9c03c0982c29c5b6d5

---

## Environment

### Server

- Ubutntu 22.04 Server
  - user: m5w

### Software

- Docker version 20.10.21
- Docker Compose version v2.12.2

---

## Directory structure

```
docker_python3/
- docker-compose.yml
- Dockerfile
- src/
  - hello.py
```

(Remote SSH : m5w@u22)

## Edit files

### docker-compose.yml

```
version: '3.9'
services:
  python3:
    container_name: python3
    build: .
    tty: true
    volumes:
      - ./src:/src
```

### Dockerfile

```
FROM python:3

RUN apt-get update
RUN pip install --upgrade pip
RUN pip install --upgrade setuptools
```

### src/hello.py

```
#!/usr/bin/env python

def main():
  print('Hello, World!')

if __name__ == '__main__':
  main()
```

## docker build/run

```
$ docker-compose build
$ docker-compose up -d
```

```
$ docker ps
---
CONTAINER ID   IMAGE                    COMMAND     CREATED          STATUS          PORTS     NAMES
6fc0d590b837   docker_python3-python3   "python3"   15 seconds ago   Up 10 seconds             python3
```

```
$ docker exec python3 python --version
---
Python 3.11.0
```

## hello world

```
$ docker exec python3 python /src/hello.py
```

```
$ docker exec -it python3 bash
---
# cd /src
# chmod +x hello.py
# ./hello.py
```
