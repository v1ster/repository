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

3. 

# 参考
- [debian10怎么设置开机自动登录到桌面](https://t.rock-chips.com/forum.php?mod=viewthread&tid=1948)
- [debian系统之修改时间与时区](https://blog.51cto.com/zhujiangtao/1554976)