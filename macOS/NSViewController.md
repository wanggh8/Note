---
title: macOS NSViewController 
date: 2020-05-05
updated: 2020-05-05
tags: 
  - macOS
  - Objective-C
categories: macOS
description: macOS 
cover: /images/Xcode.png
top_img: /images/Xcode.png
typora-root-url: ../../../source
---





在 macOS 10.10 及更高版本中，NSViewController 使用初始化方法 `[[MyViewController alloc] init]` 时，调用 `loadView` 将加载与 NSViewController 同名的 Nib 文件，将 Nib 文件实例化视图连接到视图控制器的视图属性。如果不存在 Nib 文件，会触发运行时崩溃：

```
-[NSNib _initWithNibNamed:bundle:options:] could not load the nibName: NSViewController in bundle (null).
```

