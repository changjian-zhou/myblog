---
title: "Learning Python 14"
date: 2024-09-18T11:51:20+08:00
draft: false
tags:
  - Python
---

# 迭代器和解析，第一部分

## 迭代器：初探
序列观念的通用化：如果对象是实际保存的序列，或者可以在迭代工具环境中一次产生一个结果的对象，
就看做是可迭代的。

## 文件迭代器

有`__next__`方法的对象被认为是可迭代的。

## 手动迭代：iter和next
内置函数next会自动调用一个对象的`__next__`方法

当for循环开始时，会通过它传给iter内置函数，以便从可迭代对象中获得一个迭代器，返回的对象含有需要的next方法。

## 扩展的列表解析语法
```python
lines = [line.rstrip for line in open('script1.py') if line[0] == 'p']
```

> 在函数调用时使用*arg形式，它会把一个集合的值解包为单个的参数。


## filter迭代器
`filter`内置函数对于传入的函数返回True的可迭代对象中的每一项，它都会返回该值。
```python
list(filter(bool, ['spam', '', 'ni']))
```


