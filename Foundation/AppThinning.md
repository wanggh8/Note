# App Thinning

包体积大小优化

## 指令集架构

### iOS 设备支持的指令集

#### armv6:

　　iPhone, iPhone 3G, iPod 1G/2G

#### armv7:

　　iPhone 3GS, iPhone 4, iPhone 4S, iPod 3G/4G/5G, iPad, iPad 2, iPad 3, iPad Mini

#### armv7s：

　　 iPhone 5, iPhone 5c, iPad 4

#### arm64:

　　iPhone X，iPhone 8(Plus)，iPhone 7(Plus)，iPhone 6(Plus)，iPhone 6s(Plus), iPhone 5s, iPad Air(2), Retina iPad Mini(2,3)

#### arm64e:

　　iPhone XS\XR\XS Max
　　
### macOS 设备支持的指令集　

x86_64 和 arm64

### Architectures

指定工程被编译成支持哪些指令集类型，而支持的指令集越多，就会编译出很多个指令集代码的数据包，对应生成二进制包就越大，也就是ipa包越大。　

### Valid Architectures　　

该编译项指定可能支持的指令集，该列表和Architectures列表的交集，将是Xcode最终生成二进制包所支持的指令集。

　　比如，你的Valid Architectures设置的支持arm指令集版本有：armv7/armv7s/arm64，对应的Architectures设置的支持arm指令集版本有：arm64，这时Xcode只会生成一个arm64指令集的二进制包。

　　减少安装包中的指令集数据包可以减小打包ipa的大小。　　
　　
### Build Active Architecture Only:

默认Debug的时候设置为YES，Release的时候设置为NO。设置为YES是只编译当前的architecture版本，生成的包只包含当前连接设备的指令集代码。设置为NO，则生成的包包含所有的指令集代码（上面的Valid Architectures跟Architectures的交集）。因此为了调试速度更快，则Debug应该设置为YES。


### 可执行文件大小限制

根据最大构建版本文件大小描述，苹果对可执行文件大小有明确限制，超过该限制会导致 App 审核被拒。具体限制如下：

- iOS 7 之前，二进制文件中所有的 __TEXT 段总和不得超过 80 MB
- iOS 7.X 至 iOS 8.X ，二进制文件中，每个特定架构中的 __TEXT 段不得超过 60 MB
- iOS 9.0 之后，二进制文件中所有的 __TEXT 段总和不得超过 500 MB

## Swift 

### Swift 标准库

Swift 标准库在打包动态库时，会完整放到 Frameworks 文件夹下

- 打包架构包含: armv7、armv7s、arm64、arm64e
- 压缩前共计 151.1  MB
- 压缩后共计 65.2 MB
- 预计对 App 影响：包体增大 65.2 MB

在将动态库打包进 App 工程时，XcodeBuild 会对 Swift 标准库进行优化，
strip 掉未使用的符号，从而减少 Swift 标准库大小。打进 App 内的动态库包含的 Swift 标准库如下：

- 打包架构包含: armv7、armv7s、arm64 
- 压缩前共计 40.4  MB
- 压缩后共计 12.6 MB
- 预计对 App 影响：包体增大 12.6 MB

从多架构，变成单架构支持的时候，非系统的动态库，会马上变成单架构，大小有明显的变化。而 Swift 标准库却保持不变。
Swift 标准库，在分发到具体设备的时候，是单架构

UniPack 解决方案

将动态库打进一个空壳 App，待Xcode优化后将ipa中动态库和Swift文件拷出并签名，打到目标ipa中

### 

## 参考

- https://www.zybuluo.com/qidiandasheng/note/1662385
- https://juejin.cn/post/6844904169938092045#heading-23
- https://www.cnblogs.com/lulushen/p/8135269.html

