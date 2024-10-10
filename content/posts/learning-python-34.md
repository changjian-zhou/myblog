---
title: "Learning Python 34"
date: 2024-10-10T10:40:06+08:00
draft: false
tags:
  - Python
---


# 异常对象

内置异常和用户定义的异常都可以通过类实例对象来表示。

## 基于类的异常
类异常是由超类关系进行匹配的：except子句列出一个通用的超类，任何特定的子类都可匹配。

## 内置Ecception类
`Exception`与应用相关的异常的顶层根超类。

`ArithmeticError`  所有数值错误的超类（Exception的子类）

## 定制打印显示

```python
class MyBad(Exception): pass
try:
    raise MyBad('Sorry--my mistake!')
except MyBad as X:
    print(X)

#显示以下内容：
#Sorry--my mistake!
```

因为异常也是类对象，可以修改__str__来定制打印显示。

## 定制数据和行为
异常类可以通过编写__init__中的信息构造实例属性来提供定制的信息。

