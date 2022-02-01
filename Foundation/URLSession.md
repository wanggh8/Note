---
title: URLSession
categories: Foundation
description: URLSession
---

# URLSession

iOS 支持 Multipath TCP (MPTCP)，并且允许 iPhone 或 iPad 通过蜂窝移动数据连接建立与目标主机的备份 TCP 连接。
网络管理员可能需要使用 MPTCP。使用标准家庭网络的客户无需启用 MPTCP。
关于 Multipath TCP
MPTCP 是对传输控制协议 (TCP) 规范的一组扩展。凭借 MPTCP，客户端可以通过不同网络适配器连接到有多个连接的同一目标主机。这可在各主机间建立强大而高效的数据连接，并且与现有的网络基础设施兼容。 

```swift
enum MultipathServiceType : Int
```


https://support.apple.com/zh-cn/HT201373