## Python基础(第三天)

*  学习目录
> * 序列
> * 元组
> * 列表
> * 字典
> * 字典练习

---
## 0x01 序列
> * 序列介绍
```
1、字符串、列表和元组都是序列
2、特点：索引和切片操作
   --  索引: 从序列中抓取特定项目
   --  切片：获取系列的一个切片，即一部分序列
```
> * 基本操作
```
len()          # 获取序列长度
+              # 链接2个序列
*              # 重复序列元素
in             # 判断元素是否在序列中存在
max()          # 最大值
min()          # 最小值
cmp(x, y)      # 比较两个序列是否相等
```

* Example:
```
In [15]: a = 'dasfsdae'       # 定义字符串变量
In [16]: len(a)               # 获取长度
Out[16]: 8

In [17]: a + 'dafsa'          # 字符串连接
Out[17]: 'dasfsdaedafsa'

In [21]: a = 'a'
In [22]: a * 5                # 重复前面字符5次(包含关系)
Out[22]: 'aaaaa'

In [31]: a = 'dsafdefdas'
In [32]: 'de' in a            # 判断在序列内
Out[32]: True

In [31]: a = 'dsafdefdas'
In [32]: 'xyz' in a            # 判断不在在序列内
Out[32]: False

In [37]: a = (12, 3, 10)
In [38]: max(a)               # 最大值
Out[38]: 12
In [39]: min(a)               # 最小值
Out[39]: 3

In [56]: help(cmp)            # 获取cmp() 函数帮助
cmp(...)
    cmp(x, y) -> integer

In [52]: cmp(10, 20)          # 比较两个对象， 大于为：-1  小于为：1
Out[52]: -1
In [53]: cmp(30, 10)
Out[53]: 1
```

## 0x02  元组
> * 与列表相似   
> * 与字符串一样，`不可变`
    --- 元祖标识符 `()` 括号标识 ，元素之间由`,` 逗号隔开   
    --- 可以存储一系列值  
    --- 元祖的值不会改变  

* Example: 定义元组
```
In [57]: a = ('a', 'b', 'c')   # 定义元祖
In [58]: a
Out[58]: ('a', 'b', 'c')
In [59]: type(a)               # 查看类型
Out[59]: tuple
In [60]: a[1] = 11             # 元组值不可变，报错
TypeError: 'tuple' object does not support item assignment
```
> * 元组操作
    --- 属于序列类型，可通过索引和切片操作
    --- 值 不可变

> * 元组拆分

* Example: 定义元组
```
In [63]: a = ('x', 11, [1, 2, 3])      # 定义变量, 元素包含 字符串、整数、列表
In [64]: t = (a, 'b', 'c')             # 定义元组，调用变量a
In [65]: t
Out[65]: (('x', 11, [1, 2, 3]), 'b', 'c')     # 可见，变量发生改变
```
* Example: 通过变量接收元组值
```
In [65]: t
Out[65]: (('x', 11, [1, 2, 3]), 'b', 'c')
In [66]: first, second, third = t       # 分别把变量t的元素进行赋值
In [67]: first                          # 调用打印值
Out[67]: ('x', 11, [1, 2, 3])
In [68]: second
Out[68]: 'b'
In [69]: third
Out[69]: 'c'
```
* Example: 查看元组对象方法
```
In [70]: dir(t)         # 获取元组属性
Out[70]:
['__add__',             # 内置方法
 '__class__',
 '__contains__',
 '__delattr__',
 '__doc__',
 '__eq__',
 '__format__',
 '__ge__',
 '__getattribute__',
 '__getitem__',
 '__getnewargs__',
 '__getslice__',
 '__gt__',
 '__hash__',
 '__init__',
 '__iter__',
 '__le__',
 '__len__',
 '__lt__',
 '__mul__',
 '__ne__',
 '__new__',
 '__reduce__',
 '__reduce_ex__',
 '__repr__',
 '__rmul__',
 '__setattr__',
 '__sizeof__',
 '__str__',
 '__subclasshook__',
 'count',                    # 元组方法
 'index']
```
* Example: 获取元组方法属性帮助
```
In [71]: help(t.count)       # 获取count方法的属性
count(...)
    T.count(value) -> integer -- return number of occurrences of value
In [79]: help(t.index)
    T.index(value, [start, [stop]]) -> integer -- return first index of value.
Raises ValueError if the value is not present.     # 返回值索引
```
* Example: 返回值是否在元组内  
  --- 1   表示为存在元素  
  --- 0   表示为不是单个元素，即使字符包含在值内  
```
In [75]: t = (11, 'dasfsab', 'zdsfdc', 'c')
In [76]: t.count('c')         # 返回值是否为元组内元素
Out[76]: 1
In [77]: t.count('sf')        # sf为元素内的字符
Out[77]: 0
In [78]: t.count('dasfsda')   # 不存在元素
Out[78]: 0
In [84]: t.index('c')         # 获取值'c'在列表内的元素下标
Out[84]: 3                    
```

