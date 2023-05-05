---
title: ubuntu 设置虚拟显示器输出
date: 2023-04-18  
tags: linux, system
---

### 安装程序

```Shell
$ sudo apt-get install  xserver-xorg-core-hwe-18.04
$ sudo apt-get install  xserver-xorg-video-dummy-hwe-18.04  --fix-missing
```

### 创建配置文件

```
$ sudo nano /etc/X11/xorg.conf.d/xorg.conf

Section "Device"
    Identifier  "Configured Video Device"
    Driver      "dummy"
EndSection
Section "Monitor"
    Identifier  "Configured Monitor"
    HorizSync 31.5-48.5
    VertRefresh 50-70
EndSection
Section "Screen"
    Identifier  "Default Screen"
    Monitor     "Configured Monitor"
    Device      "Configured Video Device"
    DefaultDepth 24
    SubSection "Display"
    Depth 24
    Modes "1920x1080"
    EndSubSection
EndSection
```

### 配置文件存储位置

```
/etc/X11/xorg.conf.d/xorg.conf
/usr/share/X11/xorg.conf.d/xorg.conf
```

### 参考

- [ubuntu18.04安装虚拟显示器，不接显示器可远程桌面_AIchiNiurou的博客-CSDN博客_xrandr 不接显示器](https://blog.csdn.net/weixin_44523062/article/details/105405019)