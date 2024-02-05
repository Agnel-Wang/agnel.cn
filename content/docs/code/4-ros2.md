---
title: ROS2
linktitle: ROS2
type: book
weight: 4
---

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