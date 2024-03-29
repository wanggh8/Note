---
title: Notificaiton 通知
categories: Foundation
description: Notificaiton 通知
---

# Notificaiton 通知

NSNotificaiton则是一对多注册一个通知

NSNotificationCenter

NSNotificationCenter: 实现NSNotificationCenter的原理是一个观察者模式，获得NSNotificationCenter的方法只有一种，那就是[NSNotificationCenter defaultCenter] ，通过调用静态方法defaultCenter就可以获取这个通知中心的对象了。NSNotificationCenter是一个单例模式，而这个通知中心的对象会一直存在于一个应用的生命周期。

NSNotification: 这是消息携带的载体，通过它，可以把消息内容传递给观察者。

iOS消息通知机制算是同步的，观察者只要向消息中心注册， 即可接受其他对象发送来的消息，消息发送者和消息接受者两者可以互相一无所知，完全解耦。这种消息通知机制可以应用于任意时间和任何对象，观察者可以有多个，所以消息具有广播的性质，只是需要注意的是，观察者向消息中心注册以后，在不需要接受消息时需要向消息中心注销，属于典型的观察者模式。

1.通过NSNotificationCenter注册通知NSNotification，viewDidLoad中代码如下:



```objc
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(notificationFirst:) name:@"First" object:nil];
```

第一个参数是观察者为本身，第二个参数表示消息回调的方法，第三个消息通知的名字，第四个为nil表示表示接受所有发送者的消息~

### 内存管理

```objc
NSNotificationCenter * __weak center = [NSNotificationCenter defaultCenter];
id __block token = [center addObserverForName:@"OneTimeNotification"
                                       object:nil
                                        queue:[NSOperationQueue mainQueue]
                                   usingBlock:^(NSNotification *note) {
                                       NSLog(@"Received the notification!");
                                       [center removeObserver:token];
                                       token = nil;
                                   }];
```

方法 `addObserverForName:object:queue:usingBlock:` 的返回值会被 `Notification center` 强引用。此外 `__block` 的变量会在 Block 拷贝到堆时，同时拷贝到堆。Block 内部使用返回值后，应主动设置为 nil，避免出现内存泄漏