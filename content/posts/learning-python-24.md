---
title: "Learning Python 24"
date: 2024-09-25T13:53:34+08:00
draft: false
tags:
  - Python
---

# 高级模块话题

## 在模块中隐藏数据

把下划线放在变量名前面（例如，_X），可以防止客户端使from *语句导入模块名时，把其中的那些变量名复制出去。

在模块顶层(__init__文件)把变量名的字符串列表赋值给__all__，from *语句便只会把__all__中的变量名复制出来。

## 修改模块的搜索路径
- 修改sys.path的内置列表（临时）/root/anaconda3/envs/pytorch/lib/python3.12/site-packages/torch
- 修改PYTHONPATH和.pth文件路径配置（永久）

## import和from语句的as扩展
```python
import modulename as name
from reallylongmodulename import attrname as name
```

## 用名称字符串导入模块

```python
modname = 'string'
exec('import' + modname)

string = __import__(modname)
```

## 过渡性模块重载

如果要重载某个模块A,并且A中导入了模块B和C,重载只适合A,而B和C没有进行重载。

## from复制变量名，而不是连接
from导入变量名，会得到变量名的拷贝，而不是对变量名进行连接。

import可以进行连接，使用点号（A.B）运算。

不要让reload和from同时使用，会出问题。


