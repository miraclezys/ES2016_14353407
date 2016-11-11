---
title: 配置Cartographer
grammar_cjkRuby: true
---

# 配置Cartographer
> Cartographer is a system that provides real-time simultaneous localization and mapping (SLAM) in 2D and 3D across multiple platforms and sensor configurations. This project provides Cartographer’s ROS integration.


### 编译安装

> Ubuntu 16.04 已配置好ROS

### Building & Installation
1. Install wstool and rosdep.
    ```
    sudo apt-get update
    sudo apt-get install -y python-wstool python-rosdep ninja-build
    ```
    
2. Create a new workspace in 'catkin_ws'
    ```
    mkdir catkin_ws
    cd catkin_ws
    wstool init src
    ```
    
3. Merge the cartographer_ros.rosinstall file and fetch code for dependencies
    ```
    wstool merge -t src https://raw.githubusercontent.com/googlecartographer/cartographer_ros/master/cartographer_ros.rosinstall 
    wstool update -t src
    ```
    
4. Install deb dependencies
    ```
    rosdep init
    rosdep update
    rosdep install --from-paths src --ignore-src --rosdistro=${ROS_DISTRO} -y
    ```
    
5. Build and install
    ```
    catkin_make_isolated --install --use-ninja
    source install_isolated/setup.bash
    ```
    
### Running the demos
>  Download the example bags (e.g. 2D and 3D backpack collections of the Deutsches Museum)

1. Download the 2D backpack example bag
    ```
    wget -P ~/Downloads https://storage.googleapis.com/cartographer-public-data/bags/backpack_2d/cartographer_paper_deutsches_museum.bag
    ```
2. Launch the 2D backpack demo
    ```
    roslaunch cartographer_ros demo_backpack_2d.launch bag_filename:=${HOME}/Downloads/cartographer_paper_deutsches_museum.bag
    ```
    
    Result:
    ![](/assignment/img/ros_1.jpg)   
