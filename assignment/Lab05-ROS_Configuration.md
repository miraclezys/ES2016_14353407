---
title: ROS安装
grammar_cjkRuby: true
---
# Lab05:ROS配置

### ROS
ROS(Robot operation system)，一套框架，是一个适用于机器人的开源的元操作系统，底层提供硬件驱动，软件层面支持通用的文件格式。它提供了操作系统应有的服务，包括硬件抽象，底层设备控制，常用函数的实现，进程间消息传递，以及包管理。它也提供用于获取、编译、编写、和跨计算机运行代码所需的工具和库函数。在某些方面ROS相当于一种“机器人框架（robot frameworks）”。可以使用ROS仿真激光雷达的功能。


### 安装ROS
> 参考链接：
> Ubuntu 14.04，15.04:
> http://wiki.ros.org/jade/Installation/Ubuntu
> Ubuntu 15.10，16.04:
> http://wiki.ros.org/kinetic/Installation/Ubuntu

因为我安装的Ubuntu的版本是14.04，所以将使用Ubuntu14.04安装ROS的方法

1. 编译
    1.1 配置Ubuntu软件仓库
    > 配置你的 Ubuntu 软件仓库(repositories) 以允许 "restricted"、"universe" 和 "multiverse"这三种安装模式。 你可以 按照ubuntu中的配置指南来完成配置。

    1.2 添加sources.list
    > 配置电脑使其能够安装来自 packages.ros.org的软件包。 ROS Jade 仅 支持Trusty (14.04)、Utopic (14.10) 和 Vivid (15.04)

    ```
    sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
    ```
    > 也可以使用镜像源，速度更快

    ```
    sudo sh -c '. /etc/lsb-release && echo "deb http://mirror.sysu.edu.cn/ros/ubuntu/ $DISTRIB_CODENAME main" > /etc/apt/sources.list.d/ros-latest.list'
    ```

    1.3 添加keys
    ```
    sudo apt-key adv --keyserver hkp://pool.sks-keyservers.net --recv-key 0xB01FA116
    ```

    1.4 安装
    > 首先，确保你的Debian软件包索引是最新的： 

    ```
    sudo apt-get update
    ```
    > ROS中有很多各种函数库和工具，我们选择安装`桌面完整版`安装：（推荐） 包含ROS、rqt、rviz、通用机器人函数库、2D/3D仿真器、导航以及2D/3D感知功能。

    ```
    sudo apt-get install ros-jade-desktop-full
    ```
    > 也可以使用如下命令查找可用的软件包

    ```
    apt-cache search ros-jade
    ```

    1.5 初始化 rosdep
    > 在开始使用ROS之前你还需要初始化rosdep。rosdep可以方便在你需要编译某些源码的时候为其安装一些系统依赖，同时也是某些ROS核心功能组件所必需用到的工具

    ```
    sudo rosdep init
    rosdep update
    ```

    1.6 环境配置
    > 如果每次打开一个新的终端时ROS环境变量都能够自动配置好（即添加到bash会话中），那将会方便很多：

    ```
    echo "source /opt/ros/jade/setup.bash" >> ~/.bashrc
    source ~/.bashrc
    ```

    > 如果你安装有多个ROS版本, ~/.bashrc 必须只能 source 你当前使用版本所对应的 setup.bash。
    > 如果你只想改变当前终端下的环境变量，可以执行以下命令：

    ```
    source /opt/ros/jade/setup.bash
    ```

    1.7 安装 rosinstall
    > `rosinstall` 是ROS中一个独立分开的常用命令行工具，它可以方便让你通过一条命令就可以给某个ROS软件包下载很多源码树。 要在ubuntu上安装这个工具，请运行：

    ```
    sudo apt-get install python-rosinstall
    ```

    1.8 Build farm 状态
    > 所安装的各种软件包都是通过ROS build farm来编译构建的。可以在这里查看每个软件包的编译状态。

2. 教程
    2.1 获取安装包源码
    ```
    $ apt-get source ros-jade-laser-pipeline
    ```

### 实验心得
此次实验配置了ROS，在安装过程中没有遇到太大的问题，根据安装的步骤进行安装就可以了。因为是配置完之后再写本文档的，所以没有配置过程的截图。

ROS 的主要**目标**是为机器人研究和开发提供代码复用的支持。ROS是一个分布式的进程（也就是节点）框架，这些进程被封装在易于被分享和发布的程序包和功能包集中。
为了支持分享和协作的主要目的，ROS框架也有其它几个目标：小型化、ROS不敏感库、语言独立、方便测试 、可扩展

参考：http://wiki.ros.org/cn/ROS/Introduction


