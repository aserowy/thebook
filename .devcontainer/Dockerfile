FROM mcr.microsoft.com/vscode/devcontainers/base:ubuntu

RUN apt update \
    && apt install -y python3 python3-pip \
    && pip3 install --no-cache --upgrade pip setuptools

RUN pip3 install --no-cache "mkdocs>=1.1.0"
RUN pip3 install --no-cache "mkdocs-awesome-pages-plugin>=2.4.0"
RUN pip3 install --no-cache "mkdocs-material>=6.1.7"
RUN pip3 install --no-cache "mkdocs-section-index>=0.2.1"

WORKDIR /workspace/

ENTRYPOINT mkdocs serve