---
title: Git Manual
categories: Git
description: Git Manual
typora-root-url: ../
---

# Git Manual

## Git 简介

Git 是目前世界上最先进的分布式版本控制系统。SVN 是集中式版本控制系统，版本库是集中放在中央服务器的。Git是分布式版本控制系统，那么它就没有中央服务器的，每个人的电脑就是一个完整的版本库。Git 配置用户标识：

```shell
$ git config --global user.name "Gh.Wang"
$ git config --global user.email "1299927852@qq.com"
```

## Git 使用

选择一个空目录，路径最好不包含中文，然后使用 `git init` 可以把这个目录变成Git可以管理的仓库，只会可以用 `git add` 命令将文件添加到仓库暂存区中，然后可以用 `git commit` 提交到版本库分支中

```shell
$ git add readme.txt
$ git commit -m "wrote a readme file"
```

之后可以使用给`git status` 查看结果，当前是否有新的更改以及更改是否提交，如果被修改了可以用`git diff`查看文件修改前后的不同，选择是否要保留更改。如果选择放弃更改使用命令`git checkout -- file`可以丢弃工作区的修改，同时命令`git reset HEAD <file>`可以把暂存区的修改撤销掉，重新放回工作区。`git log`命令可以显示从最近到最远的提交日志，可以加上`--pretty=oneline`让信息在一行显示。之后进行版本回退有两种 方式

- 用`HEAD`表示当前版本，也就是最新的提交版本，上一个版本就是`HEAD^`，上上一个版本就是`HEAD^^`，以此类推，如果较多可以用`HEAD~n`，然后使用命令`$ git reset --hard HEAD^`回退。
- 直接使用`$ git reset --hard 加上版本号`，一般输入版本号的前几位就可以了。

在版本回溯中，git使用指针，将指针头指向真正应用的版本，当需要更改的时候只需要移动指针就可以了。

如果要删除某个文件的话就直接使用`rm`命令,不过此时并没有在版本库中删除，如果确实要从版本库中删除需要使用

```shell
$ git rm test.txt
$ git commit -m "remove test.txt"
```

如果误删，则可以使用`git checkout -- test.txt`恢复到最新版本。

### 更新 Git 缓存

更新缓存 `git rm -r --cached .`

### 分支与标签

- 创建并切换分支:`$ git checkout -b name`

- 查看当前分支:`git branch`

- 切换分支:`git checkout name`

- 合并指定分支到当前分支:`git merge`

- 删除分支:`git branch -d <name>`

- 新建一个标签:`git tag <tagname>`
- 指定标签信息:`git tag -a <tagname> -m "blablabla..."`
- 查看所有标签:`git tag`

### 远程仓库

首先需要创建SSH Key，使用命令：

```shell
$ ssh-keygen -t rsa -C "1299927852@qq.com"
```

可以在用户目录下看到.ssh目录，目录中有`id_rsa`和`id_rsa.pub`两个文件，其中第一个是私钥，第二个是公钥，我们一般用的就是公钥。在github的setting的ssh keys界面加入自己的公钥，之后电脑就可以往github上推送了。

添加远程库，使github上的远程库与本地库同步，使用命令：

```shell
$ git remote add origin git@gitee.com:wanggh8/resume.git
```

第一次可以使用`git push -u origin master`命令，实际上是把当前分支`master`推送到远程。之后可以直接使用命令`git push origin master `

从远程库克隆时，使用` git pull git@gitee.com:wanggh8/resume.git`

使用码云时大部分只需要将 github 替换成 gitee 就可以了，可以同时关联两个远程库，但名字应该不同。

## Git规范

### Git分支

1. master 存储正式发布历史的主分支，不能直接在`master`上进行修改代码和提交。
2. dev 作为开发分支，开发完成需要提交测试的功能合并到该分支，共同维护的开发分支。
3. release 上线前的 预览分支，可用于测试人员测试要上线的正式版，测试完成后PR到`master`。
4. feature 基于`dev`创建的临时分支，用于开发新功能或新模块，在本地与`dev`合并后PR到`dev`分支。

### Git 命令行操作流程

```shell
// 本地分支 local
git pull origin local
git add .
git commit -m ''   // 这里需写明这次提交的改动说明（必须提交），以便以后回退找到对应的指针
git push origin local
     
git checkout dev 
git pull origin dev 
     
git checkout local  //切换到自己的分支
git merge dev   // 有冲突解决冲突，让冲突发生在自己本地分支
     
git checkeout dev 
git merge local  //更新代码到 dev 分支
     
git add .
git commit -m "merge local 实现的功能"
git push origin dev
```

### TAG命名

采用三段式＋日期，v版本.里程碑.序号，如v1.2.1-20200801
- Bug修复并上线，修改第3位   
- 架构升级或重大调整，修改第2位
- 新功能上线或者模块调整，修改第2位