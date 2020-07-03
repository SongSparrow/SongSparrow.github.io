---
layout: post
title: bat常用技巧
description: bat常用的功能
date: 2020-07-02 09:57:00 +0800
share: true
tags:
- drafts
---

# 1. chcp 切换控制台编码

```bash
@echo off
REM 声明采用UTF-8编码
chcp 65001
echo test
echo 中文测试
pause



```

# 2. 启动指定的应用程序

```bash
::启动TIM
start /d “d:\Tenccent\TIM\Bin” TIM.exe
```

