FROM python:3.8-slim-bullseye
ENV CONDA_DIR=/opt/conda
ENV LANG=C.UTF-8 LC_ALL=C.UTF-8
ENV PATH=${CONDA_DIR}/bin:${PATH}

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get -y update && \
    apt-get -y install \
    software-properties-common \
    binutils \
    libproj-dev \
    gdal-bin \
    libgdal-dev \
    gcc \
    python3-dev \
    build-essential \
    libxslt-dev \
    libffi-dev \
    libssl-dev \
    libgeos-dev \
    sudo \
    unzip \
    awscli \
    wget \
    git && \
    wget https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-Linux-x86_64.sh -O /tmp/miniforge.sh && \
    /bin/bash /tmp/miniforge.sh -b -p ${CONDA_DIR}

# Create the environment:
COPY .devcontainer/environment.yml .
RUN conda env create -f environment.yml
RUN conda init

ARG conda_env=geo

RUN useradd -rm -d /home/geo -s /bin/bash -g root -G sudo -u 1001 geo -p $(openssl passwd -1 password)

RUN chown -R geo /opt/conda


USER geo
WORKDIR /home/geo


ENV USERNAME='geo'

ENTRYPOINT /bin/bash -c "conda activate $conda_env"
