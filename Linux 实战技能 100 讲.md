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
# 内部命令
type cd
help cd
# 外部命令
type ls
ls --help
```

**info**

info 比 help 更详细，作为 help 的补充。

```shell
info ls
```

### 9 | 初识 pwd 和 ls 命令

**pwd** 显示当前的目录名称

**cd** 更改当前的操作目录

cd /path/to/ 绝对路径

cd ./path/to/ & cd ../path/to/ 绝对路径

**ls** 查看当前目录下的文件

-l 长格式显示文件

-a 显示隐藏文件

-r 逆序显示

-t 按时间顺序显示

-R 递归显示

**切换 root 用户**

```shell
su - root
```

### 10 | 详解 ls 命令

**du** -sh folder 可以查看文件夹总大小

du -sh folder/* 可以查看文件夹下子文件夹和文件大小

### 11 | 详解 cd 命令

内部命令的 man 帮助会变成 bash 帮助

```shell
help cd
```

回到上一次执行了 cd 的目录

```shell
cd -
```

### 12 | 创建和删除目录

**mkdir**

-p 多极目录

**rmdir**

remove empty directories

**rm**

-r remove directories and their contents recursively

-f ignore nonexistent files and arguments, never prompt

### 13 | 复制和移动目录

**cp**

-r 复制目录

-v explain what is being done

-p same as --preserve=mode,ownership,timestamps. preserve the specified attributes (default: mode, ownership, timestamps)

-a same as -dR --preserve=all

**mv**

**通配符 * ?**

### 14 | 如何在 Linux 下进行文本查看

**cat**

**head**

-n print the first K lines instead of the first 10

**tail**

-n output the last K lines, instead of the last 10

-f output appended data as the file grows

**wc**

Print newline, word, and byte counts for each FILE, and a total line if more than one FILE is specified.

-l print the newline counts

**more**

**less**

### 15 | 打包压缩和解压缩

**打包（备份）**

tar

打包只将目录转换成文件，这是磁带备份的概念，沿用到现代系统。

```shell
tar -cf /tmp/etc-backup.tar /etc
```

```shell
tar -czf /tmp/etc-backup.tar.gz /etc
```

```shell
tar -cjf /tmp/etc-backup.tar.bz2 /etc
```

-c create a new archive

-j bzip2

-z gzip

```shell
tar -xf /tmp/etc-backup.tar -C /root
```

```shell
tar -zxf /tmp/etc-backup.tar.gz -C /root
```

```shell
tar -jxf /tmp/etc-backup.tar.bz2 -C /root
```

-x extract files from an archive

-C change to directory DIR

**压缩与解压缩**

gzip / bzip2

只能对一个文件压缩，不能对目录压缩。

**扩展名**

.tar.gz & .tgz / .tar.bz2 & .tbz2

### 16 | Vim 的四种模式

正常模式 / 插入模式 / 命令模式 / 可视模式

### 17 | Vim 的正常模式

**进入插入模式**

i 当前光标位置 / a 光标位置下一位

I 行头 / A 行尾

O 上一行 / o 下一行

**进入可视模式**

v 字符可视模式

V 行可视模式

ctrl + v 块可视模式

**进入命令模式**

:

**退回到正常模式**

esc

**移动光标**

h 向左 / l 向右 / k 向上 / j 向下

:set nu 显示行数

n + G 指定行 / g 第一行 / G 最后一行

^ 行头 / $ 行尾

**复制 / 剪切**

yy / dd 单行

nyy / ndd 多行

y$ / d$ 从光标到行尾

**粘贴**

p

**撤销 / 重做**

u / ctrl + r

**其他**

x 删除单个字符

r 替换单个字符

### 18 | Vim 的命令模式

:w / :w \<filename\> 保存

:q / :q! 退出

:!\<command\> :r !ifconfig

/\<keyword\> + n 向下搜索

/\<keyword\> + N 向上搜索

:s/\<new word\>/\<old word\> 替换光标所在行一个匹配

:s/\<new word\>/\<old word\>/g 替换光标所在行全部匹配

:%s/\<new word\>/\<old word\> 替换全局（每行）一个匹配

:%s/\<new word\>/\<old word\>/g 替换全局（每行）全部匹配

:\<start line\>,\<end line\>s/\<new word\>/\<old word\>/g 替换指定行全部匹配

:%s@/@//@g 将 / 替换成 //

vim a.txt b.txt :next 下一个文件 :prev 上一个文件

**/etc/vimrc**

### 19 | Vim 的可视模式

**ctrl + v** 块可视模式

I 块插入 + 两次 esc

d 块删除

:set nohlsearch 去除高亮

### 20 | 用户和用户组管理及密码管理

**用户管理**

**useradd** 新建用户

```shell
useradd wilson
# 验证
id wilson
ls -a /home/wilson
tail -5 /etc/passwd
tail -5 /etc/shadow
```

-m create the user's home directory if it does not exist

-g the group name or number of the user's initial login group

-G a list of supplementary groups which the user is also a member of

**userdel** 删除用户

```shell
userdel -r wilson
```

-r files in the user's home directory will be removed along with the home directory itself

**passwd** 修改用户密码

```shell
passwd wilson
```

**usermod** 修改用户属性

-d the user's new login directory

```shell
usermod -d /home/<new user directory> <user>
mv /home/<old user directory> /home/<new user directory>
chown -R <user>:<user group> /home/<new user directory>
```

**chage** 修改用户属性（change user password expiry information）

**su** 临时用户切换

\-  starts the shell as login shell with an environment similar to a real login

```shell
su - <user>
su - root
```

**组管理**

**groupadd** 新建用户组

```shell
groupadd <group>
useradd <user>
usermod -g <group> <user>
```

```shell
useradd -g <group> <user>
```

**groupdel** 删除用户组

### 21 | su 和 sudo 命令的区别和使用方法

**su** 切换用户

**sudo** 以其他用户身份执行命令

```shell
visudo
:!which shutdown
<user> ALL=/usr/sbin/shutdown -c
```

```shell
sudo /usr/sbin/shutdown -c
```

**visudo** /etc/sudoers

### 22 | 用户和用户组的配置文件介绍

```shell
vim /etc/passwd
<user name>:x:<uid>:<gid>:<comment>:<user login directory>:/bin/bash
# x 是否需要密码验证
# /sbin/nologin 不能从终端登录，但是可以使用 ftp、samba 这些服务
```

```shell
vim /etc/shadow
<user name>:<encrypted password>:...

