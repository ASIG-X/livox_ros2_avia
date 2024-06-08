# ROS2 Driver Support for Livox Avia
This is a [Livox Avia](https://www.livoxtech.com/avia) driver under ROS2 Humble modified from the [official Livox driver repository](https://github.com/Livox-SDK/livox_ros2_driver) and the [Livox-SDK repository modified for ubuntu 22.04](https://github.com/acceleration-robotics/Livox-SDK.git). Details about the parameter configuration can be found there.
## Dependencies
* Ubuntu 22.04
* ROS2 Humble
## Compilation
```
cd ~/ros2_ws/src
git clone https://github.com/ASIG-X/livox_ros2_avia
cd ..
colcon build --symlink-install
```
IMPORTANT :

If you would like to compile livox_ros2_driver, be sure to delete/rename the "livox_sdk_static.a" file in the "/usr/local/lib/" directory. The livox_ros2_driver would build a shared library of Livox-SDK on its own.

## Usage
To use this driver, please follow the steps below.
1. Change the 'broadcast_code' in livox_ros2_driver/config/livox_lidar_config.json to the composition of a 14-character serial number (can be found under the QR code of the Avia body shell) and an additional character '1', e.g., '3JEDLB100127651'.
2. Change the 'enable_connect' in the same file from 'false' to 'true'.
3. Open a new terminal and launch the driver by using the following three methods:
* Publish Livox customized point cloud data
```
ros2 launch livox_ros2_avia livox_lidar_msg_launch.py
```
* Publish pointcloud2 format data
```
ros2 launch livox_ros2_avia livox_lidar_launch.py
```
* Publish pointcloud2 format data and visualize the point cloud in RViz
```
ros2 launch livox_ros2_avia livox_lidar_rviz_launch.py
```
