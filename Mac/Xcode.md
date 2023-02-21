---
title: Xcode 
categories: Mac
description: Xcode 相关
cover: /images/MacOS.jpg
---

## 错误处理

### This application's application-identifier entitlement does not match that of the installed application. These values must match for an upgrade to be allowed

原因：这个项目App已经存在这个真机上了，这个App是旧的identifier运行的。

解决方法：Xcode --->Window ---> Devices ---> 自己的真机 ---> installed Apps ----> 删除这个App  ----> 重新运行

## 查看 iPA entitlements

`codesign -d Demo_netease2.app  --entitlements -`

## Xcode Build

https://help.apple.com/xcode/mac/current/#/itcaec37c2a6

[Xcode 常见 CLI 工具](https://mp.weixin.qq.com/s/jF6mTsxC2xtn8Xp1Mn72Zw)


Create an archive of the framework or library for each platform you wish to support by entering one xcodebuild command for each platform’s generic run destination. To build a macOS variant of your framework built for UIKit, pass Mac Catalyst as the variant argument.

```sh
xcodebuild archive  [-project <project name>] -scheme <scheme name> -destination "generic/platform=<platform name>[,arch=<architecture name>][,variant=<variant name>]" [-configuration <configuration name>] [-archivePath <archive output path>]
```

Create an XCFramework which includes each variant of the framework or library by entering an xcodebuild command with the -create-xcframework option in Terminal:

```sh
xcodebuild -create-xcframework -framework <path> [-framework <path>...] -output <path>

xcodebuild -create-xcframework -library <path> [-headers <path>] [-library <path> [-headers <path>]...] -output <path>
```

## LLDB

### 命令

#### bt

#### tb

#### po

### 参考

- [http://southpeak.github.io/2015/01/25/tool-lldb/](http://southpeak.github.io/2015/01/25/tool-lldb/)