---
title: FRP 客户端配置
categories: Mac
description: macOS 系统配置 FRP 客户端，并实现开机自启动
cover: /images/MacOS.jpg
---

## 安装

[地址](https://github.com/fatedier/frp/releases)

下载 darwin_arm64（Apple 芯片）或 darwin_amd64 (Intel 芯片) 版本，解压后编辑 `frpc.ini` 文件：

```
[common]
tls_enable = true
server_addr = xxxx
server_port = xxxx
token = xxxx

[vnc]
type = tcp
local_ip = 0.0.0.0
local_port = 5900
remote_port = xxxx

[ssh]
type = tcp
local_ip = 0.0.0.0
local_port = 22
remote_port = xxxx
```

运行命令：`./frpc -c frpc.ini` 即可

- 需注意放开服务器的对应端口，并检查端口是否被其他程序占用

## 配置自启动

使用 macOS 的 `launchd` 实现开机自启动

> 1. 如果需要 root，并且是需要用户登陆后才能运行，把 plist 放在 ~/Library/LaunchAgents/
> 2. 如果需要 root，并且不需要用户登陆后都能运行，把 plist 放在 /Library/LaunchDaemons/

### 1. 创建 plist 配置文件

打开终端执行：

```shell
sudo touch /Library/LaunchDaemons/frpc.plist
``` 

使用代码编辑软件或 vim 打开 frpc.plist 并填写以下内容：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC -//Apple Computer//DTD PLIST 1.0//EN
http://www.apple.com/DTDs/PropertyList-1.0.dtd >
<plist version="1.0">
<dict>
    <key>Label</key>
    <string>frpc</string>
    <key>ProgramArguments</key>
    <array>
         <string>frpc 绝对路径</string>
         <string>-c</string>
         <string>frpc.ini 绝对路径</string>
    </array>
    <key>KeepAlive</key>
    <true/>
    <key>RunAtLoad</key>
    <true/>
</dict>
</plist>
```

### 2. 添加到自启动

为 frpc.plist赋予权限：

```shell
sudo chown root /Library/LaunchDaemons/frpc.plist
```

加载配置到系统使配置生效，随系统自启动：

```shell
sudo launchctl load -w /Library/LaunchDaemons/frpc.plist
```

如后续需关闭随系统自启动，执行：

```shell
sudo launchctl unload -w /Library/LaunchDaemons/frpc.plist
```