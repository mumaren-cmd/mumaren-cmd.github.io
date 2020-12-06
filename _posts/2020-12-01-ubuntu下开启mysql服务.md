---
layout: post
title: ubuntu下开启mysql服务 #文章标题
description: 介绍8.0版本mysql的DCL语言 #文章描述
tag: kong #文章所属标签 可写你的昵称 方便归类
categories: jekyll update
---

# 引言

由于8.0版本以上mysql的一些DCL命令不同于之前的版本，故如继续使用之前的老命令则会无情的报语法错误。这就给碰巧一直都学的5.0版本老命令的我造成了不小的麻烦，浪费了不少时间，故写下这份博客希望可以帮助到后来的人。

# 安装mysql服务
装好数据库服务端和客户端(**合理使用sudo**)，在终端利用apt包管理工具傻瓜式安装mysql。
温馨提示：在软件更新中将软件源换成阿里云会装的更顺利哦!
```powershell
apt install mysql-server 
apt install mysql-client
```
# 给root用户设置密码
刚刚安装好的mysql的root用户是没有密码的，所以为了安全性，首先设置一下root用户密码是必不可少的。

### 启动数据库

```powershell
//启动服务
service mysql start

//查看服务的状态
service mysql status

//如果像以下情况就代表启动成功了
● mysql.service - MySQL Community Server
     Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset:>
     Active: active (running) since Thu 2020-12-03 03:36:05 CST; 6h left
    Process: 735 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=ex>
   Main PID: 808 (mysqld)
     Status: "Server is operational"
      Tasks: 37 (limit: 19012)
     Memory: 393.1M
     CGroup: /system.slice/mysql.service
             └─808 /usr/sbin/mysqld
```
### 进入数据库

```powershell
//如果您不是root用户的话需要加上sudo
sudo mysql -uroot
```
### 设置密码

```powershell
//identified by 后的字符串就是你要设置的密码
alter user 'root'@'localhost' identified by '123456';
```
# 远程访问数据库
### 创建用户

```powershell
//注意@后面指可登陆的主机名，如想让任意主机都可访问，则使用%同配符
create user 'root'@'%' identified by '123456';

//查看用户是否创建成功
select user,host from mysql.user;

//表中存在我们刚刚创建的用户
+------------------+-----------+
| user             | host      |
+------------------+-----------+
| root             | %         |
| debian-sys-maint | localhost |
| mysql.infoschema | localhost |
| mysql.session    | localhost |
| mysql.sys        | localhost |
| root             | localhost |
+------------------+-----------+
6 rows in set (0.00 sec)
```
### 给新用户授权

```powershell
//为了方便我就授予所有权限了，您当然可以选择适当的权限授予
grant all privileges on *.* to 'root'@'%';

//刷新特权
flush privileges;
```
### 修改配置文件
```powershell
//打开配置文件
vi /etc/mysql/mysql.conf.d/mysqld.cnf 
```
打开文件后，找到bind-address=127.0.0.1这行，将这行注释（在最前面打#）。至于vi如何使用请自行百度。务必记得保存。

```powershell
# bind-address          = 127.0.0.1
```
修改完配置文件后请务必重启mysql服务

```powershell
service mysql restart
```
### 远程连接
远程连接就不同于本地连接了

```powershell
//-h为服务器ip -u为用户名 -p为端口号 -p指密码
mysql -hIP -uroot -p3306 -p 
```
这时就应该连接成功了，这样您就可以用另一台计算机使用数据库服务了！
```powershell
//显示数据库内容以检验是否连接成功
show databases;
```
