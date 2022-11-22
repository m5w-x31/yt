(2022.11.22)

# Docker JupyterLab

## ref.

- https://jupyterlab.readthedocs.io/en/stable/

---

## Environment

### Server

- Ubutntu 22.04 Server
  - ip: 192.168.0.100
  - user: m5w

### Software

- Docker version 20.10.21
- Docker Compose version v2.12.2

## Directory structure

```
docker_jupyterlab/
- docker-compose.yml
- Dockerfile
- requirements.txt
- src/
  - hellopy
  - test.ipynb
```

---

## Edit files

- docker-compose.yml
- Dockerfile
- requirements.txt
- src/test.py

## docker build/run

```
$ docker-compose build
$ docker-compose up -d
```

```
$ docker ps
```

## jupyterlab web access

```
http://192.168.0.100:8888/
```

---

## jupyterlab 

### Console test

- Console > Python 3(ipykernel)

```
print(1+1)
```

```
import requests
r = requests.get('https://m5w.net')
print(r.text)
```

### Terminal test

- Other > Terminal

```
# python --version

# python hello.py
```

### Notebook

- Notebook > Python 3(ipykernel)

```
print(1+1)
```

```
import requests
r = requests.get('https://m5w.net')
print(r.text)
```

#### Notebook from vscode

- vscode extension : Jupyter

- "src/test.ipynb" open
  - カーネル選択

```
print(1+2)
```