## 0x03  列表
> * 处理一组有序项目数据结构  
> * `可变`数据类型  
> * 列表标识 `[]` 中括号

* Example: 创建列表
```
In [87]: l = []              # 空列表
In [88]: l = list()          # 空列表
# 定义包含字符串、元组、列表、字典的列表
In [89]: l = l = ['a', 1, ('ab', 15), [11, 'dsa'], {'name': 'Chow', 'age': 26}]
```
* Example: 连接列表
```
In [100]: a1 = [1, 2, 3]
In [101]: a2 = [4, 5, 6]
In [102]: a1 + a2
Out[102]: [1, 2, 3, 4, 5, 6]
```
> * 列表操作
    --- 取值 -> 切片和索引
    --- 添加 -> append() 方法
    --- 删除 -> del remove() 及 pop() 方法
    --- 修改 -> 赋值
    --- 查找 -> in 或 not in

* Example: 追加元素
```
In [103]: a3 = a1 + a2
In [104]: a3.append('Chow')      # 在列表内追加元素
In [105]: a3
Out[105]: [1, 2, 3, 4, 5, 6, 'Chow']
```
* Example: 删除元素   
```
In [105]: a3
Out[105]: [1, 2, 3, 4, 5, 6, 'Chow']
In [106]: del a3[-2]              # 删除元素
In [107]: a3
Out[107]: [1, 2, 3, 4, 5, 'Chow']

In [108]: a3.remove(3)            # 移除指点元素
In [109]: a3
Out[109]: [1, 2, 4, 5, 'Chow']

In [110]: a3.pop()                # 删除列表内最后一位元素
Out[110]: 'Chow'
In [111]: a3
Out[111]: [1, 2, 4, 5]

In [122]: a3 = [1, 2, 4, 5]      # 删除指定下标元素
In [123]: a3.pop(2)
Out[123]: 4
In [124]: a3
Out[124]: [1, 2, 5]
```
* Example: 判断元素是否在列表内，返回值为True 或 False
```
In [112]: a = [1, 2, 3, 4, 5, 6, 'Chow']
In [113]: 'Chow' in a             # 元素在列表内
Out[113]: True
In [114]: 'dasfds' in a           # 元素不在列表内
Out[114]: False
In [115]: 'dfafsde' not in a      # 元素不在列表内， not in
Out[115]: True
```
* Example: 插入元素
```
In [116]: a = [1, 2, 3, 'Chow']
In [117]: a.insert(1, 'Robin')     # 在列表下标1的位置插入字符串
In [118]: a
Out[118]: [1, 'Robin', 2, 3, 'Chow']
```
* Example: 反转
```
In [119]: a.reverse()              #  反转列表
In [120]: a
Out[120]: ['Chow', 3, 2, 'Robin', 1]
```
* Example: 迭代对象(扩展)
```
In [127]: a1 = [1, 2, 5]
In [128]: a1.extend(range(10))     # range() 生成元素并扩展到列表
In [129]: a1
Out[129]: [1, 2, 5, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

## 0x04  字典
> * zip() 函数，返回列表元组  
> * python中唯一的映射类型(哈希表)  
> * 可变类型， 字典的键必须不可变  
> * 字典中可以使用不同类型的键值   
> * 字典方法  
     --- keys()     # 返回字典内的key  返回列表格式     
     --- values()   # 返回字典内的value  列表格式  
     --- items()    # 把字典转换成列表  
     --- get(k[,d])    # 判断`k`在字典里 ，返回指定值d , 不在，返回 `None`  
> * in 或 not in 在字典内用法
> * copy()          # 浅拷贝   
> * update()        # 更新字典
> * fromkeys(S[,v])    # 往字典中添加新元素
> * for 循环遍历字典内的key
> * 字典练习

* Example: zip() 用法
```
In [131]: l1 = ['name', 'Chow']
In [132]: l2 = ['age', 26]
In [133]: zip(l1, l2)                # 合并两个列表
Out[133]: [('name', 'age'), ('Chow', 26)]
```

* Example:  创建空字典
```
In [134]: dic = {}
In [135]: type(dic)
Out[135]: dict

