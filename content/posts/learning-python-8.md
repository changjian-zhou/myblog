---
title: "Learning Python 8"
date: 2024-09-12T15:09:50+08:00
draft: false
tags:
  - Python
---


# 列表与字典

## 列表
- 任意对象的有序集合
- 通过偏移读取
- 可变长度、异构以及任意嵌套
- 属于可变序列的分类
```python
L = []
L.sort()
L.extend()
L.pop()
L.remove()
L.reverse()
del L[i:j]
L[i:j] = []
```

## 字典
```python
D = {'spam' : 2, 'ham' : 1, 'eggs' : 3}

D = {}
D['name'] ='mel'
D['age'] = 45

dict(name='mel', age=45)

dict([('name', 'mel'), ('age', 45)])
```
字典的update方法类似于合并。

字典pop方法能够从字典中删除一个键并返回它的值。

## 字典解析
```python
D = {k : v for (k, v) in zip(['a', 'b', 'c'], [1, 2, 3])}
```




