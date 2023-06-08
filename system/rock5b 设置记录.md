---
title: rock5b 设置记录
date: 2023-05-29  
tags: linux 
---
1. 设置用户自动登陆桌面
```Shell
sudo  vi  /etc/lightdm/lightdm.conf

---
#autologin-user=
+++
autologin-user=USER
```

2. 修改密码
```Shell
sudo su
passwd rock
```

3.  设置imx219 获取全分辨率
```Shell
media-ctl -d /dev/media0 --set-v4l2 '"m00_b_imx219 3-0010":0[fmt:SRGGB10_1X10/3280x2464]'

# media-ctl -d /dev/media0 --set-v4l2 '"rockchip-csi2-dphy0":0[fmt:SRGGB10_1X10/3280x2464]'

media-ctl -d /dev/media1 --set-v4l2 '"rkisp-isp-subdev":0[fmt:SRGGB10_1X10/3280x2464]'

media-ctl -d /dev/media1 --set-v4l2 '"rkisp-isp-subdev":2[fmt:SRGGB10_1X10/3280x2464]'

media-ctl -d /dev/media1 --set-v4l2 '"rkisp-isp-subdev":0[crop:(0,0)/3280x2464]'

media-ctl -d /dev/media1 --set-v4l2 '"rkisp-isp-subdev":2[crop:(0,0)/3280x2464]'
```

4. 查看拓扑结构
```Shell
media-ctl -p -d 0
```

# 参考
- [debian10怎么设置开机自动登录到桌面](https://t.rock-chips.com/forum.php?mod=viewthread&tid=1948)
- [debian系统之修改时间与时区](https://blog.51cto.com/zhujiangtao/1554976)