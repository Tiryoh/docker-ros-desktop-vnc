# docker_ros-desktop-vnc

A Docker image to provide HTML5 VNC interface to access Ubuntu LXDE + ROS, based on [dorowu/ubuntu-desktop-lxde-vnc](https://github.com/fcwu/docker-ubuntu-vnc-desktop)


## Quick Start

Run the docker container and access with port `6080`

```
docker run -p 6080:80 -v /dev/shm:/dev/shm tiryoh/ros-desktop-vnc:melodic
```

Browse http://127.0.0.1:6080/

![Image from Gyazo](https://i.gyazo.com/ab43ab3f6dc10b5186416499e49d0bbe.jpg)

## Docker tags


## License

Copyright 2020 Tiryoh\<tiryoh@gmail.com\>

This repository is released under the Apache License 2.0, see [LICENSE](./LICENSE).  
Unless attributed otherwise, everything in this repository is under the Apache License 2.0.

### Acknowledgements

This Docker image is based on [dorowu/ubuntu-desktop-lxde-vnc](https://github.com/fcwu/docker-ubuntu-vnc-desktop), licensed under the [Apache License 2.0](https://github.com/fcwu/docker-ubuntu-vnc-desktop/blob/60f9ae18e71e9fabbfb23f67b212e64ab72c206e/LICENSE).
