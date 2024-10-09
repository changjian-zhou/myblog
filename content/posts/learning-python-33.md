---
title: "Learning Python 33"
date: 2024-10-09T14:58:03+08:00
draft: false
tags:
  - Python
---

# 异常编码细节

## try/except/else语句
except分句会捕捉try中代码的任何异常，只有try中代码顺利执行时，才会执行else中的代码。

## try/else分句
如果没有else,是无法知道代码是否通过了try语句，因为可能没有异常或者异常出现了而被处理了。

## try/finally语句
如果try语句中包含finally子句，无论try代码块执行时是否引发异常，都会执行finally的代码。

## 统一try语句语法
try -> except -> else -> finally

else和finally是可选的，可能会有0个或多个except,但是如果出现一个else,必须有至少一个except。

## raise语句
raise关键字，后面跟着可选的要引发的类或类的一个实例。

不管如何指定异常，异常总是通过实例对象来识别。

## assert语句
assert是有条件版的raise语句。

`assert <test>, <data>`
如果test为假，引发data异常。

assert语句通常用于验证开发期间程序的状况的，几乎都是用来收集用户定义的约束条件。

## with/as环境管理器

with/as语句就是try/finally的替代方案。

例如文件对象在with代码块之后会自动关闭。






