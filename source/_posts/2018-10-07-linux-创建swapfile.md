---
title: linux-创建swapfile
toc: true
date: 2018-10-07 23:41:49
tags:
  -linux
categories:
  - 工具
  - linux
  - 奇技淫巧
---

Linux创建交换文件：

1. 创建交换文件 -- swapfile
```bash
sudo fallocate -l 16G /swapfile #在根目录下创建一个16G的swapfile 
```

2. 更改/swapfile权限
```bash
sudo chmod 600 /swapfile
```

3. 格式化为swap
```bash
sudo mkswap /swapfile
```

4. 应用之
```bash
sudo swapon /swapfile
```

5. 为了以后开机自动挂载swap, 将其加入/etc/fstab。编辑/etc/fstab, 在其中加入一行:
```
/swapfile    none   swap   defaults  0   0
```
6. 如果对这个/swapfile不满意，比如想更改大小，可以这样
```
sudo swapoff -a   #关掉swap
sudo rm -f /swapfile  #删掉当前swapfile
```
回到第一步重新设置swapfile

