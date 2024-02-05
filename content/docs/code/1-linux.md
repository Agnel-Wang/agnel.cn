---
title: Linux
linktitle: Linux
type: book
weight: 1
---

## Linux

### Installation

1. 制作启动盘

- 下载镜像
```
官网下载
https://www.ubuntu.com/download
清华大学镜像站下载
https://mirrors.tuna.tsinghua.edu.cn/ubuntu-releases/18.04/
```

- 下载U盘制作软件
```
rufus
https://rufus.ie/
```

2. 安装

```sh
# 小鱼一键安装
wget http://fishros.com/install -O fishros && . fishros
```

### Autostart

**Service**

```sh
cd /etc/systemd/usr/
touch test.service
sudo chmod 664 test.service
```

```sh
[Unit]
Description=autostart service

[Service]
Type=oneshot
ExecStart=/bin/su unitree -c 'sh /home/unitree/test.sh'

[Install]
WantedBy=default.target
```

```sh
sudo systemctl enable test.service
```

### Network

communicate with arm by ethernet

1. temporary settings
```
sudo ifconfig NAME down
sudo ifconfig NAME IP/24  or sudo ifconfig NAME up IP down 255.255.255.0
```

    24 means netmask 255.255.255.0

2. permanent settings
```
sudo vim /etc/network/interfaces
```

    add text beneath into file
```
auto NAME
iface NAME inet static
address IP
netmask 255.255.255.0
```
    and then
```
sudo /etc/init.d/networking restart
```

3. network manager

查看网络连接列表
```sheel
nmcli connection show 
```

创建一个以太网连接
```shell
nmcli connection add type ethernet con-name <connection_name> ifname <interface_name>
```
（<connection_name> 是连接名称，任意命名； <interface_name> 是网络接口名称，如eth0）

4. 网络不好时设置代理

```bash
# 10.0.5.125是目标电脑IP，一般clash所用的port为7890
export http_proxy=http://10.0.5.125:7890
export https_proxy=http://10.0.5.125:7890
```

### Serial

ubuntu打开串口需要sudo权限

解决办法:
更改串口设备的权限：你可以更改串口设备文件的权限，使当前用户具有对其的读写权限。执行以下命令将设备文件的所有者更改为当前用户：
```bash
sudo chown $USER:$USER /dev/ttyUSB0
```

可用软件：
+ cutecom
+ minicom

### Swap space

```bash
free -t 查询内存
sudo dd if=/dev/zero of=sfile bs=1024 count=1000000
sudo mkswap sfile
sudo swapon sfile
sudo swapoff sfile
```

### Software

+ kazam 录屏

### debug

```bash
# 查看当前文件夹下的占用空间
du -ah --max-depth=1 
```

