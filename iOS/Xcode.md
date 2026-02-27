# Xcode 版本号自动递增

在 Archive 的 Scheme 的 Pre-actions 添加脚本：

```sh
cd "${PROJECT_DIR}" ; agvtool next-version -all
```

### 参考

- https://stackoverflow.com/questions/16869159/archive-in-xcode-4-5-no-errors-but-build-cancelled
- https://www.jianshu.com/p/f3141a30ce88
