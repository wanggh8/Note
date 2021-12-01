---
title: Homebrew 使用
categories: Mac
description: Homebrew 是 macOS、Linux 下的一个包管理工具
cover: /images/MacOS.jpg
---

# Homebrew

## 安装卸载软件

- brew --version 或者 brew -v 显示brew版本信息

- brew install <formula> 安装指定软件

- brew uninstall <formula> 卸载指定软件

- brew list 显示所有的已安装的软件

- brew search text 搜索本地远程仓库的软件，已安装会显示绿色的勾

- brew search /text/ 使用正则表达式搜软件

- brew info <formula> 显示指定软件信息

- brew reinstall <formula> 重新安装指定软件，先卸载后安装

- brew install <formula> --build-from-source 源码安装指定软件，可以给定指定参数

- brew commands 列出所有可用命令


## 升级软件相关

- brew update 自动升级homebrew （从github下载最新版本）

- brew outdated 检测已经过时的软件

- brew upgrade 升级所有已过时的软件，即列出的以过时软件

- brew upgrade <formula> 升级指定的软件

- brew pin <formula> 禁止指定软件升级

- brew unpin <formula> 解锁禁止升级

- brew upgrade --all 升级所有的软件包，包括未清理干净的旧版本的包

- brew edit <formula> 编辑软件，不会的情况下慎用

- brew tap 列出本地资源仓库，其中 homebrew 是默认仓库，其它都是第三方仓库

- brew tap <user/repo> 添加第三方仓库，命名的规则按照github来定的。使用

- brew untap <user/repo> 删除仓库

- brew deps <formula> 查看指定软件依赖于哪些软件

- brew uses <formula> 查看指定软件被哪些软件所依赖

## 清理相关

homebrew 在升级软件时候不会清理相关的旧版本，在软件升级后我们可以使用如下命令清理

- brew cleanup -n 列出需要清理的内容

- brew cleanup <formula> 清理指定的软件过时包

- brew cleanup 清理所有的过时软件

- brew unistall <formula> 卸载指定软件
 
- brew unistall <fromula> --force 彻底卸载指定软件，包括旧版本

通过brew安装的文件会自动设置环境变量，所以不用担心命令行不能启动的问题。

