---
title: "Learning Python 28"
date: 2024-09-27T17:38:01+08:00
draft: false
tags:
  - Python
---

# 类代码编写细节

## 一般形式
```python
class <name>(superclass, ...):
    data = value
    def method(self, ...):
        self.member = value
```

## 方法
方法位于class语句的主体内，是由def语句建立的函数对象

```python
instance.method(args...)
class.method(instance, args...)
```

## 调用超类构造函数
如果要保证子类的构造函数也会执超类构造时的逻辑，一般都必须通过类明确地调用超类的__init__方法。

```python
class Super:
    def __init__(self, x):
        ...
        default
        (code..)
class Sub(Super):
    def __init__(self, x, y):
        Super.__init__(self, x)    # 调用超类的init
        ..custom code...
I = Sub(1, 2)
```
## 继承
每次使用object.attr形式的表达式时，Python会从头到尾搜索命名空间树，先从对象开始，寻找所能找到的地一个attr。
## 抽象超类
抽象类是调用方法的类，但没有继承或定义该方法，而是期待该方法由子类填补。当行为无法预测，非得等到更为具体的子类编写时才知道，通常可用这种方式把类通用化。

## 命名空间：完整的内容
点号和无点号的变量名，会用不同的方式处理，而有些作用域是用于对对象命名空间做初始设定的。
- 无点号运算的变量名（例如，X）与作用域相对应。
- 点号的属性名使用的是对象的命名空间。
- 有些作用域会对对象的命名空间进行初始化（模块和类）。
## 命名空间字典
> 属性点号运算其实内部就是字典的索引运算，而属性继承其实就是搜索链接的字典而已。

属性实际上是Python的字典键。
```python
object.__dict__
dir(object)
```