In [178]: dict(a=10, b='abc')
Out[178]: {'a': 10, 'b': 'abc'}
```
* Example:  创建有值字典
```
In [137]: dic = {'name': 'Chow', 'age': 30}
In [138]: dic
Out[138]: {'age': 30, 'name': 'Chow'}
```
* Example:  创建包含元组及列表字典
```
In [139]: dic = {'name': 'Chow', 'age': [11, 21], ('a', 'b'): 'Robin'}
In [140]: dic
Out[140]: {'age': [11, 21], 'name': 'Chow', ('a', 'b'): 'Robin'}
In [141]: len(dic)                   # 查看字典长得
Out[141]: 3
```
* Example: 字典的方法使用
```
In [142]: dic.keys()                  # 返回字典内的key
Out[142]: [('a', 'b'), 'age', 'name']
In [143]: dic.values()                # 返回字典内的value
Out[143]: ['Robin', [11, 21], 'Chow']
In [144]: dic.items()                 # 把字典
Out[144]: [(('a', 'b'), 'Robin'), ('age', [11, 21]), ('name', 'Chow')]
In [148]: dic.get('name')             # 判断key对应字典里的值
Out[148]: 'Chow'
In [149]: dic.get('name12')           # 值不存在，返回None
In [152]: dic.get('name12', 'Python') # 当值不存在时， 返回指定的值
Out[152]: 'Python'
```
* Example: 修改字典值
```
In [150]: dic['age'] = 20             # 修改字典值
In [151]: dic
Out[151]: {'age': 20, 'name': 'Chow', ('a', 'b'): 'Robin'}
```
* Example: 判断是是否在字典内
```
In [153]: 'age' in dic                # 值在字典内
Out[153]: True
In [154]: 'name1' in dic              # 值在字典内不存在     
Out[154]: False
In [155]: 'name1' not in dic          # 不存在的值不在字典内
Out[155]: True
```
* Example: has_key() 判断值是否在字典内
```
In [156]: dic.has_key('age')
Out[156]: True
In [157]: dic.has_key('age1')
Out[157]: False
```
* Example: items()用法
```
In [158]: dic.items()                  # 把字典转换成列表
Out[158]: [(('a', 'b'), 'Robin'), ('age', 20), ('name', 'Chow')]
In [159]: dic
Out[159]: {'age': 20, 'name': 'Chow', ('a', 'b'): 'Robin'}
```
* Example: copy() 浅拷贝
```
In [160]: dic1 = dic.copy()            # 生成与旧字典相同的新字典
In [161]: dic1
Out[161]: {'age': 20, 'name': 'Chow', ('a', 'b'): 'Robin'}
```
* Example: pop() 删除字典 ，若 key不存在则报错
```
In [164]: dic
Out[164]: {'age': 20, 'name': 'Chow', ('a', 'b'): 'Robin'}
In [165]: dic.pop('age')             # 删除keys 'age'并返回值
Out[165]: 20
In [166]: dic
Out[166]: {'name': 'Chow', ('a', 'b'): 'Robin'}

In [166]: dic
Out[166]: {'name': 'Chow', ('a', 'b'): 'Robin'}
In [168]: dic.pop('age', 'KeyError')   # 若删除的key不存在，返回指定的值返回
Out[168]: 'KeyError'
```
* Example: update() 更新字典, 两个字典相加
```
In [174]: dic
Out[174]: {'name': 'Chow', ('a', 'b'): 'Robin'}
In [175]: dic1 = {'age': 15, 'sex': 'Men'}
In [176]: dic.update(dic1)            # 把dic1字典与dic字典连接
In [177]: dic
Out[177]: {'age': 15, 'name': 'Chow', 'sex': 'Men', ('a', 'b'): 'Robin'}
```
* Example: fromkeys() 创建key为指定的元素， 值为None或指定相同元素的序列
```
In [181]: dic
Out[181]: {'a': 10, 'b': 'abc'}
In [182]: dic.fromkeys('xyc')        # 分别创建key为xyc 值为None的字典
Out[182]: {'c': None, 'x': None, 'y': None}

In [183]: dic.fromkeys(range(100), 100)  # 创建key为1 - 99 ，值都为100的序列
```
* Example: for循环遍历字典
```
In [184]: dic = {'age': 15, 'sex': '男'}
In [185]: for i in dic:
     ...:     print(i)                  # 遍历key

In [186]: for k in dic:
      ...:     print(k, dic1[k])        # 遍历key及值

In [188]: for k, v in dic.items():      # 通过items()方法遍历keys及值
      ...:     print(k, v)        
```
* Example: 练习  
  --- 从键盘获取keys及value  
  --- 放入字典存放  
  --- 打印出字典中的keys及value  
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-20 22:37
# @Author  : anChow
# @File    : test.py

info = {}

name = raw_input('请输入名字: ')
age = int(input('请输入年龄: '))
gender = raw_input('请输入性别: ')

info['name'] = name
info['age'] = age
info['gender']  = gender

print(info)
print(info.items())

for k, v in info.items():       # 通过for循环遍历
    print(k, v)
```
* Example: 元组拆分
```
In [189]: a, b = ('name', '25')
In [190]: a
Out[190]: 'name'
In [191]: b
Out[191]: '25'
```
