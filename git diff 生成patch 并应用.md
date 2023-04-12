---
title: git diff 生成patch 并应用
date: 2023-04-14  
tags: git
---

```Shell
git diff lwdev:ipa_c master > dev1201.patch

git apply --directory=ipa_c --stat  dev1201.patch
git apply --directory=ipa_c --check  dev1201.patch
git apply --directory=ipa_c dev1201.patch
```

