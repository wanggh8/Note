---
title: WSL
categories: Linux
description: WSL
---

## WSL2 支持 ipv6

- 系统版本 Windows 11 22H2 及以上
- Microsoft Store 里下载最新的 Windows Subsystem for Linux
- 确认 wsl --version 在 1.0 以上

1. 使用 Hyper-V 创建 `WSLBridge` 的外部虚拟交换机来给 WSL2 用

2. 在用户目录 %USERPROFILE% 下面创建一个配置文件 .wslconfig，格式如下：
    ```shell
    [wsl2]
    networkingMode=bridged # 桥接模式
    vmSwitch=WSLBridge # 你想使用的网卡
    ipv6=true # 启用 IPv6
    ```
    
3. 输入 `wsl --shutdown && wsl` 重启 WSL2    

## WSL2 启用 systemd

1. 使用最新版本 wsl 运行以下命令：

    ```shell
    echo -e "[boot]\nsystemd=true" | sudo tee -a /etc/wsl.conf
    ```

1. 输入 `wsl --shutdown && wsl` 重启 WSL2

2. 输入 `ps --no-headers -o comm 1` 是否返回 `systemd` 判断 wsl 是否已启用 `systemd`

## WSL2 启用 sshd


