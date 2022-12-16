# PELinux
以Linux为内核的系统维护工具。

## 介绍
多数电脑问题WinPE都是可以解决的，但是在某些情况下不行。

比如说，当电脑的分区表产生了损坏的时候，Windows是无法启动的。在这种情况下，就需要Linux的帮助来修复问题。

PELinux是一个基于Linux的维护系统，内置有fdisk、gdisk等Unix下著名的分区工具和各种其他工具，可以修复很多电脑问题。可以在legacy固件和EFI固件下工作。

## 构建方法
原先使用的是[Linux from Scratch](https://www.linuxfromscratch.org/)，这个项目 ~~专门为那些厌倦世间常见Linux系统的人，量体裁衣，提供符合他们身份的Linux系统~~ 提供一整套指南让人自己制作Linux系统，但是做出来的系统仍然体积很大，并且添加新的软件包很麻烦。

## 可供下载的参考资料

PELinux的base镜像可以在Releases下载。

利用GRUB制作的启动盘，可以在UEFI和Legacy环境下启动。
> 蓝奏云[下载地址](https://wwmf.lanzout.com/ikf5u0itljtc
) 密码：5ymb
> 
> 百度云[下载地址](https://pan.baidu.com/s/1QseSN7EYP8CRWrc-i6aBtw 
) 密码：0290