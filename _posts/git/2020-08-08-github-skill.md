---
layout: post
title: github使用技巧
description: 记录常用的github使用技巧
date: 2020-08-08 15:25:00 +08000
share: true
tags: 
- git
---

*****

#  1. 如何在GitHub中高效地搜索开源项目

| 搜索项         | 参数     | 示例                | 含义                               |
| -------------- | -------- | ------------------- | ---------------------------------- |
| in:name        | string   | in:name spring boot | 项目名称中包含spring boot的项目    |
| in:readme      | string   | in:readme 微服务    | 项目的readme中包含微服务的项目     |
| in:description | string   | in:description 爬虫 | 项目描述中包含爬虫的项目           |
| stars:         | number   | stars:>1500         | 项目的star数目大于1500的项目       |
| forks:         | number   | forks:>500          | 项目的fork数目大于500的项目        |
| language:      | language | language:java       | 项目语言为java的项目               |
| pushed:        | date     | pushed:>2019-06-06  | 最近更新时间在2019-06-06之后的项目 |

常用的搜索项如上表所示，更加详细的内容，见官方文档：[搜索之仓库搜索](https://docs.github.com/en/github/searching-for-information-on-github/searching-for-repositories)

