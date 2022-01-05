# Linux 实战技能 100 讲

## 第一章 基础篇

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

## 第二章 系统操作篇

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

## 第三章 系统管理篇

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

编辑 /etc/default/grub 文件，增加 biosdevname=0 net.ifnames=0 到 GRUB_CMDLINE_LINUX

更新 grub # grub2-mkconfig -o /boot/grub2/grub.cfg

重启 # reboot

修改文件名为 /etc/sysconfig/network-scripts/ifcfg-eth0

### 27 | 查看网络配置

ifconfig eth0

inet 172.23.211.126 / netmask 255.255.240.0 / ether 00:16:3e:0a:79:e4 / RX / TX

查看网卡物理连接 mii-tool eth0

查看网关 route -n，使用 -n 参数不解析主机名

### 28 | 修改网络配置

**ifconfig**

ifconfig \<接口\> \<IP 地址\> [netmask 子网掩码]

ifup \<接口\>

ifdown \<接口\>

**route**

```shell
route  [-v] [-A family |-4|-6] add [-net|-host] target [netmask Nm] [gw Gw] [metric N] [mss M] [window W] [irtt I] [reject] [mod] [dyn] [reinstate] [[dev] If]
```

route add default gw \<网关 IP\>

route add -host \<指定 IP\> gw \<网关 IP\>

route add -net \<指定网段> netmask \<子网掩码> gw \<网关 IP\>

```shell
route  [-v] [-A family |-4|-6] del [-net|-host] target [gw Gw] [netmask Nm] [metric N] [[dev] If]
```

**ip**

ip addr (ifconfig)

ip link set dev eth0 up (ifup eth0)

ip addr add 10.0.0.1/24 dev eth0 (ifconfig eth0 10.0.0.1 netmask 255.255.255.0)

ip route add 10.0.0.0/24 via 192.168.0.1 (route add -net 10.0.0.0 netmask 255.255.255.0 gw 192.168.0.1)

ip 使用的网络栈 ifconfig 不支持，所以通过 ip 命令给一个网卡绑定多个 ip，ifconfig 是查看不到的。

### 29 | 网络故障排除命令

ping / traceroute / mtr

```shell
ping www.baidu.com
traceroute www.baidu.com
mtr www.baidu.com
```

nslookup

```shell
nslookup www.baidu.com
```

telnet

```shell
telnet www.baidu.com 80
```

tcpdump

```shell
tcpdump -i eth0 port 80
tcpdump -i eth0 host 10.0.0.1
tcpdump -i eth0 -w /tmp/tcpdump.cap
```

netstat / ss

```shell
netstat -ntpl
ss -ntpl
```

### 30 | 网络管理和配置文件

**SysV & systemd**

建议只使用 1 个：CentOS 6 -> SysV CentOS 7 -> systemd

service network status | start | stop | restart

chkconfig --list network

```shell
chkconfig --list network
network         0:off   1:off   2:on    3:on    4:on    5:on    6:off
# 关闭 SysV
chkconfig --level 2345 network off
```

systemctl list-unit-files NetworkManager.service

systemctl start | stop | restart NetworkManager.service

systemctl enable | disable NetworkManager.service 随着开机启动 / 不启动

**ifcfg-eth0 & /etc/rc.local & /etc/hosts**

/etc/sysconfig/network-scripts/ifcfg-eth0

```shell
# 动态 IP
DEVICE=eth0
BOOTPROTO=dhcp
ONBOOT=yes
# 静态 IP
BOOTPROTO=none
IPADDR=10.211.55.3
NETMASK=255.255.255.0
GATEWAY=10.211.55.1
DNS1=114.114.114.114
DNS2=
DNS3=
```

/etc/hosts

```shell
hostname
# 修改 hostname
hostname <hostname>
hostnamectl set-hostname <hostname>

vim /etc/hosts
127.0.0.1 <hostname>

reboot
```

### 31 | 软件包管理器的使用

CentOS、RedHat 使用 yum 包管理器，软件安装包格式为 rpm

Debian、Ubuntu 使用 apt 包管理器，软件安装包格式为 deb

Windows scoop / macOS Homebrew

### 32 | 使用 rpm 命令安装软件包

vim-common-7.4.10-5.el7.x86_64.rpm

vim-common 软件名称

7.4.10-5 软件版本，5 表示此 rpm 包是第几次生成的

el7 系统版本

x86_64 平台

**rpm**

mount /dev/sr0 /mnt 挂载

umount /mnt 或者 umount /dev/sr0 卸载

```shell
rpm -qa | more
rpm -qa | grep vim
rpm -q vim-common
rpm -e vim-common
# 考虑依赖关系
rpm -i vim-common-7.4.10-5.el7.x86_64.rpm
rpm -ql vim-common
```

### 33 | 使用 yum 包管理器安装软件包

**CentOS yum 源**

http://mirror.centos.org/centos/7/

https://mirrors.aliyun.com/centos/7/

**yum 配置文件**

修改 repo：/etc/yum.repos.d/CentOS-Base.repo

替换 repo：wget -O /etc/yum.repos.d/CentOS-Base.repo https://mirrors.aliyun.com/repo/Centos-7.repo

```shell
mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
wget -O /etc/yum.repos.d/CentOS-Base.repo https://mirrors.aliyun.com/repo/Centos-7.repo
yum makecache
```

**yum 命令**

install / remove / list / update

```shell
yum remove vim*
yum update
```

保存 yum 安装过程中下载的包：修改 /etc/yum.conf 配置文件，将 keepcache=0 改为 keepcache=1。

\ 被称作续行符，也就是原本在同一行中的命令，为了美观写为了多行。

### 34 | 通过源代码编译安装软件包

```shell
yum install pcre-devel -y
yum install openssl-devel -y
wget https://openresty.org/download/openresty-1.15.8.1.tar.gz
tar -zxf openresty-1.15.8.1.tar.gz
cd openresty-1.15.8.1
./configure --prefix=/usr/local/openresty
gmake -j2
gmake install
# make -j2
# make install
```

### 35 | 如何进行内核升级

**rpm**

```shell
# 查看内核版本
uname -r
# epel 库
yum install epel-release -y
# 最新版本内核
yum install kernel
# 指定版本内核
yum install kernel 3.10.0
# 更新内核 & 软件
yum update
```

**源代码编译**

```shell
# 依赖包
yum install gcc gcc-c++ make ncurses-devel openssl-devel elfutils-libelf-devel flex bison -y
# 下载 & 解压缩
# https://www.kernel.org/
# https://mirrors.aliyun.com/linux-kernel/
wget https://mirrors.aliyun.com/linux-kernel/v5.x/linux-5.1.14.tar.xz
tar -xvf linux-5.1.14.tar.xz -C /usr/src/kernels
# 配置内核编译参数
cd /usr/src/kernels/linux-5.1.14
make menuconfig | allyesconfig | allnoconfig
vim .config
# 使用当前系统内核配置
cp /boot/config-3.10.0-957.21.3.el7.x86_64 /usr/src/kernels/linux-5.1.14/.config
# 查看 cpu
lscpu
# 编译
make -j2 all
# 安装内核
make modules_install
make install
reboot
```

### 36 | grub 配置文件介绍

/etc/default/grub & /etc/grub.d/

grub2-mkconfig -o /boot/grub2/grub.cfg

