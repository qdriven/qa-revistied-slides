---
title: One Page JSON
summary: JSON in One Page for software QA
authors: [FluentQA]
tags: ['QAPython-Revisited']
categories: ['QAPython-Revisited']
date: '2023-08-12'
slides:
  # Choose a theme from https://github.com/hakimel/reveal.js#theming
  theme: simple
  # Choose a code highlighting style (see Hugo docs on Chroma)
  #   Light style: github-light. Dark style: dracula (default).
  highlight_style: github-light
---
## JSON in One Page for software QA

- Understand JSON in A Simple Way
- Short Intro, 10 minutes
- Tools used for Software Testing

--- 

<!-- TOC -->
- [JSON in One Page for software QA](#json-in-one-page-for-software-qa)
- [什么是JSON?](#什么是json)
- [JSON操作 - load(s)/dump(s)](#json操作---loadsdumps)
- [JSON字典转换](#json字典转换)
- [JSON/DICT/类的转换](#jsondict类的转换)
- [JSON/DICT 查找更简单的办法](#jsondict-查找更简单的办法)
- [JSON/DICT的DIFF的办法](#jsondict的diff的办法)
- [References](#references)
<!-- TOC -->

---

## 什么是JSON?

- 什么是JSON,key-value对？

```shell
{
  "key":"value"
}
```
- json 的value类型

```shell
{
  "keyOfObject":{"k-1":"v-1","k-i":0,"k-null":null}
}
```
- json/json array

---

## JSON操作 - load(s)/dump(s)
- 获取JSON转化为字典(DICT)
- 把字典转换为JSON

---
## JSON字典转换

- Dict 转化为 JSON
- JSON 转化为 DICT

---

## JSON/DICT/类的转换

- JSON/类相关转换,所谓序列化/反序列化
- DICT/类相互转换
- 一些异常: 字段类型是一个经常忽略的地方
  - 对于自动化测试而言全部当成字符串处理也不是不可以
  - 对于不同类型字段主要关注
    - 时间相关
    - null/或者不显示
  - 关于json key的别名

--- 

- JSON/DICT/类可以统一看，相互之间都可以转换
  - 类的好处是对于IDE友好,可以自动提示类字段
  - JSON/DICT非常任意，对IDE不友好，可以非常灵活，但是对于编程效率不算高
  - 在逻辑处理中建议都可以转化为类操作，代码可读性和变化更可控
- JSON/DICT/类的转换每门语言都可以
- 数据结构+算法=程序，JSON就是一种数据结构

---

## JSON/DICT 查找更简单的办法
- JSON query 
- 字典 query

---
## JSON/DICT的DIFF的办法

- deepdiff: 无脑比较
- 手工写比较器: 递归比较，核心问题递归在什么地方退出?

---

## References

- [python-json](https://github.com/oxylabs/python-parse-json)
- [ditty_dict](https://github.com/pawelzny/dotty_dict.git)
- [deepdiff](https://github.com/seperman/deepdiff.git)
- [dotobject](https://github.com/seperman/dotobject.git)