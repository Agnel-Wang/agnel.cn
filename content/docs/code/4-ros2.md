---
title: ROS2
linktitle: ROS2
type: book
weight: 4
---

一键安装
```bash
wget http://fishros.com/install -O fishros && . fishros
```

#### DDS 配置

```bash
# domain id
export ROS_DOMAIN_ID=0
```

network interface
更改后ros2 topic list可能依然没有显示
但cyclonedds ps会显示
```bash
export CYCLONEDDS_URI="<CycloneDDS><Domain><General><NetworkInterfaceAddress>192.168.123.234</NetworkInterfaceAddress></General></Domain></CycloneDDS>"
```

#### ROS2设置cyclonedds中间件

```bash
sudo apt install ros-foxy-rmw-cyclonedds-cpp
#bashrc
export RMW_IMPLEMENTATION=rmw_cyclonedds_cpp
```