```shell
# 修改默认引导内核
grub2-editenv list
grep ^menu /boot/grub2/grub.cfg
grub2-set-default 0
reboot
```

```shell
# DEBUG 内核启动
vim /etc/default/grub
在 GRUB_CMDLINE_LINUX 删除 rhgb quiet
```

```shell
# 重置 root 密码
press 'e' to edit the selected item
linux16 ... rd.break
ctrl + x
# 重新挂载 /sysroot
mount -o remount,rw /sysroot
# 根目录
chroot /sysroot
echo 123 | passwd --stdin root
# 关闭 SELinux
vim /etc/selinux/config
SELINUX=disabled
# 退回到虚拟根目录
exit
reboot
```

### 37 | 使用 ps 和 top 命令查看进程

运行中的程序，从程序开始运行到终止的整个生命周期是可管理的。

正常终止 / 异常终止

**ps**

```shell
# to see every process on the system
ps -e
ps -ef
# to get info about threads
ps -eLf
ID        PID  PPID   LWP  C NLWP STIME TTY          TIME CMD
# LWP 该进程拥有的线程数
# TTY 终端
```

终端，泛指一切能控制计算机的输入接口，包括串口线的硬件终端，也包括类似 Windows 的图形界面，默认运行 Linux 服务器的字符界面。而在 Linux 字符界面上，软件终端又分成标准终端设备 tty1-tty6 和虚拟终端 pts 。我们使用 ssh 连接的终端，和在图形界面打开的终端都属于虚拟终端，它们和 tty 设备的区别就是没有设备编号，所以叫做“虚拟”终端。

**pstree**

**top**

```shell
%Cpu0  :  1.7 us,  1.7 sy,  0.0 ni, 96.6 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
# us 用户态进程占用 CPU 时间百分比
# sy 内核占用 CPU 时间百分比
# id 空闲 CPU 时间百分比
# wa 等待 I/O 的 CPU 时间百分比
# 按键盘数字 "1"，可监控每个逻辑 CPU 的状况
KiB Mem :   498640 total,    26380 free,   123964 used,   348296 buff/cache
KiB Swap:        0 total,        0 free,        0 used.   347680 avail Mem
# buff/cache 内核缓存
PID USER      PR  NI    VIRT    RES    SHR S %CPU %MEM     TIME+ COMMAND
# TIME+ 该进程启动后占用的总的 CPU 时间
# NI nice
```

-p monitor only processes with specified process IDs

"E" 切换 KB / MB / GB

### 38 | 进程的控制与进程之间的关系

**调整优先级**

nice 范围从 -20 到 19，值越小优先级越高，抢占的资源就越多

renice 重新设置优先级

```shell
# nice 默认为 0
nice -n 10 ./x.sh
24370
renice -n 15 24370
```

**进程的作业控制**

jobs / & 符号

```shell
# 后台运行
./x.sh &
24667
# display status of jobs
jobs
[1]+  Running                 ./a.sh &
# move job to the foreground
fg 1
# ctrl + z 挂起暂停
[1]+  Stopped                 ./a.sh
# 恢复运行
jobs
# 前台运行
# fg 1
# 后台运行
bg 1
```

### 39 | 进程的通信方式与信号：kill 命令

进程的通信方式：管道 & 信号。

终端用户输入中断命令，通过信号机制停止一个程序的运行。

**kill**

```shell
kill -l
 1) SIGHUP       2) SIGINT       3) SIGQUIT      4) SIGILL       5) SIGTRAP
 6) SIGABRT      7) SIGBUS       8) SIGFPE       9) SIGKILL     10) SIGUSR1
11) SIGSEGV     12) SIGUSR2     13) SIGPIPE     14) SIGALRM     15) SIGTERM
16) SIGSTKFLT   17) SIGCHLD     18) SIGCONT     19) SIGSTOP     20) SIGTSTP
21) SIGTTIN     22) SIGTTOU     23) SIGURG      24) SIGXCPU     25) SIGXFSZ
26) SIGVTALRM   27) SIGPROF     28) SIGWINCH    29) SIGIO       30) SIGPWR
31) SIGSYS      34) SIGRTMIN    35) SIGRTMIN+1  36) SIGRTMIN+2  37) SIGRTMIN+3
38) SIGRTMIN+4  39) SIGRTMIN+5  40) SIGRTMIN+6  41) SIGRTMIN+7  42) SIGRTMIN+8
43) SIGRTMIN+9  44) SIGRTMIN+10 45) SIGRTMIN+11 46) SIGRTMIN+12 47) SIGRTMIN+13
48) SIGRTMIN+14 49) SIGRTMIN+15 50) SIGRTMAX-14 51) SIGRTMAX-13 52) SIGRTMAX-12
53) SIGRTMAX-11 54) SIGRTMAX-10 55) SIGRTMAX-9  56) SIGRTMAX-8  57) SIGRTMAX-7
58) SIGRTMAX-6  59) SIGRTMAX-5  60) SIGRTMAX-4  61) SIGRTMAX-3  62) SIGRTMAX-2
63) SIGRTMAX-1  64) SIGRTMAX
```

ctrl + c 表示 2) SIGINT

kill -9 \<PID\> 立即结束程序

### 40 | 守护进程

使用 nohup 与 & 符号配合

```shell
# nohup 命令使进程忽略 hangup（挂起）信号
# 关闭终端进程仍然运行
nohup tail -f /var/log/messages &
# 关闭终端后进程的父进程是 1
ps -ef | grep tail
root      1744     1  0 15:24 ?        00:00:00 tail -f /var/log/messages
# 位于内存中的伪文件系统，该目录下保存的不是真正的文件和目录，而是一些“运行时”信息
cd /proc/1744
# 进程的运行目录
ls -l cwd
lrwxrwxrwx 1 root root 0 Dec 28 15:24 cwd -> /root
# 进程打开的每一个文件的文件描述符
ls -l fd
total 0
l-wx------ 1 root root 64 Dec 28 15:25 0 -> /dev/null
l-wx------ 1 root root 64 Dec 28 15:25 1 -> /root/nohup.out
l-wx------ 1 root root 64 Dec 28 15:25 2 -> /root/nohup.out
lr-x------ 1 root root 64 Dec 28 15:25 3 -> /var/log/messages
lr-x------ 1 root root 64 Dec 28 15:25 4 -> anon_inode:inotify
```

daemon 进程，无终端启动、运行进程

```shell
ps -ef | grep sshd
root      1071     1  0 Dec25 ?        00:00:00 /usr/sbin/sshd -D
cd /proc/1071
ls -l cwd
lrwxrwxrwx 1 root root 0 Dec 28 03:52 cwd -> /
ls -l fd
total 0
lr-x------ 1 root root 64 Dec 25 20:39 0 -> /dev/null
lrwx------ 1 root root 64 Dec 25 20:39 1 -> socket:[16554]
lrwx------ 1 root root 64 Dec 25 20:39 2 -> socket:[16554]
lrwx------ 1 root root 64 Dec 25 20:39 3 -> socket:[16561]
```

### 41 | screen 命令和系统日志

**screen**

screen 进入 screen 环境

ctrl + a & d 退出（detached）screen 环境

screen -ls 查看 screen 会话

screen -r sessionid 恢复会话

ctrl + c & exit 退出

**系统日志**

/var/log/messages

/var/log/dmesg

/var/log/secure

/var/log/cron

