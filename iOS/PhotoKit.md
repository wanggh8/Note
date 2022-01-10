---
title: PhotoKit
categories: iOS
description: iOS PhotoKit
---

# PhotoKit

iOS 14 请求用户相册权限分为读写权限和仅写权限：
```objc
typedef NS_ENUM(NSInteger, PHAccessLevel) {
    PHAccessLevelAddOnly = 1,
    PHAccessLevelReadWrite = 2,
}
```

info.plist 需要添加两个权限使用描述

- 请求仅写权限描述：Privacy - Photo Library Additions Usage Description
- 请求读写权限描述：Privacy - Photo Library Usage Description

info.plist 对应源码为：

```xml
<key>NSPhotoLibraryAddUsageDescription</key>
<string>访问相册</string>
<key>NSPhotoLibraryUsageDescription</key>
<string>访问相册</string>
```

## 申请权限

在 iOS 14 及以上设备，申请读写权限和仅写权限的顺序可能会影响最终的结果

申请仅写入相册权限
```objc
[PHPhotoLibrary requestAuthorizationForAccessLevel:PHAccessLevelAddOnly handler:^(PHAuthorizationStatus status){}];
```

申请读写相册权限
```objc
[PHPhotoLibrary requestAuthorizationForAccessLevel:PHAccessLevelReadWrite handler:^(PHAuthorizationStatus status){}];
```

### 写入相册

在先进行写入相册时，为最小化权限申请，优先申请仅写入权限。在 iOS 14 及以上设备时，写入相册调用以下方法系统会自动进行仅写相册权限申请，并会在用户选择后才会执行 `completionHandler` 回调。在 iOS 14 以下设备时，`performChanges` 方法会自动进行读写权限申请，但 `completionHandler` 回调不会等待用户选择结果，需手动申请权限。

```objc
[[PHPhotoLibrary sharedPhotoLibrary] performChanges:^{} completionHandler:^(BOOL success, NSError * _Nullable error) {}];
```

### 权限申请顺序

iOS 14 及以上版本，读写相册权限和仅写入相册权限的申请执行顺序不同，可能会导致不同的结果

| 先申请权限类型 | 先申请权限结果 | 后申请权限类型 | 后申请权限结果 | 总体权限 |
|---|:-:|---|:-:|:-:|
| PHAccessLevelAddOnly | 允许 | PHAccessLevelReadWrite | 允许 | 允许 |
| PHAccessLevelAddOnly | 允许 | PHAccessLevelReadWrite | 拒绝 | 允许写，拒绝读 |
| PHAccessLevelAddOnly | 拒绝 | PHAccessLevelReadWrite | 允许 | 先拒绝写，后允许<br>PS: 在未进行后申请权限未前，不允许写 |
| PHAccessLevelAddOnly | 拒绝 | PHAccessLevelReadWrite | 拒绝 | 拒绝 |
| PHAccessLevelReadWrite | 允许 | PHAccessLevelAddOnly | 不弹出 | 允许 |
| PHAccessLevelReadWrite | 拒绝 | PHAccessLevelAddOnly | 不弹出 | 拒绝 |

3. 