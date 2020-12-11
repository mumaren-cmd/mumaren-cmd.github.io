---
layout: post
title: 第三周任务
description: git操作视频&linux C
tag: Notice
categories: jekyll update
---

# 第三周任务

## 一、视频任务(周三截止)

### step 1： clone团队博客仓库

> 打开[团队仓库地址](https://github.com/mumaren-cmd/mumaren-cmd.github.io)
>
> 在本地电脑新建个文件夹groupBlog 用来存放clone该仓库的文件
>
> 进入该文件夹后右键打开终端 clone上述仓库地址(使用http)
>
> ```shell
> git clone https://github.com/mumaren-cmd/mumaren-cmd.github.io.git
> ```
>
> 大概要等半个小时左右..
>
> 运行如下命令 查看远程仓库详情。
>
> ```shell
> git remote -v
> ```
>
> 若为`mumaren-cmd/mumaren-cmd.github.io.git`就说明已经以合作者的身份加入该项目中 可以随意的push了，否则提交给我github账号 我来添加到合作者里即可。
>
> 然后打开团队的    [GitHub Pages]( https://mumaren-cmd.github.io/)   页面，每次push完毕，在该页面上刷新即可看到最新效果

### step 2： 在本地编写md文档切分支修改合并提交

> md提交格式参考 [readme](https://mumaren-cmd.github.io/2020/12/readme/)
> 假定你的md文档名为myTest.md 则先进入其所在目录。
> 并输入以下命令提交到远程仓库
>
> ```shell
> git add . #将当前所有更改添加到暂存区
> git commit -m "add myTest.md" #提交到本地仓库
> git push origin master #推送到远程仓库
> ```
> 提交完毕后 在本地新建并切换到一个新的分支dev上
> ```shell
> git checkout -b dev #新建分支dev(可自定义) 并切换到该分支上
> ```
> 然后在`myTest.md`的结尾处添加一段话 `modify dev`
> ```shell
> echo "modify_dev" >> myTest.md
> ```
> 然后将此改变提交到本地分支的仓库
> ```shell
> git add . #将当前所有更改添加到暂存区
> git commit -m "add modify_dev to myTest.md" #提交到本地仓库
> ```
> 然后切到主分支
> ```shell
> git checkout master
> ```
> 在主分支上做类似的修改
> ```shell
> echo "modify_master" >> myTest.md
> git add . #将当前所有更改添加到暂存区
> git commit -m "add modify_master to myTest.md" #提交到本地仓库
> ```
> 然后将dev分支合并到当前分支(master)上
> ```shell
> git merge dev
> ```
> 然后会出现冲突 提示修改`myTest.md`文件 来解决冲突
> 于是`vim myTest.md` 去解决冲突 删除自动添加的冲突标记并决定代码的去留
> 然后再次输入以下命令
> ```shell
> git add.
> git commit -m "solved conflict of myTest.md "
> git push origin master #冲突解决完毕 推送到远程仓库中
> git branch -d dev #工作完毕 删除本地的dev分支
> ```
> 然后在[团队博客](https://mumaren-cmd.github.io)上查看效果
### step3：拍摄视频

> 当**step 2**过程练熟之后，在同一校区的可互相拍摄视频 
>
> 拍摄者在拍摄过程中依次说出如下命令，电脑前同学依次执行 ：
>
> > 1.拉取最新仓库 `git pull` 
> >
> > 2.在本地切一个新的分支`dev` 修改你的md文档 并提交到本地仓库
> >
> > 3.切回主分支`master` 做相似的修改(用于产生冲突) 并提交到本地仓库
> >
> > 4.把`新分支dev`合并到`主分支master`上
> >
> > 5.解决冲突 并提交到远程仓库 
> >
> > 6.删除`新分支dev`
> >
> > 7.查看当前的git状态
> >
> > 8.在[团队博客](https://mumaren-cmd.github.io)展示更改效果
> > 
> > over

## 二、Linux C 学习

**请大家认真学习以下两门课程**

[Linux C语言指针与内存](https://www.imooc.com/learn/394)

[Linux C语言编程基本原理与实践](https://www.imooc.com/learn/248)
modify dev test
