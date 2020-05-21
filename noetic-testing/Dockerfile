FROM dorowu/ubuntu-desktop-lxde-vnc:focal
LABEL maintainer="Tiryoh<tiryoh@gmail.com>"

ENV DEBIAN_FRONTEND noninteractive
RUN echo "Set disable_coredump false" >> /etc/sudo.conf
RUN apt-get update -q && \
    apt-get upgrade -yq && \
    apt-get install -yq wget curl git build-essential vim sudo lsb-release locales bash-completion tzdata && \
    rm -rf /var/lib/apt/lists/*
RUN useradd -m -d /home/ubuntu ubuntu -p $(perl -e 'print crypt("ubuntu", "salt"),"\n"') && \
    echo "ubuntu ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers
COPY ./ros-noetic-desktop-testing.sh /
RUN /ros-noetic-desktop-testing.sh && \
    rm -rf /var/lib/apt/lists/*
ENV USER ubuntu
