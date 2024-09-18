---
title: "Learning Python 12"
date: 2024-09-14T09:26:06+08:00
draft: false
tags:
  - Python
---

# if测试和语法规则

## if语句
Python if语句是选取要执行的操作。

## Python语法规则
- 语句是逐个运行的，除非你不这样编写
- 块和语句的边界会自动检查
- 复合语句=首行+“：”+缩进语句
- 空白行、空格以及注释通常都会忽略
- 文档字符串会忽略，但会保存并由工具显示

## if/else三元表达式
```python
A = Y if X else Z
# 上述代码相当于下述代码
if X:
    A = Y
else:
    A = Z
```