### 42 | 服务管理工具 systemctl

服务（提供常见功能的守护进程）集中管理工具

**service**

/etc/init.d/

```shell
# init N (0 - 6) 控制不同的级别启动不同的服务
chkconfig --list
netconsole      0:off   1:off   2:off   3:off   4:off   5:off   6:off
network         0:off   1:off   2:on    3:on    4:on    5:on    6:off
```

**systemctl**

/usr/lib/systemd/system/

```shell
# 级别
ls -l runlevel*.target
lrwxrwxrwx 1 root root 15 Jul 11  2019 runlevel0.target -> poweroff.target
lrwxrwxrwx 1 root root 13 Jul 11  2019 runlevel1.target -> rescue.target
lrwxrwxrwx 1 root root 17 Jul 11  2019 runlevel2.target -> multi-user.target
lrwxrwxrwx 1 root root 17 Jul 11  2019 runlevel3.target -> multi-user.target
lrwxrwxrwx 1 root root 17 Jul 11  2019 runlevel4.target -> multi-user.target
lrwxrwxrwx 1 root root 16 Jul 11  2019 runlevel5.target -> graphical.target
lrwxrwxrwx 1 root root 13 Jul 11  2019 runlevel6.target -> reboot.target
# 当前级别
systemctl get-default
# 重置级别
systemctl set-default multi-user.target
```

```shell
vim sshd.service

[Unit]
...
After=network.target sshd-keygen.service
...
[Install]
WantedBy=multi-user.target
```

### 43 | SELinux 简介

MAC（强制访问控制）与 DAC（自主访问控制）

```shell
# 查看 SELinux 状态
getenforce
# enforcing / permissive / disabled
vim /etc/selinux/config
# LABEL
ps -Z
id -Z
ls -Z
```

### 44 | 内存与磁盘管理

### 45 | 内存查看命令

free / top

```shell
free -m
free -g
```

> Basically, “buff/cache” counts memory used for data that’s on disk or should end up there soon, and as a result is potentially usable (the corresponding memory can be made available immediately, if it hasn’t been modified since it was read, or given enough time, if it has); “available” measures the amount of memory which can be allocated and used without causing more swapping.

> Swap is **a space on a disk that is used when the amount of physical RAM memory is full**. When a Linux system runs out of RAM, inactive pages are moved from the RAM to the swap space.

杀进程是根据 /proc/\<进程 id\>/oom_score 和 oom_adj 文件来确定的。

出现 oom kill 的时机是 malloc() 无法获得资源的时候，选择 kill 进程时会选择内存占用高、存活时间短的进程，即多释放内存，少杀无辜进程。

### 46 | 磁盘分区和文件大小查看

fdisk / df / du

```shell
# parted -l
fdisk -l
Disk /dev/vda: 21.5 GB, 21474836480 bytes, 41943040 sectors
...
Partition Table: msdos
...
   Device Boot      Start         End      Blocks   Id  System
/dev/vda1   *        2048    41943039    20970496   83  Linux

ls -l /dev/vd*
brw-rw---- 1 root disk 253, 0 Dec 25 16:06 /dev/vda
brw-rw---- 1 root disk 253, 1 Dec 25 16:06 /dev/vda1

df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/vda1        20G  4.8G   14G  26% /

# dd convert and copy a file
dd if=/dev/zero bs=4M count=10 of=afile
# 空洞文件（kvm xen 虚拟化工具）
dd if=/dev/zero bs=4M count=10 seek=20 of=bfile
# ls
ls -lh bfile
-rw-r--r-- 1 root root 120M Dec 28 19:09 bfile
# 实际占用空间
du -h bfile
40M     bfile
```

**msdos**

在早期的 Windows 引导启动过程中，负责引导和启动的数据放在磁盘的第一个扇区中，众做周知第一个扇区大小是 512 字节，前 446 字节用于主引导记录（MBR），64 字节用于分区表，后面的 55 AA 放在最后做校验位。Linux 为了兼容 Windows 使用了这种分区记录方式，即：msdos 分区表。

msdos 方式分区表空间有限，既要保证分区数量充足，又要记录分区使用空间，就导致硬盘如果大于 2T 无法记录的问题（gpt / LBA），因此要使用一种新的方法来引导，即 UEFI + GPT 方式。

UEFI 方式引导要修改 BIOS，GPT 方式要在 parted 命令使用 mklabel gpt 进行更改。

### 47 | 文件系统管理

**常见文件系统**

ext4 / xfs / NTFS（需安装额外软件）

**ext4**

超级块 / 超级块副本 / inode / 数据块（datablock）

df 读取 超级块

inode 记录文件编号（ls -i）、大小、权限 etc. / 文件名记录在父目录 inode 中 => 所以，文件的 r 权限和目录的 r 权限不同

ls 读取 inode 中文件大小信息，du 统计 datablock 个数

### 48 | inode 和数据块操作

```shell
# 默认数据块 4K
touch xfile
echo xxx > xfile
ls -li xfile
931094 -rw-r--r-- 1 root root 4 Dec 28 23:20 xfile
du -h xfile
4.0K    xfile
# cp 创建了不同的文件
cp xfile xxfile
931094 -rw-r--r-- 1 root root 4 Dec 28 23:20 xfile
931095 -rw-r--r-- 1 root root 4 Dec 28 23:26 xxfile
# mv 仅修改父目录记录的文件名
# 移动速度的快慢取决于是否跨分区
mv xxfile xxxfile
931095 -rw-r--r-- 1 root root 4 Dec 28 23:26 xxxfile
# vim 修改 inode 和 datablock (.swp)
# echo 仅修改 datablock
# rm 断开文件名和 inode 链接
# 硬链接 不能跨文件系统
ls -li xfile
931094 -rw-r--r-- 1 root root 4 Dec 28 23:20 xfile
ln xfile yfile
# 2 表示硬链接个数
931094 -rw-r--r-- 2 root root 4 Dec 28 23:20 xfile
931094 -rw-r--r-- 2 root root 4 Dec 28 23:20 yfile
# 软链接（符号链接）inode 不同，可跨不同的文件系统（分区）
ln -s xfile zfile
931089 lrwxrwxrwx 1 root root 5 Dec 28 23:46 zfile -> xfile
# 对软链接 zfile 的修改，会传递到 xfile
chmod 755 zfile
931094 -rwxr-xr-x 2 root root 4 Dec 28 23:20 xfile
```

```shell
# facl 文件访问控制列表
getfacl xfile
setfacl -m u:user1:w xfile
setfacl -m g:group1:r xfile
setfacl -x u:user1 xfile
setfacl -x g:group1 xfile
```

### 49 | 分区和挂载

```shell
# 分区
fdisk /dev/vdb
# n add a new partition
# p print the partition table
# w write table to disk and exit
Disk /dev/vdb: 21.5 GB, 21474836480 bytes, 41943040 sectors
...
   Device Boot      Start         End      Blocks   Id  System
/dev/vdb1            2048    41943039    20970496   83  Linux
# 格式化（文件系统）
# mkfs.btrfs   mkfs.cramfs  mkfs.ext2    mkfs.ext3    mkfs.ext4    mkfs.minix   mkfs.xfs
mkfs.ext4 /dev/vdb1
```

