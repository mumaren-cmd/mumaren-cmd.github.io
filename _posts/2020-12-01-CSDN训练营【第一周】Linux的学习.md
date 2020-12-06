---
layout: post
title: CSDN训练营【第一周】Linux的学习 #文章标题
description: 这周的主要任务是学习关于Linux的知识 #文章描述
tag: kang #文章所属标签
categories: jekyll update
---

## CSDN训练营【第一周】Linux的学习

这周的主要任务是学习关于Linux的知识，主要分为以下六个方面：
1.了解Linux操作系统与不同发行版本特点；
2.自主制作Linux操作系统USB安装盘；
3.熟练掌握路径、通配符以及磁盘管理系统常见使用技巧；
4.熟悉用户及Linux权限管理；
5.熟悉Linux网络管理及常用配置；
6.了解Linux服务

**了解Linux操作系统与不同发行版本特点**
1、版本：
a、Ubuntu，是一个以桌面应用为主的Linux操作系统,其名称来自非洲南部祖鲁语或豪萨语的"ubuntu"一词，意思是"人性"、“我的存在是因为大家的存在”，是非洲传统的一种价值观.，Ubuntu基于linux的免费开源桌面PC操作系统，十分契合英特尔的超极本定位，支持x86、64位和ppc架构
b、CentOS(Community Enterprise Operating System，中文意思是:社区企业操作系统)是Linux发行版之一
c、RHEL是Red Hat Enterprise Linux的缩写，是Red Hat公司的Linux系统，该系列有三个版本:Red Hat Enterprise Linux (Server including virtualization)，Red Hat Enterprise Linux Virtualization Platform。
d、Debian是指一个致力于创建自由操作系统的合作组织及其作品。
2、区别：
a、 Ubuntu,是一个以桌面应用为主的linux操作系统。Ubuntu的目标在于为一般用户提供一个最新的、同时又相当稳定的主要由自由软件构建而成的操作系统。
b、Centos,是一个基于redhat linux 提供的可自由使用源代码的企业级linux发行版本
c、Red Hat ，是redhat自己的发行的企业版，是redhat的一个重要节点。
红旗linux的发行版，包括桌面版、工作站版、数据中心服务器版、HA集群版和红旗嵌入式linux等产品，是中国较大、较成熟的linux发行版之一。
d、 Debian,三大发行版中唯一以社区形式运作，不以商业公司形式运作。是一个致力于创建自由操作系统的合作组织。而且debian开发者所创建的操作系统中绝大部分基础工具来自于GNU工程。
老师在上课的时候还详细给我们讲了如何从版本号区分是测试版还是正式版。如：x.y：为linux的主版本号。通常y若为奇数，表示此版本为测试版，系统会有较多bug，主要用途是提供给用户测试； zz：为次版本号； www：代表发行号（注意，它与发行版本号无关）。

**自主制作Linux操作系统USB安装盘**
1、首先要搞清楚自己电脑的类型，如我电脑的类型是UEFI新式bios+单硬盘，可以通过win+r输入msinfo32进行查看；
2、给自己的电脑进行分盘；
3、将ubuntun的镜像写入u盘；
4、u盘安装系统

**熟练掌握路径、通配符以及磁盘管理系统常见使用技巧**
在linux下分为绝对路径和相对路径，简单来说绝对路径就是从目录最最最最开始的地方开始查找，相对路径就是相对于你的当前目录下开始查找。
如果一个路径以 / 开头，就称为绝对路径；它表示当前文件与根目录的关系。举例如下：

```bash
/etc/passwd
/users/sjones/chem/notes
/dev/rdsk/Os3
123
```

不以 / 开头的路径称为相对路径，它表示文件与当前目录的关系。例如：

```bash
chem/notes
personal/res
12
```

如果想获取当前所在的目录，可以使用 pwd 命令：

```bash
$ pwd
/home/kyx/
12
```

通配符