# !! 新添加的用户没有设置密码
postfix:!!:18088::::::
# * 无法验证密码
mail:*:17834:0:99999:7:::
```

```shell
vim /etc/group
mail:x:12:postfix
<group name>:x:<gid>:<user list>

id postfix
uid=89(postfix) gid=89(postfix) groups=89(postfix),12(mail)
```

### 23 | 文件与目录权限的表示方法

**文件类型**

\- 普通文件 / d 目录文件 / b 块（设备）特殊文件 / c 字符（设备）特殊文件 / l 符号链接 / p 命名管道 / s 套接字文件

**文件权限的表示方法**

r=4 读 / w=2 写 / x=1 执行

-rw-r-xr-- 1 username group name mtime filename

创建新文件有默认权限，根据 umask 值计算，属主和属组根据当前进程的用户来设定。

**目录权限的表示方法**

x 进入目录

rx 显示目录内的文件名

wx 修改目录内的文件名

### 24 | 文件权限的修改方法和数字表示方法

**chmod** 修改文件、目录权限

```shell
[ugoa...][[+-=][perms...]...]
chmod u+x a.txt
chmod g-r a.txt
chmod o=w a.txt
chmod a+r a.txt
```

```shell
chmod 644 a.txt
```

```shell
umask
0022
# 普通文件默认权限
644 = 666 - 022
```

**chown** 更改属主、属组

```shell
chown [OPTION]... [OWNER][:[GROUP]] FILE...
```

**chgrp** 更改属组，不常用

ctrl + r 查找之前执行过的命令

### 25 | 权限管理以及文件的特殊权限

属主权限和属组权限冲突时，以属主权限为准。

**SUID** 用于二进制可执行文件，执行命令时取得文件属主权限

```shell
ls -l /usr/bin/passwd
-rwsr-xr-x. 1 root root 27832 Jun 10  2014 /usr/bin/passwd

ls -l /etc/shadow
---------- 1 root root 728 Dec 26 21:26 /etc/shadow

chmod 4755 -> -rwsr-xr-x
```

**SGID** 用于目录，在该目录下创建新的文件和目录，权限自动更改为该目录的属组

**SBIT** 用于目录，在该目录下创建的文件和目录，仅 root 和自己可以删除

```shell
ls -ld /tmp
drwxrwxrwt. 8 root root 4096 Dec 26 12:47 /tmp

chmod 1777 -> drwxrwxrwt
```

### 26 | 网络管理

**网络状态查看工具**

net-tools

ifconfig / route / netstat

iproute2

ip / ss

**网络状态查看命令**

**ifconfig**

eth0 第一块网卡（网络接口）

CentOS 7 使用了一致性网络设备命名，以下都不匹配则使用 eth0

eno1 板载网卡 / ens33 PCI-E 网卡 / enp0s3 无法获取物理信息的 PCI-E 网卡

**网络接口命名修改**

编辑 /etc/default/grub 文件，增加 biosdevname=0 net.ifnames=0

更新 grub # grub2-mkconfig -o /boot/grub2/grub.cfg

重启 # reboot

