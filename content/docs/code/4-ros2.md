---
title: ROS2
linktitle: ROS2
type: book
data: 2023.11.1
weight: 4
---

#### DDS 配置

```bash
# domain id
export ROS_DOMAIN_ID=0
# network interface
export CYCLONEDDS_URI="<CycloneDDS><Domain><General><NetworkInterfaceAddress>127.0.0.1</NetworkInterfaceAddress></General></Domain></CycloneDDS>"
```
