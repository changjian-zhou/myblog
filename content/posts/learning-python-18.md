---
title: "Learning Python 18"
date: 2024-09-19T16:07:21+08:00
draft: false
tags:
  - Python
---

# 参数

参数是通过赋值来传递的。

## 传递参数
- 参数的传递是通过自动将对象赋值给本地变量名来是实现的
- 在函数内部的参数名的赋值不会影响调用者
- 改变函数的可变对象参数的值也许会对调用者有影响

## 参数和共享引用
```python
def changer(a, b):
    a = 2
    b[0] = 'spam'
X = 1
L = [1, 2]
changer(X, L)
print(X, L)
1 ['spam', 2]
```
## 特定的参数匹配模型
### 收集参数
*args：用于接收任意数量的未命名位置参数。它将所有这些参数作为元组传递给函数。

**kwargs：用于接收任意数量的关键字参数。它将所有这些参数作为字典传递给函数。
```python
def f(a, *args, **kargs):
    print(a, args, kargs)

f(1,2,3,x=1,y=2)
# 1 (2, 3) {'x': 1, 'y': 2}
```
### 解包参数

可以使用 * 和 ** 解包列表或字典，将其传递给函数。
```python
def func(a,b,c,d):
    print(a,b,c,d)
func(*(1,2),**{'d':4,'c':4})
```

### Keyword-only
在参数列表中使用 * 后，所有后续参数都必须作为关键字参数传递，不能通过位置传递。
```python
def greet(name, *, age):
    print(f"Hello, {name}. You are {age} years old.")

greet("Alice", age=30)  # 正确
# greet("Alice", 30)  # 错误： age必须通过关键字参数传递
```

