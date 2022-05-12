# PELinux
以Linux为内核的系统维护工具。

## 介绍
多数电脑问题WinPE都是可以解决的，但是在某些情况下不行。

比如说，当电脑的分区表产生了损坏的时候，Windows是无法启动的。在这种情况下，就需要Linux的帮助来修复问题。

PELinux是一个基于Linux的维护系统，内置有fdisk、gdisk等Unix下著名的分区工具和各种其他工具，可以修复很多电脑问题。可以在legacy固件和EFI固件下工作。

## 构建方法
原先打算用LFS的，后来用着用着发现光是安装一个桌面就要下载近一百个软件包，还手动编译，麻了。打算魔改一下[Tiny Core Linux](http://www.tinycorelinux.net)。