---
title: "Learning Python 31"
date: 2024-10-08T11:46:07+08:00
draft: false
tags:
  - Python
---

# 类的高级主题

## 扩展内置类型
除了实现新的种类的对象以外，类偶尔也用于扩展Python的内置类型的功能，从而支持更另类的数据结构。

## 新式类
Python 3.X中所有的类都是新式类。

类自身就是类型：type对象产生类作为自己的实例，并且类产生它们的类型的实例。

类现在就是类型，并且一个实例的类型是该实例的类。

类型检查中isinstance内置函数很可能是在极少数情况下想要使用的。

## 钻石继承变动
Python先寻找第一个搜索的右侧的所有超类，然后才一路往上搜索至顶端共同的超类。换句话说，搜索过程先水平进行，然后向上进行。

可以通过赋值或者在类混合处指出想要的变量名以解决继承不明的问题。

## slots实例
如有有__slots__这个运算符重载，只有__slots__列表内的这些变量名可赋值为实例属性。

## 静态方法和类方法

静态方法和类方法是两种特殊的类方法类型，分别通过 @staticmethod 和 @classmethod 装饰器来定义。


定义静态方法
```python
class MyClass:
    @staticmethod
    def static_method():
        print("This is a static method.")

# 通过类调用静态方法
MyClass.static_method()  # 输出: This is a static method

# 也可以通过实例调用
obj = MyClass()
obj.static_method()  # 输出: This is a static method
```

定义类方法
```python
class MyClass:
    class_attribute = 0

    @classmethod
    def class_method(cls):
        cls.class_attribute += 1
        print(f"Class attribute is now {cls.class_attribute}")

# 通过类调用类方法
MyClass.class_method()  # 输出: Class attribute is now 1

# 通过实例调用类方法
obj = MyClass()
obj.class_method()  # 输出: Class attribute is now 2
```

## 装饰器和元类
装饰器用于函数或类的行为增强，而元类则是用于创建或修改类本身的行为。


```python
def my_decorator(func):
    def wrapper():
        print("Something before the function.")
        func()
        print("Something after the function.")
    return wrapper

@my_decorator
def say_hello():
    print("Hello!")

# 调用被装饰的函数
say_hello()
```

当 @my_decorator 被应用到 say_hello 函数时，Python 相当于将 say_hello 替换为 my_decorator(say_hello)。


