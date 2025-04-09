---
title: Yocoto 调试总结
date: 2025-04-09
tags:
  - linux
category:
  - linux
---
添加设备树编译, 修改文件 `sources/meta-nxp-harpoon/conf/layer.conf` 
```
KERNEL_DEVICETREE:append:imx8mm-lpddr4-evk = " \
                                              freescale/imx8mm-evk-harpoon.dtb \
                                              freescale/imx8mm-evk-harpoon-avb.dtb \
                                              freescale/imx8mm-evk-harpoon-industrial.dtb \
                                              freescale/imx8mm-evk-harpoon-virtio-net.dtb \
+++
                                              freescale/sdp-dante.dtb \
```

添加 defconfig 配置, 修改文件 `sources/meta-nxp-harpoon/recipes-kernel/linux/linux-imx_%.bbappend`
```
DELTA_KERNEL_DEFCONFIG:append:mx8mm-nxp-bsp = "imx_ch1_defconfig"
```

patch 文件生效, 修改文件  `sources/meta-nxp-harpoon/recipes-kernel/linux/linux-imx_%.bbappend`
patch 文件需要存储在 `sources/meta-nxp-harpoon/recipes-kernel/linux/files` 路径下
```
 `sources/meta-nxp-harpoon/recipes-kernel/linux/linux-imx_%.bbappend`
```