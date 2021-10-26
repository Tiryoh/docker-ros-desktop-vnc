# docker-ros-desktop-vnc

![Docker Automated build](https://img.shields.io/docker/automated/tiryoh/ros-desktop-vnc)
[![Publish to Registry](https://github.com/Tiryoh/docker_ros-desktop-vnc/workflows/Publish%20to%20Registry/badge.svg?branch=master)](https://github.com/Tiryoh/docker-ros-desktop-vnc/actions?query=workflow%3A%22Publish+to+Registry%22+branch%3Amaster)
[![](https://img.shields.io/docker/pulls/tiryoh/ros-desktop-vnc.svg)](https://hub.docker.com/r/tiryoh/ros-desktop-vnc)

A Docker image to provide HTML5 VNC interface to access Ubuntu LXDE + ROS, based on [dorowu/ubuntu-desktop-lxde-vnc](https://github.com/fcwu/docker-ubuntu-vnc-desktop)

ROS 2 version: https://github.com/Tiryoh/docker-ros2-desktop-vnc

![Image from Gyazo](https://i.gyazo.com/044eed360f341c2819023a81aa709bd5.gif)

このツールの詳細については以下の記事で紹介しています。  
The details of these tools are written in Japanese on this page.  
https://memoteki.net/archives/2955

## Quick Start

Run the docker container and access with port `6080`.  
Change the `shm-size` value depending on the situation.

```
docker run -p 6080:80 --shm-size=512m tiryoh/ros-desktop-vnc:melodic
```

Browse http://127.0.0.1:6080/.

![Image from Gyazo](https://i.gyazo.com/ab43ab3f6dc10b5186416499e49d0bbe.jpg)

## Docker tags

* [`noetic`, `latest`](https://github.com/Tiryoh/docker-ros-desktop-vnc/blob/master/noetic/Dockerfile)
* [`melodic`](https://github.com/Tiryoh/docker-ros-desktop-vnc/blob/master/melodic/Dockerfile)
* ~~[`kinetic`](https://github.com/Tiryoh/docker-ros-desktop-vnc/blob/master/kinetic/Dockerfile)~~ depricated

Docker tags and build logs are listed on this page.  
https://github.com/Tiryoh/docker-ros-desktop-vnc/wiki

## FAQ

### `apt update` shows an `GPG error`

Error:

```
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://packages.ros.org/ros/ubuntu bionic InRelease: The following signatures were invalid: EXPKEYSIG F42ED6FBAB17C654 Open Robotics <info@osrfoundation.org>
E: The repository 'http://packages.ros.org/ros/ubuntu bionic InRelease' is not signed.
```

Details of this error: https://discourse.ros.org/t/ros-gpg-key-expiration-incident/20669

There are two ways to solve this.

#### 1. Update the ros-desktop-vnc image

Stop the container and re-pull the image.

Example command:

```
docker pull tiryoh/ros-desktop-vnc:melodic
```

#### 2. Update the key (temporary fix)

If you do not want to stop the container, you can update the key manually.  
NOTE: This is a temporaly fix. Please consider updating the image.

Example command:

```
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | apt-key add -
apt update
```

## License

Copyright 2020 Tiryoh\<tiryoh@gmail.com\>

This repository is released under the Apache License 2.0, see [LICENSE](./LICENSE).  
Unless attributed otherwise, everything in this repository is under the Apache License 2.0.

### Acknowledgements

This Docker image is based on [dorowu/ubuntu-desktop-lxde-vnc](https://github.com/fcwu/docker-ubuntu-vnc-desktop), licensed under the [Apache License 2.0](https://github.com/fcwu/docker-ubuntu-vnc-desktop/blob/60f9ae18e71e9fabbfb23f67b212e64ab72c206e/LICENSE).
