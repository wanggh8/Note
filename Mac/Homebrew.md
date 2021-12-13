---
title: Homebrew 使用
categories: Mac
description: Homebrew 是 macOS、Linux 下的一个包管理工具
cover: /images/MacOS.jpg
---

# Homebrew
Homebrew 是一款自由及开放源代码的软件包管理系统，用以简化 macOS 和 linux 系统上的软件安装过程。它拥有安装、卸载、更新、查看、搜索等很多实用的功能，通过简单的一条指令，就可以实现包管理，十分方便快捷。

Homebrew 主要有四个部分组成:
| 名称             | 备注                            |
|------------------|---------------------------------|
| brew             | Homebrew 源代码仓库             |
| homebrew-core    | Homebrew 核心软件仓库           |
| homebrew-bottles | Homebrew 预编译二进制软件包     |
| homebrew-cask    | 提供 macOS 应用和大型二进制文件 |



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

## 源管理

### 查看源

查看 brew.git 当前源

```shell
cd "$(brew --repo)" && git remote -v
```

查看 homebrew-core.git 当前源

```shell
cd "$(brew --repo homebrew/core)" && git remote -v
```

### 替换为清华源

#### 替换 brew.git 源
```shell
git -C "$(brew --repo)" remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git
```

#### 替换 homebrew-core.git 源
```shell
git -C "$(brew --repo homebrew/core)" remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git
```

#### 替换 homebrew-cask.git 源
```shell
git -C "$(brew --repo homebrew/cask)" remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-cask.git
```

#### zsh 替换 brew bintray 镜像
```shell
echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles' >> ~/.zshrc
```
更新配置
```shell
source ~/.zshrc
```

#### bash 替换 brew bintray 镜像
```shell
echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles' >> ~/.bash_profile
```
更新配置
```shell
source ~/.bash_profile
```

#### 刷新源
```shell
brew update
```

### 替换为阿里源

#### 替换 brew.git 源
```shell
git -C "$(brew --repo)" remote set-url origin https://mirrors.aliyun.com/homebrew/brew.git
```

#### 替换 homebrew-core.git 源
```shell
git -C "$(brew --repo homebrew/core)" remote set-url origin https://mirrors.aliyun.com/homebrew/homebrew-core.git
```

#### 替换 homebrew-cask.git 源
```shell
git -C "$(brew --repo homebrew/cask)" remote set-url origin https://mirrors.aliyun.com/homebrew/homebrew-cask.git
```

#### zsh 替换 brew bintray 镜像
```shell
echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.aliyun.com/homebrew/homebrew-bottles' >> ~/.zshrc
```
更新配置
```shell
source ~/.zshrc
```

#### bash 替换 brew bintray 镜像
```shell
echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.aliyun.com/homebrew/homebrew-bottles' >> ~/.bash_profile
```
更新配置
```shell
source ~/.bash_profile
```

#### 刷新源
```shell
brew update
```

### 重置为官方源

#### 重置 brew.git 源
```shell
git -C "$(brew --repo)" remote set-url origin https://github.com/Homebrew/brew.git
```

#### 重置 homebrew-core.git 源
```shell
git -C "$(brew --repo homebrew/core)" remote set-url origin https://github.com/Homebrew/homebrew-core.git
```

#### 替换 homebrew-cask.git 源
```shell
git -C "$(brew --repo homebrew/cask)" remote set-url origin https://github.com/Homebrew/homebrew-cask.git
```

#### zsh 注释掉 HOMEBREW_BOTTLE_DOMAIN 配置
```shell
vi ~/.zshrc
```
更新配置
```shell
source ~/.zshrc
```

#### bash 注释掉 HOMEBREW_BOTTLE_DOMAIN 配置
```shell
vi ~/.bash_profile
```
更新配置
```shell
source ~/.bash_profile
```

#### 刷新源
```shell
brew update
```


