# Copyright 2020-2024 Tiryoh<tiryoh@gmail.com>
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#
# This Dockerfile is based on https://github.com/AtsushiSaito/docker-ubuntu-sweb
# which is released under the Apache-2.0 license.

FROM ubuntu:bionic-20230530

# Automatic platform ARGs in the global scope
# https://docs.docker.com/reference/dockerfile/#automatic-platform-args-in-the-global-scope
ARG TARGETPLATFORM
ARG TARGETARCH

LABEL maintainer="Tiryoh<tiryoh@gmail.com>"

SHELL ["/bin/bash", "-c"]

# Upgrade OS
RUN apt-get update -q && \
    DEBIAN_FRONTEND=noninteractive apt-get upgrade -y && \
    apt-get autoclean && \
    apt-get autoremove && \
    rm -rf /var/lib/apt/lists/*

# Install Ubuntu Mate desktop
RUN apt-get update -q && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y \
        ubuntu-mate-desktop && \
    apt-get autoclean && \
    apt-get autoremove && \
    rm -rf /var/lib/apt/lists/*

# Add Package
RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y \
        tigervnc-standalone-server tigervnc-common \
        supervisor wget curl gosu git sudo python-pip python3-pip \
        build-essential vim sudo lsb-release locales \
        bash-completion tzdata terminator && \
    apt-get autoclean && \
    apt-get autoremove && \
    rm -rf /var/lib/apt/lists/*

# Add tini
RUN curl -sL "https://github.com/krallin/tini/releases/download/v0.19.0/tini-$TARGETARCH" -o /usr/bin/tini && \
    chmod +x /usr/bin/tini

# Fix numpy install error
# https://github.com/numpy/numpy/issues/24377
RUN if [ "$TARGETPLATFORM" = "linux/arm64" ]; then \
    pip3 install --no-cache-dir 'cython<3' && \
    pip3 install --no-cache-dir numpy; \
    fi
# noVNC and Websockify
RUN git clone https://github.com/AtsushiSaito/noVNC.git -b add_clipboard_support /usr/lib/novnc
RUN pip3 install --no-cache-dir git+https://github.com/novnc/websockify.git@v0.10.0
RUN ln -s /usr/lib/novnc/vnc.html /usr/lib/novnc/index.html

# Set remote resize function enabled by default
RUN sed -i "s/UI.initSetting('resize', 'off');/UI.initSetting('resize', 'remote');/g" /usr/lib/novnc/app/ui.js

# Disable auto update and crash report
RUN sed -i 's/Prompt=.*/Prompt=never/' /etc/update-manager/release-upgrades
RUN sed -i 's/enabled=1/enabled=0/g' /etc/default/apport

# Install Firefox
RUN DEBIAN_FRONTEND=noninteractive add-apt-repository ppa:mozillateam/ppa -y && \
    echo 'Package: *' > /etc/apt/preferences.d/mozilla-firefox && \
    echo 'Pin: release o=LP-PPA-mozillateam' >> /etc/apt/preferences.d/mozilla-firefox && \
    echo 'Pin-Priority: 1001' >> /etc/apt/preferences.d/mozilla-firefox && \
    apt-get update -q && \
    apt-get install -y --allow-downgrades \
    firefox && \
    apt-get autoclean && \
    apt-get autoremove && \
    rm -rf /var/lib/apt/lists/*

# Install VSCodium
# The latest VSCodium requires new gcc which is not ready for Ubuntu 18.04
RUN apt-get update -q && \
    curl -sL https://github.com/VSCodium/vscodium/releases/download/1.84.2.23319/codium_1.84.2.23319_${TARGETARCH}.deb -o codium.deb && \
    apt-get install -y ./codium.deb && \
    rm codium.deb && \
    apt-get autoclean && \
    apt-get autoremove && \
    rm -rf /var/lib/apt/lists/*

# Install ROS
ENV ROS_DISTRO melodic
# desktop or ros-base
ARG INSTALL_PACKAGE=desktop

RUN apt-get update -q && \
    apt-get install -y curl gnupg2 lsb-release && \
    curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg && \
    echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros/ubuntu $(lsb_release -cs) main" | tee /etc/apt/sources.list.d/ros.list > /dev/null && \
    apt-get update -q && \
    apt-get install -y ros-${ROS_DISTRO}-${INSTALL_PACKAGE} \
    python-rosinstall \
    python-rosinstall-generator \
    python-wstool \
    python-catkin-tools \
    python-rosdep python3-vcstool && \
    rosdep init && \
    rm -rf /var/lib/apt/lists/*

RUN rosdep update --include-eol-distros

RUN apt-get update -q && \
    apt-get install -y \
    ros-${ROS_DISTRO}-gazebo-ros-pkgs && \
    rm -rf /var/lib/apt/lists/*

# Enable apt-get completion after running `apt-get update` in the container
RUN rm /etc/apt/apt.conf.d/docker-clean

COPY ./entrypoint.sh /
ENTRYPOINT [ "/bin/bash", "-c", "/entrypoint.sh" ]

ENV USER ubuntu
ENV PASSWD ubuntu