```shell
# 挂载
mkdir /mnt/vdb1
mount /dev/vdb1 /mnt/vdb1

mount
/dev/vda1 on / type ext4 (rw,relatime,data=ordered)
/dev/vdb1 on /mnt/vdb1 type ext4 (rw,relatime,data=ordered)

df -h
/dev/vda1        20G  4.9G   14G  26% /
/dev/vdb1        20G   45M   19G   1% /mnt/vdb1

# /etc/fstab
vim /etc/fstab
/dev/vdb1 /mnt/vdb1 ext4 defaults 0 0
```

### 50 | 分区和挂载磁盘配额

```shell
umount /dev/vdb1
fdisk /dev/vdb
# d & n
mkfs.xfs -f /dev/vdb1
mkdir -p /mnt/vdb1
mount -o uquota,gquota /dev/vdb1 /mnt/vdb1
chmod 1777 /mnt/vdb1
# 查看
xfs_quota -x -c 'report -ugibh' /mnt/vdb1
# 设置
xfs_quota -x -c 'limit -u isoft=5 ihard=10 user1' /mnt/vdb1
# 测试
su - user1
touch 1 2 3 4 5 6 7 8 9 10
touch 11
touch: cannot touch ‘11’: Disk quota exceeded
```

### 51 | 交换分区 swap 的查看与创建

**mkswap & swapon**

```shell
free -m
              total        used        free      shared  buff/cache   available
Mem:            486         123         114           0         248         336
Swap:             0           0           0
# 分区
fdisk /dev/vdb
# 格式化
mkswap /dev/vdb1
# 开启
swapon /dev/vdb1
# /etc/fstab
/dev/vdb1 swap swap defaults 0 0
free -m
              total        used        free      shared  buff/cache   available
Mem:            486         139          98           0         249         321
Swap:         20478           0       20478
# 关闭
swapoff /dev/vdb1
```

**使用文件制作交换分区**

```shell
dd if=/dev/zero bs=4M count=1024 of=/swapfile
mkswap /swapfile
chmod 600 /swapfile
swapon /swapfile
# /etc/fstab
/swapfile swap swap defaults 0 0
```

### 52 | 软件 RAID 的使用

RAID 0 / RAID 1 / RAID 5 / RAID 10

**RAID 卡**

**软件 RAID**

```shell
# 分区 /dev/vdb1 & /dev/vdc1
yum install mdadm -y
# RAID 1
mdadm -C /dev/md0 -a yes -l1 -n2 /dev/vd[b,c]1
# 查看
mdadm -D /dev/md0
# /etc/mdadm.conf
echo DEVICE /dev/vd[b,c]1 >> /etc/mdadm.conf
mdadm -Evs >> /etc/mdadm.conf
# 格式化（文件系统）
mkfs.xfs /dev/md0
# 挂载
mkdir /mnt/md0
mount /dev/md0 /mnt/md0
# 破坏磁盘
dd if=/dev/zero of=/dev/vdc bs=4M count=1
# 禁用 RAID
umount /dev/md0
mdadm --stop /dev/md0
```

### 53 | 逻辑卷 LVM 的用途与创建

```shell
# 破坏 RAID 超级块
dd if=/dev/zero of=/dev/vdb1 bs=1M count=1
dd if=/dev/zero of=/dev/vdc1 bs=1M count=1
# 分区 /dev/vdb1 /dev/vdc1
# PV / VG / LV 实现了动态扩展，xfs 实现了以文件方式进行操作
# xfs 既可以在分区上，也可以在 LV 上
# 物理卷（PV Physical Volume）
yum reinstall lvm2
pvcreate /dev/vd[b,c]1
pvs
# 卷组（VG Volume Group）
vgcreate vg1 /dev/vdb1
vgs
# 逻辑卷（LV Logical Volume）
lvcreate -L 100M -n lv1 vg1
lvs
# 格式化（文件系统）
mkfs.xfs /dev/vg1/lv1
# 挂载
mkdir /mnt/lv1
mount /dev/vg1/lv1 /mnt/lv1
```

```shell
# 扩展
vgextend vg1 /dev/vdc1
lvextend -L +10G /dev/vg1/lv1
xfs_growfs /dev/vg1/lv1
df -h
```

### 54 | 系统综合状态查看命令 sar 以及第三方命令

**sar**

**iftop**

yum install iftop -y

iftop -P

## 第四章 Shell 篇

### 55 | 什么是 Shell

Shell 是命令解释器，用于解释用户对操作系统的操作。

```shell
cat /etc/shells
/bin/sh
/bin/bash
/usr/bin/sh
/usr/bin/bash
```

CentOS 7 默认使用的 Shell 是 bash。

### 56 | Linux 的启动过程

BIOS / MBR / BootLoader (grub) / kernel / systemd / 系统初始化 / shell

**BIOS**

选择引导介质

**MBR**

dd if=/dev/vda of=mbr.bin bs=446 count=1

dd if=/dev/vda of=mbr.bin bs=512 count=1

hexdump -C mbr.bin

55 aa

**grub**

选择内核版本

/boot/grub2/

grub2-editenv list / uname -r

**init & systemd**

ls -l /etc/rc.d/

ls -l /etc/systemd/system/ & ls -l /usr/lib/systemd/system/

### 57 | Shell 脚本的格式

Unix 的哲学：一条命令只做一件事

为了组合命令和多次执行，使用脚本文件来保存需要执行的命令

赋予该文件执行权限（chmod u+rx filename）

Sha-Bang #!/bin/bash

### 58 | 脚本不同执行方式的影响

bash ./filename.sh bash 解释脚本，产生子进程

./filename.sh Sha-Bang 解释脚本，产生子进程，必须有可执行权限

source ./filename.sh 不产生子进程

. ./filename.sh 不产生子进程

**内建命令和外部命令**

内建命令不会创建子进程；内建命令对当前 Shell 生效

### 59 | 管道

管道和信号一样，也是进程通信的方式之一

匿名管道（管道符）是 Shell 编程经常用到的通信工具

管道符 “|” 将前一个命令执行的结果传递给后面的命令

> 外部命令会产生子进程，管道符同样会产生子进程。内部命令在 shell 当前进程运行，不会产生子进程。
>
> 在管道符两端放置内部命令，相当于打开了新的子 shell。内部命令执行结束之后，子 shell 也会跟着一起结束。

cat | ps -f => cat 子进程阻塞

### 60 | 重定向

"<" 输入重定向符号

">" ">>" "2>" "&>" 输出重定向符号

```shell
wc -l < /etc/passwd
echo xxx > x.txt	
```

