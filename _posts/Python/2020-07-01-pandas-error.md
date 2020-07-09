---
layout: post
date: 2020-07-01 10:19:00 +0800
title: pandas errors
description: python-pandas 错误笔记
share: true
tags: 
- python
---

#### 1. 读取CSV文件时出错

**错误描述：**

```tex
UnicodeEncodeError:'mbcs' codec can't encode characters in position 0--1: invalid character
```

**原因：**文件路径不对，很可能是字符的编码方式不对造成的

**解决方式：**

```python
data = pd.read_csv(open(os.path.join(data_path, file_name), 'r', encoding='utf-8'))
```



#### 2. 创建csv文件时出错

**错误描述：**

```tex
FileNotFoundError: [Errno 2] No such file or directory: 'results/01/21/2020.csv'
```

**原因：** python可以创建新的文件，但是不可以创建新文件夹

**解决方案：**

```python
date.replace("/","-")
```



# 筛选数据出错



https://blog.csdn.net/qq_43003405/article/details/100005786





# 数据类型转换出错

https://www.cnblogs.com/chaojiyingxiong/p/10189357.html



# json.dump中文编码问题

https://blog.csdn.net/qq284489030/article/details/90260699



# 超大json文件解析

https://www.cnblogs.com/hexiaoqi/p/13040074.html