---
title: "Learning Python 13"
date: 2024-09-14T11:49:58+08:00
draft: false
tags:
  - Python
---

# while和for循环

## while循环

循环主体在顶端测试为真时会重复执行，而如果测试一开始就是假，主体就绝不会执行。

## break

跳出最近所在的循环

## continue

跳到最近所在循环的开头处

## pass

什么事也不做，只是空占位语句

## 循环else块

只有当循环正常离开时才会执行

## for循环

可以遍历任何有序的序列对象内的元素

```python
a, *b, c = (1, 2, 3, 4)
print(a, b, c)
1 [2, 3] 4
```

## zip

```python
L1 = [1, 2, 3, 4]
L2 = [5, 6, 7, 8]
list(zip(L1, L2))
```

## map

map会带一个函数，以及一个或多个的序列参数，然后用从序列中取出的并行元素调用函数的结果收集起来

```python
list(map(ord, 'spam'))
```

## enumerate
```python
S = 'spam'
for (offset, item) in enumerate(S):
    print(item, 'appears at offset', offset)
```



