<a name="unreleased"></a>
## [Unreleased]


<a name="v1.3.0"></a>
## [v1.3.0] - 2024-06-04
### Chore
- Bump docker/setup-qemu-action from 2 to 3 ([#49](https://github.com/Tiryoh/docker-ros-desktop-vnc/issues/49))
- Bump docker/metadata-action from 3 to 4 ([#42](https://github.com/Tiryoh/docker-ros-desktop-vnc/issues/42))
- Bump actions/checkout from 2 to 3 ([#44](https://github.com/Tiryoh/docker-ros-desktop-vnc/issues/44))
- Bump docker/login-action from 1 to 2 ([#43](https://github.com/Tiryoh/docker-ros-desktop-vnc/issues/43))
- Bump docker/setup-qemu-action from 1 to 2 ([#41](https://github.com/Tiryoh/docker-ros-desktop-vnc/issues/41))
- Create dependabot.yml ([#40](https://github.com/Tiryoh/docker-ros-desktop-vnc/issues/40))
- Add docker label ([#34](https://github.com/Tiryoh/docker-ros-desktop-vnc/issues/34))

### Fix
- Fix GPG error on Ubuntu 20.04 ([#35](https://github.com/Tiryoh/docker-ros-desktop-vnc/issues/35))


<a name="v1.2.0"></a>
## [v1.2.0] - 2022-01-08
### CI
- Fix deploy log URL ([#32](https://github.com/Tiryoh/docker-ros-desktop-vnc/issues/32))
- Create multi architecture image ([#31](https://github.com/Tiryoh/docker-ros-desktop-vnc/issues/31))
- Simplify authentication ([#30](https://github.com/Tiryoh/docker-ros-desktop-vnc/issues/30))

### Features
- Add Dockerfile for noetic-arm64 to support Apple Silicon ([#20](https://github.com/Tiryoh/docker-ros-desktop-vnc/issues/20))
- Drop ROS Kinetic support ([#23](https://github.com/Tiryoh/docker-ros-desktop-vnc/issues/23))


<a name="v1.1.1"></a>
## [v1.1.1] - 2021-05-04
### CI
- Fix duplicate conditions ([#19](https://github.com/Tiryoh/docker-ros-desktop-vnc/issues/19))

### Chore
- Update git-chglog config ([#21](https://github.com/Tiryoh/docker-ros-desktop-vnc/issues/21))


<a name="v1.1.0"></a>
## [v1.1.0] - 2021-05-04
### CI
- Use official skip [skip ci]
- Ignore error on testing image ([#18](https://github.com/Tiryoh/docker-ros-desktop-vnc/issues/18))

### Features
- Add Dockerfile for arm64 to support Apple Silicon ([#16](https://github.com/Tiryoh/docker-ros-desktop-vnc/issues/16))


<a name="v1.0.0"></a>
## [v1.0.0] - 2021-05-04
### BREAKING CHANGE
- Set noetic the "latest" image ([#17](https://github.com/Tiryoh/docker-ros-desktop-vnc/issues/17))


<a name="v0.3.1"></a>
## [v0.3.1] - 2021-05-04
### Chore
- Update build log format to avoid sync error ([#14](https://github.com/Tiryoh/docker-ros-desktop-vnc/issues/14))


<a name="v0.3.0"></a>
## [v0.3.0] - 2021-05-04
### Chore
- Publish to ghcr.io ([#13](https://github.com/Tiryoh/docker-ros-desktop-vnc/issues/13))

### Features
- Add ROS Noetic (ros-testing) ([#5](https://github.com/Tiryoh/docker-ros-desktop-vnc/issues/5))


<a name="v0.2.0"></a>
## [v0.2.0] - 2020-08-11
### Features
- Enable catkin-tools for ROS Noetic ([#11](https://github.com/Tiryoh/docker-ros-desktop-vnc/issues/11))


<a name="v0.1.0"></a>
## [v0.1.0] - 2020-05-24
### Features
- Add ROS Noetic ([#9](https://github.com/Tiryoh/docker-ros-desktop-vnc/issues/9))

### Fix
- Fix gosu not found

### Refactor
- Update the installer execution step to avoid rosdep permission error ([#7](https://github.com/Tiryoh/docker-ros-desktop-vnc/issues/7))
- Remove dupulicate ENV ([#6](https://github.com/Tiryoh/docker-ros-desktop-vnc/issues/6))


<a name="v0.0.1"></a>
## v0.0.1 - 2020-02-13
### Chore
- Add git-chglog settings
- Update deploy script for Kinetic
- Add GHA settings
- Add license file

### Features
- Add ROS Kinetic Dockerfile
- Add ROS Melodic Dockerfile

### Fix

- Fix ENV ROS_DISTRO from dashing to melodic([#1](https://github.com/Tiryoh/docker_ros-desktop-vnc/pull/1))


[Unreleased]: https://github.com/Tiryoh/docker-ros-desktop-vnc/compare/v1.3.0...HEAD
[v1.3.0]: https://github.com/Tiryoh/docker-ros-desktop-vnc/compare/v1.2.0...v1.3.0
[v1.2.0]: https://github.com/Tiryoh/docker-ros-desktop-vnc/compare/v1.1.1...v1.2.0
[v1.1.1]: https://github.com/Tiryoh/docker-ros-desktop-vnc/compare/v1.1.0...v1.1.1
[v1.1.0]: https://github.com/Tiryoh/docker-ros-desktop-vnc/compare/v1.0.0...v1.1.0
[v1.0.0]: https://github.com/Tiryoh/docker-ros-desktop-vnc/compare/v0.3.1...v1.0.0
[v0.3.1]: https://github.com/Tiryoh/docker-ros-desktop-vnc/compare/v0.3.0...v0.3.1
[v0.3.0]: https://github.com/Tiryoh/docker-ros-desktop-vnc/compare/v0.2.0...v0.3.0
[v0.2.0]: https://github.com/Tiryoh/docker-ros-desktop-vnc/compare/v0.1.0...v0.2.0
[v0.1.0]: https://github.com/Tiryoh/docker-ros-desktop-vnc/compare/v0.0.1...v0.1.0
