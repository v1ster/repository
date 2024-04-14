---
title: 创建ASCII码的目录树
date: 2023-12-22
tags:
  - Shell
  - tool
---

```Shell
 ls -R | grep ":$" | sed -e 's/:$//' -e 's/[^-][^\/]*\//--/g' -e 's/^/   /' -e 's/-/|/'
# or
tree .
```