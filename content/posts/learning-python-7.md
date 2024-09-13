---
title: "Learning Python 7"
date: 2024-09-11T18:27:37+08:00
draft: false
tags:
  - Python
---

# 字符串
字符串可以用来表示能够像文本那样编辑的任何信息。

## 基本操作
```python
len('abc')
'abc' + 'def'
'Ni!' * 4
```
完整形式的分片是`X[I:J:K]`，这表示索引X对象中的元素，从偏移为I直到偏移为J-1,每隔K元素索引一次。

`S[::-1]`是将序列进行了反转。


## 字符串代码转换
`ord()`函数可以将单个字符转换称ASCII码，即对应字符的二进制值，`chr()`函数将获取的ASCII码转换成对应的字符。
```python
ord('s')
chr(115)
```
## 字符串方法实例：修改字符串
字符串是不可变的，可以通过分片和合并建立新的字符串。
```python
'SPAM'.join(['eggs', 'sausage', 'ham'])
'eggsSPAMsausageSPAMham'
```
## 字符串方法实例：文本解析
解析是只要需要的数据组件。
```python
line = 'aaa bbb ccc'
cols = line.split()
['aaa', 'bbb', 'ccc']
```


## 字符串格式化表达式
```python
'That is %d %s bird!' % (1, 'dead')
```
## 基于字典的字符串格式化
```python
'%(n)d %(x)s' % {'n':1, 'x':'spam'}

reply = '''
Greetings...
Hello %(name)s!
Your age squared is %(age)s
'''
values = {'name' : 'Bob', 'age' : 40}
print(reply % values)
```
## 字符串格式化调用方法
```python
template = '{0}, {1}, {2}'
template.format('spam', 'ham', 'eggs')

template='{motto}, {pork}, and {food}'
template.format(motto='spam', pork='ham', food='eggs')
```
## 同样分类的类型共享其操作集合
- `数字`

支持加法和乘法等
- `序列`（字符串、列表、元组）

支持索引、分片和合并等。
- `映射`（字典）

支持通过键的索引等

## 可变类型能够在原处修改
- 不可变类型（数字、字符串、元组、不可变集合）
- 可变类型（列表、字典、可变集合）