[How does "cat << EOF" work in bash?](https://stackoverflow.com/questions/2500436/how-does-cat-eof-work-in-bash)

**Assign multi-line string to a shell variable**

```shell
sql=$(cat <<EOF
SELECT foo, bar FROM db
WHERE foo='baz'
EOF
)
```

**Pass multi-line string to a file in Bash**

```shell
cat <<EOF > /root/print.sh
#!/bin/bash
echo \$PWD
echo $PWD
EOF
```

**Pass multi-line string to a pipe in Bash**

```shell
cat <<EOF | grep 'b' | tee /root/b.txt
foo
bar
baz
EOF
```

> Linux 系统规定，一个进程执行时会默认打开标准输入、标准输出、错误输出三个文件描述符，当程序作者发现程序出现语法错误，或者自定义一些逻辑错误时，会把错误提示输出到 2 号文件描述符，也就是错误输出描述符中。

du -sh * > /tmp/x.log 2> &1

du -sh * &> /tmp/x.log

把错误输出重定向到文件描述符 1，即标准输出，再将标准输出重新定向到 x.log 文件。

### 61 | 变量赋值

变量名=变量值

x=123

使用 let

let x=12+3

将命令赋值给变量

l=ls

将命令结果赋值给变量，使用 $() 或 ``

lsetc=$(ls -l /etc)

变量有空格等特殊字符可以包含在 “” 或 '' 中

x='hello "bash"'

### 62 | 变量引用及作用范围

${变量名}

${变量名} 在部分情况下可以省略为 $变量名

echo ${变量名}other

**作用范围**

默认为当前 shell 进程

```shell
x=1
# 子进程
bash
echo $x
x=2
# 父进程
exit
# 1
echo $x
```

```shell
# 子进程获取父进程的变量
export x
# 子进程
bash
# 1
echo $x
```

export 变量名=变量值

unset 变量名

### 63 | 环境变量、预定义变量与位置变量

```shell
# 环境变量 export
env
# 命令搜索路径
echo $PATH
PATH=$PATH:/root
echo $PS1
# 预定义变量 & 位置变量
set
# 上一条命令是否正确执行
echo $?
# 当前进程 PID
echo $$
# 当前进程名称
echo $0
# 位置参数
$1
# 变量替换，规避 $2 为空值，默认为 _
${2-_}
${10}
```

```shell
#!/bin/bash

echo $$
echo $0

# x.sh
bash x.sh
# ./x.sh
./x.sh
# -bash
source x.sh
# -bash
. ./x.sh
```

### 64 | 环境变量配置文件

**执行顺序**

/etc/profile

/etc/profile.d/

~/.bash_profile

~/.bashrc

/etc/bashrc 

**区别**

**/etc/** 全部用户；**~/** 特有用户

Login Shell (su - username) & Non-Login Shell (su username)

Non-Login Shell 仅执行 bashrc

**即刻生效**

**source** /etc/bashrc

### 65 | 数组

```shell
IPTS=( 10.0.0.1 10.0.0.2 10.0.0.3 )
# 10.0.0.1 10.0.0.2 10.0.0.3
echo ${IPTS[@]}
# 10.0.0.1
echo ${IPTS[0]}
# 3
echo ${#IPTS[@]}
```

### 66 | 转义和引用

\# 注释

; 分号

\ 转义符号 \n \r \t \\$ \\" \\\ 

" 和 ' 引号

```shell
x=xxx
# 不完全引用 xxx
echo "$x"
# 完全引用 $x
echo '$x'
```

### 67 | 运算符

```shell
# 4+5
num=4+5
# 9
num=`expr 4 + 5`
# 9 (()) 同 let
(( num=4+5 ))
# 10
(( num++ ))
```

仅支持整数运算，不支持浮点数运算

### 68 | 特殊字符大全

**引号**

" 完全引用

' 不完全引用

` 执行命令

**括号**

() (()) $() 圆括号

```shell
# 产生子 shell
( x=xxx )
# 数组
IPS=( 10.0.0.1 10.0.0.2 10.0.0.3 )
# 算数运算
# let 等价 (())
echo $(( 4+5 ))
# 将命令结果赋值给变量
x=$(ls -l)
```

[] [[]] 方括号

```shell
# test 等价 []
[ 5 -gt 4 ]
# 0
echo $?
# [] 扩展写法 [[]]，测试表达式
[[ 5 > 4]]
# 0
echo $?
```

< > 尖括号

```shell
# 输入、输出重定向
ls -l > ls.txt
```

{} 花括号

```shell
# 输出范围 0 1 2 3 4 5 6 7 8 9
echo {0..9}
# 文件复制
cp /etc/passwd{,.bak}
```

**运算符号和逻辑符号**

\+ - * / % 算数运算符

\> < = 比较运算符

&& || ! 逻辑运算符

```shell
(( 5 > 4 && 6 > 5 ))
(( ! 5 > 4 ))
```

**转义符号**

\

**其他符号**

\# 注释符

; 命令分隔符 ifdown eth0 ; ifup eth0 / case 分支 ;;

: 空指令

. 等价 source

~ 家目录

, 分隔目录，如 cp /etc/passwd{,.bak}

\* 通配符

? 条件测试 或 通配符

$ 取值符号

| 管道符

& 后台运行

  空格 echo {0..9} / echo { 0..9 }

### 69 | test 比较

**exit** returns the status of last command that is executed

exit 10

$? 判断前一个进程是否正常退出

**test** check file types and compare values

```shell
test -f /etc/passwd
[ -d /etc/ ]
[ -e /etc/ ]
[ 5 -gt 4 ]
[[ 5 > 4 ]]
[ "abc" = "ABC" ]
```

### 70 | if 判断的使用

```shell
if [ $UID = 0 ]; then echo "root user"; fi
if pwd; then echo "pwd running"; fi
```

### 71 | if-else 判断的使用

```shell
#!/bin/bash

if [ $USER = root ]; then
	echo "root user"
else
	echo "other user"
	echo $UID
fi
```

```shell
#!/bin/bash

if [ $USER = root ]; then
	echo "root user"
elif [ $USER = admin ]; then
	echo "it's admin"
else
	echo "other user"
fi
```

### 72 | 嵌套 if 的使用

```shell
#!/bin/bash

if [ $UID = 0 ]; then
	echo "have permission"
	if [ -x /tmp/x.sh ]; then
		echo "start running"
		/tmp/x.sh
	fi
else
	echo "permission denied"
fi
```

### 73 | case 分支

```shell
#!/bin/bash

case $1 in
"start" | "START")
	echo "$0 start..."
	;;

"stop" | "STOP")
	echo "$0 stop..."
	;;

"restart" | "RESTART" | "reload" | "RELOAD")
	echo "$0 restart|reload..."
	;;

*)
	echo "usage: $0 {start|stop|restart|reload}"
	;;
esac
```

### 74 | for 的基本使用

```shell
for i in {1..9}; do echo $i; done
```

```shell
#/bin/bash

for file in $(ls *.mp3); do
	mv $file $(basename $file .mp3).mp4
done
```

### 75 | C 语言风格的 for

```shell
for ((i = 0; i <= 10; i++)); do echo $i; done
```

### 76 | while 循环和 until 循环

```shell
while [ $x -lt 10 ]; do
	echo $x
	((x++))
done
```

```shell
until [ $x -gt 10 ]; do
	echo $x
	((x++))
done
```

```shell
# 死循环
while :; do echo "loop"; done
```

### 77 | 循环的嵌套和 break、continue 语句

```shell
for script in /etc/profile.d/*.sh; do if [ -x $script ]; then . $script; fi; done
```

```shell
# 1 2 3 4
for num in {1..9}; do
	if [ $num -eq 5 ]; then break; fi
	echo $num
done
```

```shell
# 1 2 3 4 6 7 8 9
for num in {1..9}; do
	if [ $num -eq 5 ]; then continue; fi
	echo $num
done
```

### 78 | 使用循环处理位置参数

$1 $2 ... ${10} 命令行参数

$0 脚本名称

$* 和 $@ 所有位置参数

$# 位置参数的数量

```shell
#!/bin/bash

for arg in $*; do
	if [ "$arg" = "help" ]; then
		echo $arg $arg
	fi
done
```

```shell
#!/bin/bash

while [ $# -ge 1 ]; do
	if [ "$1" = "help" ]; then
		echo $1 $1
	fi
	# 参数左移
	shift
done
```

### 79 | 自定义函数

```shell
function cdls() {
	cd $1
	ls -l
}

# cdls /tmp/
```

```shell
#!/bin/bash

checkpid() {
	local pid
	for pid in $*; do
		[ -d "/proc/$pid" ] && return 0
	done
	return 1
}

# source checkpid.sh
# checkpid 0
# echo $?
```

### 80 | 系统函数库介绍

/etc/init.d/functions

source /etc/init.d/functions

### 81 | 脚本资源控制

ulimit -a shell resource limits

fork 炸弹 .(){.|.&}; .

### 82 | 信号

kill 默认发送 15 号信号

ctrl + c 发送 2 号信号

kill -9 9 号信号不可阻塞

```shell
#!/bin/bash

trap "echo SIG 15" 15
trap "echo SIG 2" 2

echo $$

while :; do
	:
done

### kill -15 <PID>
### ctrl + c
### kill -9 <PID>
```

### 83 | 一次性计划任务

**at** executes commands at a specified time

```shell
at 10:24
# 命令执行路径
# 无标准输入、输出
at> echo $(date) > /tmp/date.txt
# ctrl + d
at> <EOT>
```

**atq** lists the user's pending jobs

### 84 | 周期性计划任务

**crontab**

\-l displays the current crontab on standard output

\-e edits the current crontab

配置格式：分钟 小时 日期 月份 星期 执行的命令

```shell
# crontab -e
* * * * * /usr/bin/date >> /tmp/minute.txt
* * * * * for i in `seq 60`; do /usr/bin/date; sleep 1; done >> /tmp/second.txt
```

cat /var/spool/cron/\<username\>

tail -f /var/log/cron

### 85 | 为脚本加锁

**anacontab** 延时计划任务

延时计划任务会查询计划任务，哪些任务在该执行的时间点没执行？需要在开机多久再补充执行一次？

/etc/cron.d/0hourly

/etc/anacrontab

**flock** 锁文件

flock -xn "/tmp/f.lock" -c "/root/x.sh"

## 第五章 文本操作篇

### 86 | 元字符介绍

**shell 通配符**

\* ?  [] {}

[命令行通配符教程](http://www.ruanyifeng.com/blog/2018/09/bash-wildcards.html)

**元字符**

. * [] ^ $ \

[正则表达式 - 元字符](https://www.runoob.com/regexp/regexp-metachar.html)

```shell
# # Root password
grep password /root/anaconda-ks.cfg
# auth --enableshadow --passalgo=sha512
# # Root password
grep pass.... /root/anaconda-ks.cfg
# # Root password
grep pass....$ /root/anaconda-ks.cfg
# auth --enableshadow --passalgo=sha512
# # Root password
grep pass.* /root/anaconda-ks.cfg
# [Hh]ello
# # ...
grep ^# /root/anaconda-ks.cfg
# V9N.V9Bg
grep "\." /root/anaconda-ks.cfg
# auth
# #
grep pass.* /root/anaconda-ks.cfg | cut -d " " -f 1
# 42 /sbin/nologin
cut -d ":" -f 7 /etc/passwd | sort | uniq -c | sort -r
```

### 87 | find 演示

**扩展元字符**

\+ ? |

**find**

find 默认使用通配符

```shell
# /etc/pam.d/passwd
# /etc/passwd
find /etc/ -name passwd
# 通配符
# /etc/openldap/certs/password
# /etc/pam.d/password-auth-ac
# /etc/pam.d/password-auth
# /etc/pam.d/passwd
# /etc/selinux/targeted/active/modules/100/passenger
# /etc/passwd
# /etc/passwd-
find /etc/ -name pass*
# 正则表达式
# /etc/pam.d/passwd
# /etc/security/opasswd
# /etc/passwd
find /etc/ -type f -regex .*wd
# -mtime file's data was last modified n*24 hours ago
find /etc/ -type f -atime 5 -regex .*wd
# touch /tmp/{1..9}.txt
find /tmp/{1..9}.txt -exec rm -v {} \;
find /tmp/ -regex "\./[1-9]\.txt" -exec rm -v {} \;
```

```shell
LANG=C stat <filename>
```

```shell
# 正则匹配的是路径名称，-name 匹配的是文件或者文件夹名称
find /etc/ -name *wd
find /etc/ -regex .*wd
```

### 88 | sed 和 awk 介绍

sed awk 行编辑器

sed 一般用于对文件内容做替换

awk 一般用于对文本内容进行统计，按需要的格式进行输出

### 89 | sed 替换命令讲解

**sed 的基本工作方式**

将文件以行为单位读取到内存（模式空间）

使用 sed 的每个脚本对该行进行操作

处理完成后输出该行

**替换命令 s**

sed 's/old/new/' filename

sed -e 's/old/new/' -e 's/old/new/' filename ...

sed -i 's/old/new/' 's/old/new/' filename ...

old 正则表达式

sed -r 扩展正则表达式

```shell
# echo a a a > x.txt
# b a a
sed 's/a/b/' x.txt
# b b b
sed 's/a/b/g' x.txt
# echo / / / >> x.txt
# ? / /
sed 's@/@?@' x.txt
# b a a
# ? / /
sed -e 's/a/b/' -e 's@/@?@' x.txt
sed 's/a/b/;s@/@?@' x.txt
# -i 替换原始文件
sed 's/a/b/' x.txt > tmp.txt
sed -i 's/a/b/' x.txt
```

```shell
head -5 /etc/passwd | sed 's/...//'
head -5 /etc/passwd | sed 's/s*bin//'
grep root /etc/passwd | sed 's/^root//'
sed 's/ab*/!/' y.txt
sed -r 's/ab+/!/' y.txt
sed -r 's/ab?/!/' y.txt
# 回调
# echo axyzb > z.txt
# axyzb:axyzb
sed -r 's/(a.*b)/\1:\1/' z.txt
```

### 90 | sed 替换指令加强版

全局替换 / 标志位 / 寻址 / 分组 / sed 脚本文件

```shell
# 标志位
# 全局替换
s/old/new/g
# / 和正则匹配的内容冲突
s@old@new@g
# 替换每行的全部
head -5 /etc/passwd | sed 's/root/*/g'
# 替换每行的第 2 个
head -5 /etc/passwd | sed 's/root/*/2'
# 仅输出替换成功行
# -n 阻止默认输出
# p 打印模式空间的内容
head -5 /etc/passwd | sed -n 's/root/*/p'
# 将替换成功行写入文件
# w 将模式空间的内容写入到文件
head -5 /etc/passwd | sed -n 's/root/*/w /tmp/tmp.txt'
# 寻址（指定范围）
# /正则表达式/s/old/new/
head -5 /etc/passwd | sed '/daemon/s/nologin/*/'
head -5 /etc/passwd | sed '/^bin/s/nologin/*/'
# 行号s/old/new/，行号可以是具体的行，也可以是最后一行 $ 符号，可以使用两个寻址符号
head -5 /etc/passwd | sed '1s/bin/*/'
head -5 /etc/passwd | sed '1,3s/bin/*/'
head -5 /etc/passwd | sed '1,$s/bin/*/'
# 可以混合使用行号和正则地址
head -5 /etc/passwd | sed '/^bin/,$s/nologin/*/'
# 分组
head -5 /etc/passwd | sed '/^bin/{s/bin/*/;s/nologin/*/}'
# 脚本文件
-f
```

### 91 | sed 其他常用命令

```shell
# 删除命令 d
# 删除模式空间的内容，; 后面的指令不会执行
# = 打印行号
sed '/ab/d;=' y.txt
# 追加命令 a，添加到匹配下一行
sed '/ab/a xxx' y.txt 
# 插入命令 i，添加到匹配上一行
sed '/ab/i xxx' y.txt 
# 更改命令 c，替换匹配行
sed '/ab/c xxx' y.txt
# 读取文件 r，追加到匹配行下一行
sed '/ab/r x.txt' y.txt
# 写入文件 w
sed '/ab/w tmp.txt' y.txt
# 退出命令 q
# seq 1 1000000 > lines.txt
# wc -l lines.txt
time sed 10q lines.txt
time sed -n 1,10p lines.txt
```

### 92 | sed 多行模式空间

使用 XML 或 JSON 格式的配置文件，为多行出现

N 将下一行加入到模式空间

D 删除模式空间中的第一个字符到第一个换行符

P 打印模式空间中的第一个字符到第一个换行符

```shell
# hel
# lo
# *
sed 'N;s/hel\nlo/*/' x.txt
# . 匹配换行符
sed 'N;s/hel.lo/*/' x.txt
# cat << EOF > y.txt
# > hell
# > o bash hel
# > lo bash
# > EOF
sed 'N;s/\n//;s/hello bash/hello sed\n/;P;D' y.txt
```

### 93 | 什么是 sed 保持空间

覆盖 / 追加

h H 将模式空间内容存放到保持空间

g G 将保持空间内容取出到模式空间

x 交叉模式空间和保持空间内容

```shell
# 反转
head -6 /etc/passwd | cat -n | tac
cat -n /etc/passwd | head -6 | sed -n '1h;1!G;$!x;$p'
cat -n /etc/passwd | head -6 | sed -n '1!G;h;$p'
cat -n /etc/passwd | head -6 | sed '1!G;h;$!d'
```

### 94 | 认识 awk

awk 用于“比较规范”的文本处理，用于统计数量并输出指定字段

使用 sed 将不规范的文本处理为“比较规范”的文本

**awk 脚本的流程控制**

输入数据前例程 BEGIN{}

主输入循环 {}

所有文件读取完成例程 END{}

### 95 | awk 的字段

每行称作 awk 的记录

使用空格、制表符分隔开的单词称作字段

可以自己指定分隔的字段

**字段的引用**

awk 中使用 $1 $2 ... $n 表示每一个字段

awk 可以使用 -F 选项改变字段分隔符

分隔符可以使用正则表达式

```shell
awk -F "'" '/^menu/{print x++,$2}' /boot/grub2/grub.cfg
```

### 96 | awk 表达式

**赋值操作符**

= ++ -- += -= *= /= %= ^=

**算数操作符**

\+ - * / % ^

**系统变量**

FS 和 OFS 字段分隔符，FS 表示输入的字段分隔符，OFS 表示输出的字段分隔符，默认为空格

```shell
head -5 /etc/passwd | awk -F ':' '{print $1}'
head -5 /etc/passwd | awk 'BEGIN{FS=":"}{print $1}'
head -5 /etc/passwd | awk 'BEGIN{FS=":";OFS=";"}{print $1,$2}'
```

RS 记录分隔符，默认为 \n

```shell
head -5 /etc/passwd | awk 'BEGIN{RS=":"}{print $0}'
```

NR 和 FNR 行数，FNR 区分文件重新计数

```shell
head -5 /etc/passwd | awk '{print NR,$0}'
awk '{print FNR,$0}' /etc/hosts /etc/hosts
```

NF 字段数量，最后一个字段内容可以用 $NF 取出

```shell
head -5 /etc/passwd | awk 'BEGIN{FS=":"}{print NF}'
head -5 /etc/passwd | awk 'BEGIN{FS=":"}{print $NF}'
```

**关系操作符**

< > <= >= == != ~ !~

**布尔操作符**

&& || ! 

### 97 | awk 判断和循环

if while do for

```shell
# cat <<EOF > kpi.txt
# > user1 70 72 74 76 74 72
# > user2 80 82 84 82 80 78
# > user3 60 61 62 63 64 65
# > user4 90 89 88 87 86 85
# > user5 45 60 63 62 61 50
# > EOF
awk '{if($2>=80) print $1}' kpi.txt
awk '{if($2>=80){print $1;print $2}}' kpi.txt
# 每行平均值
awk '{sum=0;for(i=2;i<=NF;i++) sum+=$i;print sum/(NF-1)}' kpi.txt
```

### 98 | awk 数组

```shell
# 全部行平均值
awk '{sum=0;for(i=2;i<=NF;i++) sum+=$i;avg[$1]=sum/(NF-1)}END{for(user in avg) avgsum=avgsum+=avg[user];print avgsum/NR}' kpi.txt
# 保存到文件
vim avg.awk
{sum=0;for(i=2;i<=NF;i++) sum+=$i;avg[$1]=sum/(NF-1)}END{for(user in avg) avgsum=avgsum+=avg[user];print avgsum/NR}
awk -f avg.awk kpi.txt
```

**命令行参数数组**

ARGC ARGV

```shell
vim arg.awk 
BEGIN{for(arg=0;arg<ARGC;arg++) print ARGV[arg];print ARGC}
# awk
# a
# b
# c
# 4 
awk -f arg.awk a b c
```

### 99 | awk 数组功能的使用

```shell
{
sum=0
for(i=2;i<=NF;i++)
  sum+=$i
avg[$1]=sum/(NF-1)

if(avg[$1]>=80)
  score="S"
else if(avg[$1]>=70)
  score="A"
else if(avg[$1]>=60)
  score="B"
else
  score="C"
scores[score]++
print $1,avg[$1],score
}
END{
for(user in avg)
  avg_sum+=avg[user]
avg_avg=avg_sum/NR
print "average",avg_avg

for(user in avg)
  if(avg[user]>avg_avg)
    above++
  else
    below++
print "above",above
print "below",below

print "S",scores["S"]
print "A",scores["A"]
print "B",scores["B"]
print "C",scores["C"]
}
```

### 100 | awk 函数

**算数函数**

sin() cos()

int()

rand() srand()

```shell
awk 'BEGIN{pi=3.14;print int(pi)}'
awk 'BEGIN{srand();print rand()}'
```

**字符串函数**

gsub(r,s,t) index(s,t) length(s) match(s,r) split(s,a,sep) sub(r,s,t) substr(s,p,n)

**自定义函数**

```shell
awk 'function f(){return 0} BEGIN{print f()}'
awk 'function double(str){return str str} BEGIN{print double("awk")}'
```

## 第六章 服务管理篇

### 101 | 防火墙概述

**软件**、硬件防火墙

**包过滤**、应用层防火墙

CentOS 6 默认防火墙 iptables

CentOS 7 默认防火墙 firewallD

**iptables 表和链**

规则表 filter nat mangle raw

规则链 INPUT OUTPUT FORWARD PREROUTING POSTROUTING

### 102 | iptables 规则的基本使用

iptables -t 规则表 命令 规则链 规则

```shell
# -n 不解析域名
# -v 详细
iptables -t filter -vnL
# filter
iptables -vnL
iptables -t filter -A INPUT -s 10.0.0.1 -j ACCEPT
```

### 103 | iptables 过滤规则的使用

```shell
# -A / -I
iptables -A INPUT -s 10.0.0.2 -j ACCEPT
iptables -A INPUT -s 10.0.0.2 -j DROP
iptables -I INPUT -s 10.0.0.3 -j DROP
iptables -A INPUT -s 10.0.0.0/24 -j ACCEPT
# 默认 policy
iptables -P INPUT DROP
# -F 清空
iptables -F
# -D 删除
iptables -D INPUT 1
# -N -X -E 自定义规则
# -i eth0
iptables -I INPUT -s 10.0.0.4 -i eth0 -j DROP
# -p tcp udp icmp
iptables -t filter -A INPUT -i eth0 -s 10.0.0.5 -p tcp --dport 80 -j ACCEPT
iptables -t filter -A INPUT -j DROP
```

### 104 | iptables nat 表的使用

PREROUTING 目的地址转换

POSTROUTING 源地址转换

```shell
iptables -t nat -A PREROUTING -i eth0 -d 114.115.116.117 -p tcp --dport 80 -j DNAT --to-destination 10.0.0.1
iptables -t nat -A POSTROUTING -s 10.0.0.0/24 -o eth0 -j SNAT --to-source 111.112.113.114
```

**iptables 配置文件**

/etc/sysconfig/iptables

yum install iptables-services

service iptables save | start | stop | restart

### 105 | firewalld

支持区域 zone 概念

firewall-cmd

systemctl start | stop | enable | disable firewalld.service

```shell
# systemctl
service iptables stop
systemctl start firewalld.service
systemctl status firewalld.service
# firewall-cmd
firewall-cmd --state
firewall-cmd --list-all
firewall-cmd --zone=public --list-services
firewall-cmd --get-zones
firewall-cmd --get-default-zone
firewall-cmd --get-active-zone
# service
firewall-cmd --add-service=https
# port
# --permanent 永久生效，需要重新加载
firewall-cmd --add-port=8080/tcp --permanent
# --reload 临时规则被清除
firewall-cmd --reload
# source
firewall-cmd --remove-source=10.0.0.1
```

### 106 | SSH 介绍之 Telnet 明文漏洞

```shell
yum install telnet telnet-server xinetd -y
systemctl start xinetd.service
systemctl start telnet.socket
# 23/tcp
grep telnet /etc/services
# iptables
iptables -I INPUT -p tcp --dport=23 -j ACCEPT
# firewalld
firewall-cmd --permanent --add-port=23/tcp
firewall-cmd --reload
```

```shell
# 抓包
tcpdump -i any port 23 -s 1500 -w /tmp/23.dump
telnet localhost
# wireshark
yum install wireshark-gnome -y
```

### 107 | SSH 服务

**配置文件**

客户端 /etc/ssh/ssh_config

服务端 /etc/ssh/sshd_config

```shell
# Port 22
netstat -ntpl | grep 22
# systemctl status | start | stop | restart | enable | disable sshd.service
systemctl restart sshd.service
# PermitRootLogin yes
AuthorizedKeysFile .ssh/authorized_keys
```

```shell
# SecureCRT / Xshell / putty
# 密码认证
ssh -p 22 root@47.93.56.143
who
# 密钥认证
# ssh-keygen -t rsa
# ssh-copy-id
ssh-copy-id -i id_rsa.pub root@47.93.56.143
ssh root@47.93.56.143
ls -l /root/.ssh/authorized_keys
# scp 文件拷贝
scp x.txt root@47.93.56.143:/tmp/
scp root@47.93.56.143:/tmp/x.txt ./
```

### 108 | FTP 服务器 vsftpd 介绍与软件包安装

```shell
yum install vsftpd ftp -y
systemctl start vsftpd.service
systemctl enable vsftpd.service
# localhost
ftp localhost
# 匿名用户 ftp / 空密码，回车 /var/ftp
# 本地账号 /home/xxx
```

### 109 | vsftpd 配置文件介绍

/etc/vsftpd/vsftpd.conf

/etc/vsftpd/ftpusers

/etc/vsftpd/user_list

```shell
# vsftpd.conf
anonymous_enable=YES
local_enable=YES
write_enable=YES
# 主动传输模式
connect_from_port_20=YES
# man 5 vsftpd.conf
# 黑名单 / 白名单
userlist_enable=YES
# systemctl
systemctl restart vsftpd
# SELinux
getsebool -a | grep ftpd
setsebool -P ftpd_xxx 1
# firewalld
firewall-cmd --add-service ftp
# 远程
ftp 47.93.56.143
# 上传
put x.txt
# 下载
get x.txt
```

### 110 | vsftp 虚拟用户

```shell
# 创建虚拟用户
useradd vuser -d /data/ftp -s /sbin/nologin
cd /etc/vsftpd/
vim vuser.temp
vu1
123456
vu2
123456
vu3
123456
db_load -T -t hash -f /etc/vsftpd/vuser.temp /etc/vsftpd/vuser.db
chmod 600 /etc/vsftpd/vuser.db
# PAM
vim /etc/pam.d/vsftpd.vuser
auth sufficient /lib64/security/pam_userdb.so db=/etc/vsftpd/vuser
account sufficient /lib64/security/pam_userdb.so db=/etc/vsftpd/vuser
# vsftpd.conf
vim /etc/vsftpd/vsftpd.conf
guest_enable=YES
guest_username=vuser
allow_writeable_chroot=YES
pam_service_name=vsftpd.vuser
user_config_dir=/etc/vsftpd/vuserconfig
# vuserconfig
mkdir -p /etc/vsftpd/vuserconfig
vim vu1
local_root=/data/ftp
write_enable=YES
anon_umask=022
anon_world_readable_only=NO
anon_upload_enable=YES
anon_mkdir_write_enable=YES
anon_other_write_enable=YES
download_enable=YES
# 重启
systemctl restart vsftpd.service
# 登陆
ftp 47.93.56.143
vu1
123456
```

### 111 | samba 服务

```shell
yum install samba -y
yum install cifs-utils -y
mkdir -p /data/share
vim /etc/samba/smb.conf
[share]
        comment = Share Directories
        path = /data/share
        read only = No
# 创建 & 关联用户
useradd samba
smbpasswd -a samba
# samba.123
# 查看用户
pdbedit -L
# 删除用户
# smbpasswd -x samba
systemctl start smb.service
# 挂载 /home/samba
mount -t cifs -o username=samba //127.0.0.1/samba /mnt
# 挂载 /data/share
mount -t cifs -o username=samba //127.0.0.1/share /mnt
# 卸载
# umount /mnt/
```

### 112 | NFS 服务

```shell
yum install nfs-utils -y
vim /etc/exports
chown -R nfsnobody:nfsnobody /data/share/
# 配置
/data/share *(rw,sync,all_squash)
systemctl start nfs.service
# 客户端挂载
showmount -e localhost
mount -t nfs localhost:/data/share /mnt
```

### 113 | Nginx 基本配置文件

```shell
yum install yum-utils -y
yum-config-manager --add-repo https://openresty.org/package/centos/openresty.repo
yum install openresty -y
# 配置
/usr/local/openresty/nginx/conf/nginx.conf
service openresty start
```

