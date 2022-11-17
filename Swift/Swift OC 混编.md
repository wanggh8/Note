# Swift OC 混编



## Q & A

Q: 在 framework 中，是没有办法使用这个桥接文件的，就算你生成了这个桥接文件，并且正确的配置了 Objective-C Bridging Header 路径，编译的时候会提示 “using bridging headers with framework targets is unsupported“ 错误。所以怎么在 Swift 中使用或者继承 Objective-C 文件呢？
A: 虽然不支持桥接文件，并且 Swift 也不可以直接继承或者使用 Objective-C 文件的，所以需要在 framework 的头文件（比如 framework 为 Sample.framework, 头文件即为 Sample.h）对 Objective-C 文件声明，然后设置权限为 Public，并且设置 Objective-C 文件头文件权限为 Public

