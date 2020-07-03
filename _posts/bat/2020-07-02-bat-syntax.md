---
layout: post
title: bat入门
description: Windows bat 批处理文件
date: 2020-07-02 20:51:00 +0800
share: true
tags:
- drafts
---





**转载：**[批处理菜鸟教程](https://blog.csdn.net/Joker_N/article/details/89838719)

# 一、常用命令简介

## 1. echo

- 功能：打开或关闭回显功能，回显消息
- 语法：echo [{on|off}] [message]
- 示例：@echo off / echo hello word
- 注意：

  - 控制台编码

## 2. rem

- 功能：注释
- 语法：rem [注释内容]
- 示例：rem 你好
- 注意：
  - ::也具有rem功能
  - 关闭回显时，rem和::后面的内容都不会显示
  - 打开回显时，rem后内容会显示出来，::后的内容不会显示

## 3. pause

- 功能：暂停

- 语法：pause

- 示例：

  ```bash
  echo off
  :begin
  copy g:\test\CMakeLists.txt d:\back
  echo another
  pause
  goto begin
  ```

- 例子释义：

  - 驱动器 G 中磁盘上的所有文件均复制到d:\back中。

  - 显示的注释提示您将另一张光盘盘放入驱动器 G 时，pause 命令会使程序挂起，以便您更换光盘，然后按任意键继续处理。
  
  - back是无后缀名的文件，而不是一个文件夹

  

## 4. call





## 5. start



## 6. goto



## 7. set



- 获取当前日日期与时间

  ```bash
  set d=%date:~0,10%
  set t=%time:~0,8%
  echo %d% %t%
  ```

  



















































