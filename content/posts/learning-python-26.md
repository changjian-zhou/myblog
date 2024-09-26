---
title: "Learning Python 26"
date: 2024-09-26T13:59:02+08:00
draft: false
tags:
  - Python
---

# 类代码编写基础

## 类产生多个实例对象
类对象提供默认行为（函数或方法），是实例对象的工厂。

类中的函数通常成为`方法`。

```python
class FirstClass:
    def setdata(self, value):
        self.data = value
    def display(self):
        print(self.data)

y = FirstClass()
y.setdata(3.14159)     # FirstClass.setdata(y, 3.14159)
```

## 类通过继承进行定制

Python也可让类继承其他类，因而开启了编写`类层次结构`的大门，在阶层较低的地方覆盖现有的属性，让行为特定化。

## 类可以截获Python运算符

运算符重载是面向对象编程（OOP）中的一种技术，允许开发者为自定义的类定义或修改运算符的行为。
例如，当你在类实例上使用+、-、*、/等运算符时，Python允许你自定义这些运算符如何对实例进行操作。

```python
class Vector:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __add__(self, other):
        if isinstance(other, Vector):
            return Vector(self.x + other.x, self.y + other.y)
        raise ValueError("Operands must be of type Vector.")

    def __repr__(self):
        return f"Vector({self.x}, {self.y})"

# 创建两个向量实例
v1 = Vector(2, 3)
v2 = Vector(5, 7)

# 使用 + 运算符进行向量加法
result = v1 + v2
print(result)  # 输出: Vector(7, 10)
```



