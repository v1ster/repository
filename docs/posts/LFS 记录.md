---
title: LFS 记录
date: 2025-08-31
tags:
  - linux
category:
  - linux
---
# LFS 记录

#### 1) 看当前目录总大小（人类可读）

```bash
du -sh .
```

#### 备份

```Shell
tar -cJpf $HOME/lfs-temp-tools-12.3.tar.xz .
```

#### 还原

```
cd $LFS
rm -rf ./*
tar -xpf $HOME/lfs-temp-tools-12.3.tar.xz
```

####  Entering the Chroot Environment

```
chroot "$LFS" /usr/bin/env -i   \
    HOME=/root                  \
    TERM="$TERM"                \
    PS1='(lfs chroot) \u:\w\$ ' \
    PATH=/usr/bin:/usr/sbin     \
    MAKEFLAGS="-j_`$(nproc)`_"      \
    TESTSUITEFLAGS="-j_`$(nproc)`_" \
    /bin/bash --login
```

#### Preparing Virtual Kernel File Systems
```
mount -v --bind /dev $LFS/dev

mount -vt devpts devpts -o gid=5,mode=0620 $LFS/dev/pts
mount -vt proc proc $LFS/proc
mount -vt sysfs sysfs $LFS/sys
mount -vt tmpfs tmpfs $LFS/run

if [ -h $LFS/dev/shm ]; then
  install -v -d -m 1777 $LFS$(realpath /dev/shm)
else
  mount -vt tmpfs -o nosuid,nodev tmpfs $LFS/dev/shm
fi
```