FROM dorowu/ubuntu-desktop-lxde-vnc:focal
LABEL maintainer="Tiryoh<tiryoh@gmail.com>"

RUN wget -q -O - https://dl.google.com/linux/linux_signing_key.pub | apt-key add -
RUN apt-get update -q && \
    apt-get upgrade -yq && \
    DEBIAN_FRONTEND=noninteractive apt-get install -yq wget curl git build-essential vim sudo lsb-release locales bash-completion tzdata gosu && \
    rm -rf /var/lib/apt/lists/*
RUN useradd --create-home --home-dir /home/ubuntu --shell /bin/bash --user-group --groups adm,sudo ubuntu && \
    echo ubuntu:ubuntu | chpasswd && \
    echo "ubuntu ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers
COPY ./ros-noetic-desktop-testing.sh /
RUN gosu ubuntu /ros-noetic-desktop-testing.sh && \
    rm -rf /var/lib/apt/lists/*
ENV USER ubuntu
