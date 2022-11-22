FROM python:3

COPY requirements.txt .
RUN apt-get update && \
    pip install --upgrade pip && \
    pip install --upgrade setuptools && \
    pip install -r requirements.txt && \
    pip install jupyterlab

WORKDIR /src
