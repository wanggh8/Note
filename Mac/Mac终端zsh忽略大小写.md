---
title: Mac终端zsh忽略大小写 
date: 2021-05-25
updated: 2021-05-25
categories: Mac
description: Mac终端zsh忽略大小写 
cover: /images/MacOS.jpg
top_img: /images/MacOS.jpg
typora-root-url: ../../../source
---

Mac 终端默认是大小写不敏感的，cd desktop 其实也能切到桌面，但是无法通过tab补全。
如果你已经使用了zsh，那么一般情况下，修改.inputrc 并没有效果。
在.zshrc 里添加下面两个命令并重启后可以忽略大小写。

```sh
# Ignore lower upper
autoload -Uz compinit && compinit -u
zstyle ':completion:*' matcher-list 'm:{[:lower:][:upper:]}={[:upper:][:lower:]}' 'm:{[:lower:][:upper:]}={[:upper:][:lower:]} l:|=* r:|=*' 'm:{[:lower:][:upper:]}={[:upper:][:lower:]} l:|=* r:|=*' 'm:{[:lower:][:upper:]}={[:upper:][:lower:]} l:|=* r:|=*'
```

