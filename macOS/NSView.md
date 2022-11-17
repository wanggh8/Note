---
title: macOS NSView 
description: macOS NSView
typora-root-url: ../
---

# macOS NSView

在 macOS 10.10 及更高版本中，NSView 使用初始化方法时，调用 `loadView` 将加载与 NSView 同名的 Nib 文件，将 Nib 文件实例化视图连接到视图控制器的视图属性。如果不存在 Nib 文件，会触发运行时崩溃：

```
-[NSNib _initWithNibNamed:bundle:options:] could not load the nibName: NSView in bundle (null).
```

解决办法：重写 `loadView` 方法

```objc
- (void)loadView {

}
```

## NSCollectionView

在低版本系统下，`NSCollectionView` 必须嵌套在 `NSScrollView` 中，否则 `dataSource` 中的 `func collectionView(_ collectionView: NSCollectionView, itemForRepresentedObjectAt indexPath: IndexPath) -> NSCollectionViewItem` 回调不会执行。

实例代码: 

```swift
lazy var flowLayout: NSCollectionViewFlowLayout = {
    let layout = NSCollectionViewFlowLayout()
    layout.scrollDirection = .vertical
    layout.itemSize = CGSize(width: (view.frame.width - 80) / 2, height: 40)
    layout.minimumLineSpacing = 20
    layout.minimumInteritemSpacing = 20
    layout.headerReferenceSize = NSZeroSize
    layout.footerReferenceSize = NSZeroSize
    layout.sectionInset = NSEdgeInsets(top: 20, left: 20, bottom: 20, right: 20)
    return layout
}()
    
let homeCollectionViewReuseIdentifier = NSUserInterfaceItemIdentifier(rawValue: "HomeViewItem")
    
lazy var collectionView: NSCollectionView = {
    let collectionView = NSCollectionView()
    collectionView.collectionViewLayout = self.flowLayout
    collectionView.register(HomeViewItem.self, forItemWithIdentifier: homeCollectionViewReuseIdentifier)
    collectionView.dataSource = self
    collectionView.delegate = self
    return collectionView
}()
    
lazy var scrollView: NSScrollView = {
    let scrollView = NSScrollView()
    // 必须将 NSCollectionView 嵌入到 NSScrollView，否则低版本系统无法正常显示
    scrollView.documentView = collectionView
    scrollView.autohidesScrollers = true
    return scrollView
}()
```



