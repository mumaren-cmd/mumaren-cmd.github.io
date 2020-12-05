# 团队博客提交格式

## 一、提交的md文档首部必须添加如下信息

```yaml
---
layout: post
title: ssh概述 #文章标题
description: 全面了解SSH 并应用到github上 #文章描述
tag: zeroac #文章所属标签 可写你的昵称 方便归类
categories: jekyll update
---
```

## 二、md文档命名开头要以日期开始，如下

```cpp
2020-12-06-自定义全英文名.md
```

## 三、将md文件放入你们clone的仓库下的 `_posts`文件夹下即可

## 四、将其推送到远程服务器即可

```shell
git add *
git commit -m "某某提交关于啥啥的Blog"
git pull origin master #拉取最新分支
git push origin main #推送到服务器
```

