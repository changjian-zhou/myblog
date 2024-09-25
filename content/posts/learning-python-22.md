---
title: "Learning Python 22"
date: 2024-09-24T14:35:19+08:00
draft: false
tags:
  - Python
---

# 模块代码编写基础

## 模块的创建
任何以'.py'为后缀所保存的文件都会被自动认为是Python的模块。

## 模块的使用
```python
import module1
from module1 import printer
from module1 import *
```

模块只会在第一次import或者from会执行。

from也总是会把整个模块导入到内存中。

## 模块命名空间
模块就是命名空间，而存在于模块内的变量名就是模块对象的属性。

## 重载模块
- 模块导入只会在模块第一次被导入时加载
- 之后的导入不会重载模块文件内部的代码
- reload函数会强制已加载的模块代码重新载入并重新执行



