# Fixes Implemented in Borealbikes Fork

1. Skip version check to allow 0.9.13. https://github.com/carla-simulator/ros-bridge/issues/608#issuecomment-1104055866
2. A Python error in a package that doesn't use Python, so change build system to ament_cmake. https://github.com/carla-simulator/ros-bridge/pull/613/commits/5e36ba502029638747d6b8f8bfe1d67a10406d9a
3. Remove some over-eager configuration arguments in `carla_ros_bridge/launch/carla_ros_bridge.launch.py` and `carla_ros_bridge/src/carla_ros_bridge/bridge.py, so that it doesn't change any CARLA world settings, and doesn't crash the main server as often.
4. Fix issue in `carla_ros_bridge/src/carla_ros_bridge/pseudo_actor.py` where it can't handle multiple sensors of the same type. The fix uses the sensor's uid to create new ROS topics for each actual sensor.

I don't know why they haven't been pushed to upstream, so I made this fork.

# ROS/ROS2 bridge for CARLA simulator

[![Actions Status](https://github.com/carla-simulator/ros-bridge/workflows/CI/badge.svg)](https://github.com/carla-simulator/ros-bridge)
[![Documentation](https://readthedocs.org/projects/carla/badge/?version=latest)](http://carla.readthedocs.io)
[![GitHub](https://img.shields.io/github/license/carla-simulator/ros-bridge)](https://github.com/carla-simulator/ros-bridge/blob/master/LICENSE)
[![GitHub release (latest by date)](https://img.shields.io/github/v/release/carla-simulator/ros-bridge)](https://github.com/carla-simulator/ros-bridge/releases/latest)

 This ROS package is a bridge that enables two-way communication between ROS and CARLA. The information from the CARLA server is translated to ROS topics. In the same way, the messages sent between nodes in ROS get translated to commands to be applied in CARLA.

![rviz setup](./docs/images/ad_demo.png "AD Demo")

**This version requires CARLA 0.9.12**

## Features

- Provide Sensor Data (Lidar, Semantic lidar, Cameras (depth, segmentation, rgb, dvs), GNSS, Radar, IMU)
- Provide Object Data (Transforms (via [tf](http://wiki.ros.org/tf)), Traffic light status, Visualization markers, Collision, Lane invasion)
- Control AD Agents (Steer/Throttle/Brake)
- Control CARLA (Play/pause simulation, Set simulation parameters)

## Getting started and documentation

Installation instructions and further documentation of the ROS bridge and additional packages are found [__here__](https://carla.readthedocs.io/projects/ros-bridge/en/latest/).
