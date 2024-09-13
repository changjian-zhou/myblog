---
title: "Learning Python 11"
date: 2024-09-13T16:09:25+08:00
draft: false
tags:
  - Python
---

# 赋值、表达式和打印


## 赋值语句
- 赋值语句建立对象引用值
- 变量名在首次赋值时会被创建
- 变量名在引用前必须先赋值
- 执行隐式赋值的一些操作

## 表达式语句
- 调用函数和方法
- 在交互模式提示符下打印值

## 打印操作
`print([object, ...][, sep=' '][, end='\n'][, file=sys.stdout])`

```python
import sys
sys.stdout = open('log.txt', 'a')
print(x, y, z)
```

