---
title: iOS 沙盒
categories: iOS
description: iOS 沙盒机制
cover: /images/Xcode.png
---

用 Xcode 运行和停止项目，可以达到 App crash 的效果，但是无论是用真机还是模拟器，每用 Xcode 运行一次，都会改变沙盒路径，这会导致系统对绝对路径相关的文件操作失败，在某些情况系统记录的是上次的项目沙盒路径，最终导致出现找不到文件夹等错误。
