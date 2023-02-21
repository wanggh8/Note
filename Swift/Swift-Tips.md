---
title: Swift Tips
categories: Swift
description: Swift Tips
---

## Swift 5.5 引入了新的语法和 API 来支持这些功能。在应用程序中，除了使用最新的 Swift 版本外，还需要针对某些平台版本：

如果使用的是 Xcode 13.2 或更高版本，它会将新的并发运行时与应用程序捆绑在一起，这样就可以将 iOS 13 和 macOS 10.15 作为最低的支持版本（对于本地应用程序）。
如果使用的是 Xcode 13，但版本低于 13.2，那么只能把 iOS 15 或 macOS 12（或更高版本）作为最低的支持版本。

## ‘FrameworkName’ is not a member type of ‘FrameworkName’ errors inside swiftinterface

XCFramework 下类名和模块名重复时，报错。这是 xcframework 已知问题，后续 Apple 可能会修复。

目前快速解决方案：

1. 在 xcframework 所在文件夹打开命令行终端
2. 执行以下命令（替换 frameworkName 字段）：
    ```shell
    find . -name "*.swiftinterface" -exec sed -i -e 's/frameworkName\.//g' {} \;
    ```
3. 清理工程，重新编译

### 参考

- https://forums.swift.org/t/frameworkname-is-not-a-member-type-of-frameworkname-errors-inside-swiftinterface/28962
- https://stackoverflow.com/questions/34159442/x-is-not-a-member-type-of-y