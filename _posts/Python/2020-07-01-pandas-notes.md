---
layout: post
date: 2020-07-04 23:23:00 +0800
title: pandas notes
description: python-pandas 笔记
share: true
toc: true
tags: 
- python
---



[TOC]

[pandas官方网站](https://pandas.pydata.org/pandas-docs/stable/)



# 1. NaN的识别与判断

NaN是没有办法直接比较的，因为NaN不等于任何具体的数据类型，并且NaN也不等于NaN，

如果DataFrame需要判断某一列是否为NaN，可以使用函数isna()和notna()

```python
data = data[data["AdminRegion1"].isna()]
```



# 2. NaN的处理之fillna方法

对于DataFrame中出现的NaN，可以选择直接删去它所在的一行，

也可以使用合适的方式对其值进行推理，进行填充，

pandas中，一般使用fillna方法对NaN进行填充。

## 函数

```python
fillna(value=None, method=None, axis=None, inplace=False, limit=None, downcast=None, **kwargs)
```

## 参数列表

**value**：用于填充NaN的值，default=None  

**method**： 定义了填充空值的方法，

- {'backfill','bfill','pad','ffill', None}, default=None。

- pad / ffill表示用前面行/列的值，填充当前行/列的空值， 

- backfill / bfill表示用后面行/列的值，填充当前行/列的空值。

**axis**：操作的方向，按行还是按列

- {0,1,‘index’,‘columns’} ，default=0

- 0/index按行

- 1/columns按列

**inplace**：是否为原位操作

- True，表示进行原位操作

- False，表示不是原位操作，是默认值

**limit**：int，default=None。

- 如果method被指定，对于连续的空值，这段连续区域，最多填充前 limit 个空值。

- 如果method未被指定， 在该axis下，不论空值连续区间是否间断，最多填充前limit个空值  

**downcast**：dict, default is None，

- 字典中的项为，为类型向下转换规则。或者为字符串“infer”，此时会在合适的等价类型之间进行向下转换，比如float64 to int64 if possible。

## 注意事项

在这些参数中value、method、inplace是常用的参数

在一次调用中，value和method只能赋值一个，另一个保持默认，因为二者的填充方式是矛盾的



# 3. NaN的处理方式之dropna方法

<hr>

## 函数

```python
df.dropna(axis=0, how='any', inplace=True)
```

## 参数列表



**axis**：

- 0: 行操作（默认）  

- 1: 列操作

**how**：

- any: 只要有空值就删除（默认）  

- all:全部为空值才删除

**inplace**：

- False: 返回新的数据集（默认）  

- True: 在愿数据集上操作



# 填充某一列

https://blog.csdn.net/luoganttcc/article/details/78573669



# 4. 获取DataFrame的行数与列数

## 行数

```python
df.shape[1]
```

## 列数

```python
df.shape[0] 
len(df)
```



# 5. 检查一个属性字段是否在DataFrame中

## 方法一 in

```python
# if 'attribute_name' in df:
# 也可以用，但是为了清楚起见，大多使用如下版本，不省略coulumns
# df.columns - DataFrame的属性集合
if 'attribute_name' in df.columns:
```

## 方法二 issubset

```
if set(['A','C']).issubset(df.columns):
# or
if {'A', 'C'}.issubset(df.columns):
```



# 6. 筛选满足指定条件数据

## 直接筛选

直接使用列需要满足的条件，

如果需要多个列同时满足条件，使用’&‘符号连接即可；

如果只需要某一列满足条件，则使用’|'连接多个列的条件。

```python
date_column = source["Updated"]
country_column = source["AdminRegion1"].isna()
data = source[(date_column == date) & country_column] 
```

## 基于map筛选

其中map返回的值必须是bool类型，即某一个条件。然后使用直接筛选的方式，把条件合并，最终得出筛选的结果

```python
user_requried = all_data['User_id'].map(lambda x : x==1439408)
date_requried = all_data['Date'].map(lambda x : np.isnan(x))
some = all_data[user_requried & date_requried]
print(some) 
```



# 7 排序

## 按标签排序-sort_index()

函数：

```python
df.sort_index(axis=0,ascending=True)
```

参数：

- **axis**：0，按行；1，按列

- **ascending**：True，升序；False，降序

## 按值排序-sort_values()

函数：

```python
df.sort_values(by="column_name", kind="algorithm", ascending=True)
```

参数：

- **by**：排序标准

- **kind**：排序算法，{“Mergesort”,“Heapsort”,“Quicksort”}

- **ascending**：True，升序；False，降序



# 8 更改列的数据类型与值

## apply

```python
import pandas as pd

data = pd.read_csv('price.csv',encoding='utf-8')
data[u'buy_place'] = data[u'buy_place'].astype(str)
data[u'buy_place'] = data[u'buy_place'].apply(lambda x :x.split(' ')[-1])
data.to_csv('price.csv',index=False, encoding='utf-8')python
```



# 根据条件获取元素所在的位置（索引）

https://blog.csdn.net/xwd18280820053/article/details/72614734



# 删除行和列

https://www.cnblogs.com/everfight/p/pandas_drop.html



