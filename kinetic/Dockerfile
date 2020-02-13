FROM dorowu/ubuntu-desktop-lxde-vnc:xenial
LABEL maintainer="Tiryoh<tiryoh@gmail.com>"

RUN apt-get update -q && \
    apt-get upgrade -yq && \
    apt-get install -yq wget curl git build-essential vim sudo lsb-release locales bash-completion tzdata && \
    rm -rf /var/lib/apt/lists/*
RUN useradd -m -d /home/ubuntu ubuntu -p $(perl -e 'print crypt("ubuntu", "salt"),"\n"') && \
    echo "ubuntu ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers
ENV ROS_DISTRO kinetic
RUN git clone https://github.com/Tiryoh/ros_setup_scripts_ubuntu.git /tmp/ros_setup_scripts_ubuntu && \
    cd /tmp/ros_setup_scripts_ubuntu && \
    ./ros-kinetic-desktop.sh && \
    rm -rf /var/lib/apt/lists/*
ENV USER ubuntu
