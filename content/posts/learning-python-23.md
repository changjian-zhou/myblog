---
title: "Learning Python 23"
date: 2024-09-24T17:01:26+08:00
draft: false
tags:
  - Python
---

# 模块包
模块（Module）是Python中组织代码的基本单元，通常对应于一个以.py为后缀的文件，模块内部包含Python代码、函数、类、变量等。

包（Package）是一个包含多个模块的文件夹（目录），并且该文件夹下有一个特殊的__init__.py文件。包允许模块的层次结构组织，可以方便地管理和分发大型项目中的代码。

## 包导入基础
```python
import dir1.dir2.mod
from dir1.dir2.mod import x
```
容器目录dir0需要添加在模块搜索路径中。

在Python包中，`__init__.py`文件起着两个主要作用：
- 标记目录为Python包
- 初始化包


## 包导入实例
import语句会在每个目录首次遍历时，执行该目录的初始化文件。

```python
from dir1.dir2.mod import x
```
上述使用from语句，可以避免每次读取时都得重新输入路径。


## 为什么要使用包导入
包让导入更具信息性，并可以作为组织工具，简化模块的搜索路径，而且可以解决模糊性。

> 作为组织工具的意思是可以根据功能把文件组织成子目录，让同一大类的模块都在一起;解决模糊性就是指导入的文件可以更明确，解决多个同名程序文件安装在同一个机器上。

## 包相对导入
import为绝对导入，在sys.path所包含的绝对目录中查找。

位于某个A.B.C中的代码可以做下面的任何一种相对导入。
```python
from . import D        # import A.B.D(.means A.B)
from .. import E       # import A.E(..means A)

from .D import X       # import A.B.D.X(.means A.B)
from ..E import X      # import A.E.X(..means A)
```
## 模块的查找规则
- 简单模块名通过搜索sys.path路径列表上的每个目录来查找，从左到右进行。
- 包是一个带有__init__.py文件的Python模块的直接目录。
- 在一个包文件中，常规的import语句使用和其他地方的导入一样的sys.path搜索规则。




