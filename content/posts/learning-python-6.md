---
title: "Learning Python 6"
date: 2024-09-11T16:22:27+08:00
draft: false
tags:
  - Python
---

# 动态类型简介
动态类型是Python自动为我们跟踪对象的类型，不需要我们在脚本中编写声明语句。
## 缺少类型声明语句的情况
类型是在运行过程中自动决定的，而不是通过代码声明。
### 变量、对象和引用
变量在赋值的时候才创建，它可以引用任何类型的对象，并且必须在引用之前赋值。
### 类型属于对象，而不是变量
变量名没有类型。
### 对象的垃圾收集
每当一个变量名被赋予一个新的对象，之前的那个对象占用的空间就会被回收。
## 共享引用
多个变量引用了同一个对象。
### 共享引用和在原处修改
`pass`
### 共享引用而后相等
```python
==   # 值是否相等
is   # 是否是同一个对象
```
## 动态类型随处可见
`pass`


