---
title: Framework 相关
categories: Foundation
description: Framework 相关
---

# Framework 相关

### Xcode Search Paths 选项配置

https://www.jianshu.com/p/d41e05e6d9fa

#### 查看 库 为静态库或动态库

命令行进入Framework后，使用file查看对应二进制文件，`current ar archive` 为静态库，引入时选择 `Do not Embed`；  `dynamically linked shared` 为动态库，引入时需要 `Embed&Sign`。

可以在 **Build Setting - Mach-O Type** 中设置动态库或静态库。创建 Framework 的时候默认是`Dynamic Library`，我们可以修改为`Static Library`。


## 参考

https://juejin.cn/post/6844903930439139336

https://www.jianshu.com/p/e05b965672c7

https://www.jianshu.com/p/42891fb90304