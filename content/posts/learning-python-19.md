---
title: "Learning Python 19"
date: 2024-09-20T11:19:15+08:00
draft: false
tags:
  - Python
---

# 函数的高级话题

## 函数设计概念
- 耦合性：对于输入使用参数并且对于输出使用return语句（函数的参数和返回值应该清晰明了，避免混淆）。
- 耦合性：只有在真正必要的情况下使用全局变量。
- 耦合性：不要改变可变类型的参数，除非调用者希望这么做。
- 聚合性：每一个函数都应该有一个单一的、统一的目标。
- 大小：每一个函数应该相对较小。
- 耦合：避免直接改变在另一个模块文件中的变量。


## 递归函数
递归函数是直接或间接地调用自身以进行循环的函数。

递归可以要求遍历任意形状的结构。

```python
def mysum(L):
    if not L:
        return 0
    else:
        return L[0] + mysum(L[1:])

mysum([1,2,3,4,5])
# 15
```
## 函数对象：属性和注解

函数是第一类对象，这意味着函数可以像其他对象一样被传递、赋值和操作。函数对象具有一些属性和可以使用注解（Annotations）来提供额外的信息。

```python
def greet():
    pass

print(greet.__name__)  # 输出: greet
```

函数注解用于为函数的参数和返回值提供类型提示或其他元数据。它们不会影响函数的实际运行，但可以用于静态类型检查和文档生成。

```python
def greet(name: str, age: int) -> str:
    return f"Hello, {name}. You are {age} years old."

print(greet.__annotations__)
# 输出: {'name': <class 'str'>, 'age': <class 'int'>, 'return': <class 'str'>}
```


## 匿名函数：lambda
lambda表达式用于创建简短的匿名函数，通常用于需要函数对象的场景，但不想显式定义函数。

```python
add = lambda x, y: x + y
print(add(2, 3))  # 输出: 5
```

## map
map函数用于将一个函数应用于可迭代对象的每个元素，返回一个迭代器。

```python
numbers = [1, 2, 3, 4]
squared = list(map(lambda x: x ** 2, numbers))
print(squared)  # 输出: [1, 4, 9, 16]
```

## 函数式编程工具：filter和reduce
filter函数用于筛选可迭代对象中的元素，返回满足条件的元素组成的迭代器。
```python
numbers = [1, 2, 3, 4, 5, 6]
even_numbers = list(filter(lambda x: x % 2 == 0, numbers))
print(even_numbers)  # 输出: [2, 4, 6]
```
reduce函数用于对可迭代对象的元素进行累积操作，最终返回一个单一的值。reduce在Python 3中被移到了functools模块中。
```python
from functools import reduce

numbers = [1, 2, 3, 4]
total = reduce(lambda x, y: x + y, numbers)
print(total)  # 输出: 10
```


