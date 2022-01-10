---
title: Block 块
categories: Objective-C
description: Objective-C Block 块
---

# Block 块

## 简介

<img src="/assets/image-20210419104023197.png" alt="image-20210419104023197" style="zoom:60%;" />

## 实现

## 注意事项

> 截获自动变量的方法没有实现对C语言数组的捕获，使用指针替代可解决
>
> ```objc
> typedef void (^Blk)(void);
> // 截获自动变量的方法没有实现对C语言数组的捕获
> // 使用指针替代可解决
> // const char text[] = "hello";
> const char *text = "hello";
> Blk blk3 = ^{
> 	printf("%c\n", text[2]);
> };
> blk3();
> ```
>
> 

> 测试2