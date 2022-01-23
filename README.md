# PELinux
以Linux为内核的系统维护工具。

## 介绍
多数电脑问题WinPE都是可以解决的，但是在某些情况下不行。

比如说，当电脑的分区表产生了损坏的时候，Windows是无法启动的。在这种情况下，就需要Linux的帮助来修复问题。

PELinux是一个基于Linux的维护系统，内置有fdisk、gdisk等Unix下著名的分区工具和各种其他工具，可以修复很多电脑问题。

## 构建方法
目前的构建方法是Linux From Scratch 11。这种方法构架出的系统体积极小，最小的系统只有8MB，还可以运行Apache服务器。

## 构建进度
* 准备环境
* 准备源代码
* 构建LFS工具链和临时编译器
  - 构建交叉编译器
    * Binutils-2.37
    * GCC-11.2.0
    * Linux-5.13.12 内核 API 头文件
    * Glibc-2.34
    * GCC-11.2.0 中的 Libstdc++
  - 交叉编译临时工具
    * M4-1.4.19
    * Ncurses-6.2
    * Bash-5.1.8
    * Coreutils-8.32
    * Diffutils-3.8
    * File-5.40
    * Findutils-4.8.0
    * Gawk-5.1.0
    * Grep-3.7
    * Gzip-1.10
    * Make-4.3
    * Patch-2.7.6
    * Sed-4.8
    * Tar-1.34
    * Xz-5.2.5
    * Binutils-2.37
    * GCC-11.2.0
* 进入 chroot 编译更多临时工具
  - 准备
  - GCC-11.2.0 中的 Libstdc++
  - Gettext-0.21
  - Bison-3.7.6
  - Perl-5.34.0
  - Python-3.9.6
  - Texinfo-6.8                   **正在编译**
  - Util-linux-2.37.2
  - 清理系统

## 关于 LFS 的备注
GMP、MPFR、MPC三个包很容易编译错误，这是官方手册里面没有提到的事情。
1. 在编译GCC-11.2.0时，务必先提前编译三个包，然后在configure时加入三个包的路径（以第一次为例）：
```bash
../configure \
...（LFS书里面说的configure代码） \
--with-gmp=/path/to/gmp \
--with-mpfr=/path/to/mpfr \
--with-mpc=/path/to/mpc
```
如果配置得当，编译的时候configure可能会自动找到三个包，就不需要手动配置了，但是最好还是手动配置。

2. 在chroot中编译的时候，可能会出现找不到编译器的情况，这是因为configure虽然找到了GCC，但是测试不通过。查看`config.log`后，可以知道，是`/lib`下面缺少了三个包的so文件，因此再次编译三个包，在chroot外面configure如下：
```bash
../configure \
--prefix=/mnt/lfs \
--host=i686-lfs-linux-gnu
```
然后`make install`安装一下，问题基本就解决了。