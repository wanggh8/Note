---
title: Protobuf 使用
categories: Foundation
description: Protobuf 使用
---

# Protobuf 使用

## 安装

```shell
brew install protobuf
```

查看版本

```shell
protoc --version
```

## 编译生成 OC 文件

```shell
protoc --objc_out=./ ./input.proto
```

