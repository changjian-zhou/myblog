---
title: "Learning Python 29"
date: 2024-09-29T14:49:50+08:00
draft: false
tags:
  - Python
---

# 运算符重载

## 基础知识
运算符重载只是意味着在类方法中拦截内置的操作。

- 运算符重载让类拦截常规的Python运算。
- 类可重载所有Python表达式运算符。
- 类也可重载打印、函数调用、属性点号运算等内置运算。
- 重载使类实例的行为像内置类型。
- 重载是通过提供特殊名称的类方法来实现的。

## 索引和分片：__getitem__
当实例X出现在X[i]这样的索引运算中时，Python会调用这个实例继承的__getitem__方法，把X作为第一个参数传递，并且方括号内的索引值传给第二个参数。

## 迭代器对象：__iter__和__next__
```python
class Squares:
    def __init__(self,start,stop):
        self.value = start - 1
        self.stop = stop
    def __iter__(self):
        return self
    def __next__(self):
        if self.value == self.stop
            raise StopIteration
        self.value += 1
        return self.value ** 2
```

## 成员关系：__contains__、__iter__、__getitem__
出现in时，通常能够优先级：__contains__>__iter__>__getitem__

__getitem__方法更通用，但有时__iter__更容易编写

## 属性引用：__getattr__和__setattr__
__getattr__方法是拦截属性点号运算。当通过对不存在属性名称和实例进行点号运算时，就会用属性名称作为字符串调用这个方法。


__setattr__会拦截所有属性的赋值语句。

## __repr__和__str__会返回字符串表达形式
当类的实例打印或转换成字符串时__repr__或__str__就会自动调用。

__repr__ 在调用 repr() 函数、解释器中查看变量、或用于调试时被调用。

__str__ 在调用 str() 函数或使用 print() 打印对象时被调用。

> 为了确保一个定制显示在所有环境中都显示而不管容器是什么，编写__repr，而不是__str__。

## 右侧加法和原处加法：__radd__和__iadd__
__radd__ 用于处理加法中的反向操作，通常用于当左操作数不知道如何处理右操作数时。

__iadd__ 用于就地加法操作，即用 += 来对对象进行修改。

5 + num 触发了 __radd__，而 num += 5 触发了 __iadd__

## Call表达式：__call__

__call__ 是 Python 中的一个特殊方法（也称为魔术方法），它使一个类的实例能够像函数一样被调用。这意味着你可以在实例后加上括号，并传递参数，就像调用函数一样。

```python
class Adder:
    def __init__(self, increment):
        self.increment = increment

    def __call__(self, value):
        return value + self.increment

add_5 = Adder(5)
print(add_5(10))  # 输出: 15
print(add_5(20))  # 输出: 25
```
## 比较：__lt__、__gt__和其他方法

__lt__ 和 __gt__ 是 Python 中的两个特殊方法，用于定义对象之间的比较运算，分别表示小于 (<) 和大于 (>) 运算符的行为。

## 布尔测试：__bool__和__len__

__bool__ 和 __len__ 是 Python 中的两个特殊方法，它们分别用于确定对象的布尔值和返回对象的长度。

如果一个对象没有定义 __bool__ 方法，但定义了 __len__ 方法，Python 会根据 __len__ 的返回值来判断对象的布尔值：如果 __len__ 返回 0，对象为假，否则为真。

## 对象析构函数：__del__

__del__ 是 Python 中的一个特殊方法，用于定义对象的析构函数（也称为终结方法）。
当对象的生命周期结束、被垃圾回收机制回收时，Python 会调用 __del__ 方法。它通常用于清理资源，例如关闭文件、释放网络连接等。

