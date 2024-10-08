---
title: "Learning Python 30"
date: 2024-09-30T09:03:53+08:00
draft: false
tags:
  - Python
---

# 类的设计

## Python和OOP
Python的OOP实现可以概括为三个概念：
- 继承：继承是基于Python中的属性查找的（在X.name表达式中）。
- 多态：在X.method方法中，method的意义取决于x的类型（类）。
- 封装：方法和运算实现行为，数据隐藏默认是一种惯例。

> 类可以表示任何用一句话表达的对象和关系。只要用类取代名词，用方法取代动词。


## OOP和委托：“包装”对象
委托就是指控制器对象内嵌其他对象，而把运算请求传给那些对象。

## 类的伪私有属性
class语句内开头有两个下划线，但结尾没有两个下滑线的变量名会扩张，从而包含了所在类的名称。像Spam类内__X这样的变量名会自动变成_Spam__X。

## 方法是对象：绑定或无绑定
当方法在对象实例上被调用时，它们是绑定方法；当方法通过类本身来访问时，它们是无绑定方法。

```python
class MyClass:
    def greet(self):
        print("Hello from", self)

# 创建一个实例
x = MyClass()

# 绑定方法
x.greet()  # 输出: Hello from <__main__.MyClass object at 0x...>

# 无绑定方法的调用
MyClass.greet(x)  # 输出: Hello from <__main__.MyClass object at 0x...>
```
## 多重继承：“混合”类
多重继承：类和其实例继承了列出的所有超类的变量名。

## 类是对象：通用对象的工厂
工厂：把类传给会产生任意种类对象的函数




