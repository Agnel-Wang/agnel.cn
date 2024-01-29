---
title: ROS
linktitle: ROS
type: book
data: 2023.11.1
weight: 3
---

#### Joystick

```shell
#install
sudo apt install ros-<>-joy
sudo apt install ros-<>-joystick-drivers
```

```shell
roscore
rosrun joy joy_node
rosropic echo joy
```

更改输入端口

```shell
ls /dev/input/
rosparam set joy_node/dev "/dev/input/jsX"
```