---
layout: post
date: 2020-07-01 16:23:00 +0800
title: pandas notes
description: python-pandas 笔记
share: true
tags: 
- python
---

1. NaN是没有办法直接比较的，因为NaN不等于任何具体的数据类型，并且NaN也不等于NaN，如果DataFrame需要判断某一列是否为NaN，可以使用函数isna()和notna()来判断，使用fillna()等函数来处理

   ```python
   data = data[data["AdminRegion1"].isna()]
   ```

   