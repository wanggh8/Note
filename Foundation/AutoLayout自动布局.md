---
title: AutoLayout 自动布局
categories: Foundation
description: Auto Layout是由苹果公司提供的一个用于动态计算UIView及其子类的大小和位置的库
cover: /images/Xcode.png
---

# AutoLayout 自动布局

## 历史

Auto Layout 构建在 Cassowary 算法的基础之上，苹果公司在 iOS 6 系统时引入了 Auto Layout，在iOS 9发布时，苹果推出了更简洁语法的 [NSLayoutAnchor](https://developer.apple.com/documentation/uikit/nslayoutanchor)。iOS 12 大幅度提升Auto Layout 性能，使滑动屏幕时达到满帧

## NSLayoutConstraint

步骤和代码繁杂，除非兼容 iOS 9 以下，否则不建议使用。

## NSLayoutAnchor

### 常用属性

- leadingAnchor
- trailingAnchor
- leftAnchor
- rightAnchor
- topAnchor
- bottomAnchor
- widthAnchor
- heightAnchor
- centerXAnchor
- centerYAnchor
- firstBaselineAnchor
- lastBaselineAnchor

参考 [Apple Developer NSLayoutAnchor](https://developer.apple.com/documentation/uikit/nslayoutanchor)

### 更新约束

- setNeedsLayout: 告知页面需要更新，但是不会立刻开始更新。执行后会立刻调用layoutSubviews。

- layoutIfNeeded: 告知页面布局立刻更新。所以一般都会和setNeedsLayout一起使用。如果希望立刻生成新的frame需要调用此方法，利用这点一般布局动画可以在更新布局后直接使用这个方法让动画生效。

- layoutSubviews: 更新子View约束

- setNeedsUpdateConstraints:需要更新约束，但是不会立刻开始

- updateConstraintsIfNeeded:立刻更新约束

- updateConstraints:更新View约束


### 使用步骤

1. 在使用 `NSLayoutAnchor` 为视图添加约束时一定要先把`translatesAutoresizingMaskIntoConstraints` 设置 false

2. 在使用 `safeAreaLayoutGuide` 适配 iPhone X 等机型时要对 iOS 11 之前的系统做适配，否则会导致低版本系统上程序 Crash

3. 设置约束后要将其激活，即设置 active 为 true

可选

1. 设置宽高比，设置multiplier为相应比例



### 注意事项

1. `leadingAnchor` 与 `leftAnchor`、`trailingAnchor` 与 `rightAnchor` 不允许混用。在编译时不会出现任何问题，但是在运行时就会报错，并会导致程序 Crash

2. 




### 使用示例

```objc
UIView *parentView = [[UIView alloc] init];
UIView *childView = [[UIView alloc] init];
[parentView addSubview:childView];

childView.translatesAutoresizingMaskIntoConstraints = NO;
[childView.centerXAnchor constraintEqualToAnchor:parentView.centerXAnchor].active = YES;
[childView.centerYAnchor constraintEqualToAnchor:parentView.centerYAnchor].active = YES;
[childView.widthAnchor constraintEqualToConstant:100].active = YES;
[childView.heightAnchor constraintEqualToConstant:100].active = YES;
```

## Auto Layout 的生命周期

苹果的Auto Layout是基于Cassowary算法的，苹果在此基础上提供了一套Layout Engine引擎，由它来管理页面的布局，来完成创建、更新、销毁等。

在APP启动后，会开启一个常驻线程来监听约束变化，当约束发生变化后会出发Deffered Layout Pass(延迟布局传递)，在里面做容错处理（如有些视图在更新约束时没有确定或缺失布局申明），完成后进入约束监听变化的状态。

当下一次刷新视图（如调用layoutIfNeeded()）时，Layout Engine会从上到下调用layoutSubviews()，然后通过Cassowary算法计算各个子视图的大小和位置，算出来后将子视图的frame从layout Engine里拷贝出来，在之后的处理就和手写frame的绘制、渲染的过程一样了。使用Auto Layout和手写frame多的工作就在布局计算上。
