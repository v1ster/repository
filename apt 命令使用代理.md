---
title: apt 命令使用代理
date: 2023-04-14  
tags: linux, system
---

```Shell
# 在终端
export http_proxy=http://yourproxyaddress:proxyport

# 永久设置
sudo nano /etc/apt/apt.conf
# 在文件中添加, 保存并退出
Acquire::http::Proxy "http://yourproxyaddress:proxyport";
Acquire::https::Proxy "http://yourproxyaddress:proxyport";

# 在.bashrc 中添加
nano ~/.bashrc

http_proxy=http://username:password@yourproxyaddress:proxyport

export http_proxy
# 保存并退出
source ~/.bashrc

# 临时使用
sudo apt -o Acquire::http::proxy="http://192.168.100.101:1080/" update
```