通配符含义===>匹配文件名
它是shell的内置功能
通配符，用过DOS的应该很了解，也很常用。
通配符，指包含这些字符的字符串“？”，“*”，“[]”，{}

| 符号   | 作用                                                         |
| ------ | ------------------------------------------------------------ |
| [abcd] | 匹配abcd中任何一个字符                                       |
| {…}    | 表示生成序列. 以逗号分隔，且不能有空格                       |
| *      | 匹配任何字符串／文本，包括空字符串；*代表任意字符（0个或多个） ls file * |
| ?      | 匹配任何一个字符（不在括号内时）?代表任意1个字符 ls file 0   |
| [a-z]  | 表示范围a到z，表示范围的意思 []匹配中括号中任意一个字符 ls file 0 |

管理磁盘分区时经常会使用 df (disk free) 命令，df -k 命令可以用来查看磁盘空间的使用情况（以千字节计），例如：

```bash
$ df -k
Filesystem      1K-blocks      Used   Available Use% Mounted on
/dev/vzfs        10485760   7836644     2649116  75% /
/devices                0         0           0   0% /devices
$
12345
```

每一列的含义如下：
列 说明
Filesystem 代表文件系统对应的设备文件的路径名（一般是硬盘上的分区）。
kbytes 分区包含的数据块（1024字节）的数目。
used 已用空间。
avail 可用空间。
capacity 已用空间的百分比。
Mounted on 文件系统挂载点。

某些目录（例如 /devices）的 kbytes、used、avail 列为0，use列为0%，这些都是特殊（或虚拟）文件系统，即使位于根目录下，也不占用硬盘空间。

你可以结合 -h (human readable) 选项将输出信息格式化，让人更易阅读。 结合 -h 选项可以让信息显示的更加清晰：

```bash
$ du -h /etc
5k    /etc/cron.d
63k   /etc/default
3k    /etc/dfs
...
$
123456
```

**熟悉用户及Linux权限管理**
管理用户和组
下面是一些常用的管理用户和组的命令：

| 命令     | 说明         |
| -------- | ------------ |
| useradd  | 添加用户     |
| usermod  | 修改用户信息 |
| userdel  | 删除用户     |
| groupadd | 添加用户组   |
| groupmod | 删除用户组   |
| groupdel | 删除用户组   |

创建目录
可以使用 mkdir 命令来创建目录，语法为：

```bash
$ mkdir dirname
1
```

dirname 可以为绝对路径，也可以为相对路径。例如

```bash
$ mkdir 12345
1
```

会在当前目录下创建 mydir 目录。又如

```bash
$ mkdir /home/kyx/aaa
1
```

会在 /home/kyx目录下创建aaa目录。
mkdir 成功创建目录后不会输出任何信息。

删除目录
可以使用 rmdir 命令来删除目录，例如：

```bash
$ rmdir /home/kyx/aaa
1
```

注意：删除目录时请确保目录为空，不会包含其他文件或目录。

也可以使用 rmdir 命令同时删除多个目录：

```bash
$ rmdir dirname1 dirname2 dirname3
1
```

如果 dirname1、dirname2、dirname3 为空，就会被删除。rmdir 成功删除目录后不会输出任何信息。

查看文件权限
使用 ls -l 命令可以查看与文件权限相关的信息：

```bash
$ ls -l /home/kyx
-rwxr-xr--  1 kyx   users 1024  Nov 2 00:10  myfile
drwxr-xr--- 1 kyx   users 1024  Nov 2 00:10  mydir
123
```

第一列就包含了文件或目录的权限。
第一列的字符可以分为三组，每一组有三个，每个字符都代表不同的权限，分别为读取®、写入(w)和执行(x)：
第一组字符(2-4)表示文件所有者的权限，-rwxr-xr-- 表示所有者拥有读取®、写入(w)和执行(x)的权限。
第二组字符(5-7)表示文件所属用户组的权限，-rwxr-xr-- 表示该组拥有读取®和执行(x)的权限，但没有写入权限。
第三组字符(8-10)表示所有其他用户的权限，rwxr-xr-- 表示其他用户只能读取®文件。

