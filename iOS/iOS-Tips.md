---
title: iOS Tips
categories: iOS
description: iOS Tips
---

# iOS Tips

## 屏幕旋转 

[supportedInterfaceOrientations not called in iPad](https://stackoverflow.com/questions/35274428/supportedinterfaceorientations-not-called-in-ipad)

Requires full screen

## Home Indicator

- 隐藏 Home 键，设置 `prefersHomeIndicatorAutoHidden` 为 `true`。设置后页面不再显示 Home Indicator，但点击后仍会出现，且上拉一次就会返回主页面。一般用于视频播放等页面

- 优先 App 内手势，设置 `preferredScreenEdgesDeferringSystemGestures` 为 `UIRectEdgeAll`。设置后，点击无法触发Home Indicator，只有从底部往上拉才会触发，并且第二次才会触发返回界面的动作。

- `prefersHomeIndicatorAutoHidden` 和 `preferredScreenEdgesDeferringSystemGestures` 不可一起使用，否则后者不生效
