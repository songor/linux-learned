# Linux 实战技能 100 讲

### 01 | 课程介绍

### 02 | 内容综述

### 03 | 什么是 Linux

Linux 有两种含义，一种是 Linus 编写的开源操作系统的内核，另一种是广义的操作系统。

### 04 | Linux 的内核版本及常见发行版

[The Linux Kernel Archives](https://www.kernel.org/)

RedHat Enterprise Linux / Fedora / CentOS / Debian / Ubuntu

### 05 | 安装 VirtualBox 虚拟机

[Download VirtualBox](https://www.virtualbox.org/wiki/Downloads)

### 06 | 在虚拟机中安装 Linux 系统

[Download CentOS](http://mirrors.aliyun.com/centos/7/isos/x86_64/)

### 07 | 第一次启动 Linux

**常见目录介绍**

/ 根目录

/root root 用户的家目录

/home/username 普通用户的家目录

/etc 配置文件目录

/bin 命令目录

/sbin 管理命令目录

/usr/bin & /usr/sbin 系统预装的其他命令

/usr/bin 放用户需要执行的命令；/usr/sbin 放系统运行不必须的命令。

### 08 | 万能的帮助命令：man、help、info

**man**

```shell
yum install -y man-pages
```

```shell
man man
DESCRIPTION
       The default action is to search in all of the available sections, following a pre-defined order and to show only the first page found, even if page exists in several sections.
       1   Executable programs or shell commands
       2   System calls (functions provided by the kernel)
       3   Library calls (functions within program libraries)
       4   Special files (usually found in /dev)
       5   File formats and conventions eg /etc/passwd
       6   Games
       7   Miscellaneous (including macro packages and conventions), e.g. man(7), groff(7)
       8   System administration commands (usually only for root)
       9   Kernel routines [Non standard]
```

```shell
man ls
man 1 passwd
man 5 passwd
man -a passwd
```

**help**

shell（命令解释器）自带的命令是内部命令，其他的是外部命令。

```shell
-- 内部命令
type cd
help cd
-- 外部命令
type ls
ls --help
```

**info**

info 比 help 更详细，作为 help 的补充。

```shell
info ls
```