改变权限
可以使用 chmod (change mode) 命令来改变文件或目录的访问权限，权限可以使用符号或数字来表示。
使用符号表示权限
对于初学者来说最简单的就是使用符号来改变文件或目录的权限，你可以增加(+)和删除(-)权限，也可以指定特定权限。
符号 说明

- 为文件或目录增加权限

- 删除文件或目录的权限
  = 设置指定的权限

下面的例子将会修改 testfile 文件的权限：

```bash
$ ls -l testfile
-rwxrwxr--  1 kyx  users 1024  Nov 2 14:10  testfile
$ chmod o+wx testfile
$ ls -l testfile
-rwxrwxrwx  1 kyx   users 1024  Nov 2 15:10  testfile
$ chmod u-x testfile
$ ls -l testfile
-rw-rwxrwx  1 kyx   users 1024  Nov 2 20:10  testfile
$ chmod g=rx testfile
$ ls -l testfile
-rw-r-xrwx  1 kyx   users 1024  Nov 2 20:15  testfile
1234567891011
```

也可以同时使用多个符号：

```bash
$ chmod o+wx,u-x,g=rx testfile
$ ls -l testfile
-rw-r-xrwx  1 kyx   users 1024  Nov 2 12:10  testfile
123
```

更改所有者和用户组
在Linux中，每添加一个新用户，就会为它分配一个用户ID和群组ID，上面提到的文件权限也是基于用户和群组来分配的。

有两个命令可以改变文件的所有者或群组：
chown：chown 命令是"change owner"的缩写，用来改变文件的所有者。
chgrp：chgrp 命令是"change group"的缩写，用来改变文件所在的群组。

chown 命令用来更改文件所有者，其语法如下：

```bash
$ chown kyx uftp
1
```

user 可以是用户名或用户ID，例如

```bash
$ chown kyx testfile
1
```

将 testfile 文件的所有者改为 kyx。

注意：超级用户 root 可以不受限制的更改文件的所有者和用户组，但是普通用户只能更改所有者是自己的文件或目录。

chgrp 命令用来改变文件所属群组，其语法为：

```bash
$ chgrp group filelist
1
```

group可以是群组名或群组ID，例如

```bash
$ chgrp special testfile
1
```

将文件 testfile 的群组改为 special。

**熟悉Linux网络管理及常用配置**
ping 命令
ping 命令会向网络上的主机发送应答请求，根据响应信息可以判断远程主机是否可用。

ping 命令的语法：

```bash
$ ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.068 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.070 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.081 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.062 ms
64 bytes from 127.0.0.1: icmp_seq=5 ttl=64 time=0.090 ms
64 bytes from 127.0.0.1: icmp_seq=6 ttl=64 time=0.063 ms
64 bytes from 127.0.0.1: icmp_seq=7 ttl=64 time=0.084 ms
64 bytes from 127.0.0.1: icmp_seq=8 ttl=64 time=0.061 ms

1234567891011
```

如果网络畅通，很快就可以看到响应信息。
ftp 工具
ftp 是 File Transfer Protocol 的缩写，称为文件传输协议。通过 ftp 工具，能够将文件上传到远程服务器，也可以从远程服务器下载文件。

ftp 工具有自己的命令（类似Linux命令），可以：
连接并登录远程主机；
查看目录，遍历目录下的文件；
上传或下载文件，包括文本文件、二进制文件等。

ftp 命令的用法如下：

```bash
$ ftp hostname or ip-address
1
```

接下来会提示你输入用户名和密码，验证成功后会进入主目录，然后就可以使用 ftp 工具的命令进行操作了。

在周日上午我们进行了任务核查，在看了其他人的上台展示发现自己还是有许多不足之处，还需要更加熟练linux中的各种命令，保证自己能熟练完成各种任务。
