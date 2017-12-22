## Python基础(第三天)

*  学习目录
> * 字典
> * 字典练习

---
## 0x01  字典
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

for k, v in info.items():       
    print('%s： %s' % (k, v))   # 字符串格式化输出
```
* Example: 元组拆分
```
In [189]: a, b = ('name', '25')
In [190]: a
Out[190]: 'name'
In [191]: b
Out[191]: '25'
```

## 0x02  作业
> * 题目
```
1. 现有一个字典dict1 保存的是小写字母a-z对应的ASCII码
dict1 = {'a': 97, 'c': 99, 'b': 98, 'e': 101, 'd': 100, 'g': 103, 'f': 102, 'i': 105, 'h': 104, 'k': 107, 'j': 106, 'm': 109, 'l': 108, 'o': 96, 'n': 110, 'q': 113, 'p': 112, 's': 115, 'r': 114, 'u': 117, 't': 116, 'w': 119, 'v': 118, 'y': 121, 'x': 120, 'z': 122}

1） 将该字典按照ASCII码的值排序
2） 有一个字母的ASCII错了，修改为正确的值，并重新排序

2. 用最简洁的代码，自己生成一个大写字母 A-Z 及其对应的ASCII码值的字典dict2(使用dict，zip，range方法)
3. 将dict2与第一题排序后的dict1合并成一个dict3
```

* Example: 将该字典按照ASCII码的值排序
```
In [312]: sorted(dict1.items())
Out[312]:
[('a', 97),
 ('b', 98),
 ('c', 99),
 ('d', 100),
 ('e', 101),
 ('f', 102),
 ('g', 103),
 ('h', 104),
 ('i', 105),
 ('j', 106),
 ('k', 107),
 ('l', 108),
 ('m', 109),
 ('n', 110),
 ('o', 96),
 ('p', 112),
 ('q', 113),
 ('r', 114),
 ('s', 115),
 ('t', 116),
 ('u', 117),
 ('v', 118),
 ('w', 119),
 ('x', 120),
 ('y', 121),
 ('z', 122)]
 ```
 PS： 参考文档
      http://blog.csdn.net/tangtanghao511/article/details/47810729

* Example: 将该字典按照ASCII码的值排序
```    
In [318]: dict1['o'] = 111

In [319]: dict1
Out[319]:
{'0': 111,
 'a': 97,
 'b': 98,
 'c': 99,
 'd': 100,
 'e': 101,
 'f': 102,
 'g': 103,
 'h': 104,
 'i': 105,
 'j': 106,
 'k': 107,
 'l': 108,
 'm': 109,
 'n': 110,
 'o': 111,                   # 已修改
 'p': 112,
 'q': 113,
 'r': 114,
 's': 115,
 't': 116,
 'u': 117,
 'v': 118,
 'w': 119,
 'x': 120,
 'y': 121,
 'z': 122}
```
* Example: 用最简洁的代码，自己生成一个大写字母 A-Z 及其对应的ASCII码值的字典dict2(使用dict，zip，range方法)  
```  
# 方法一(同事思考)
In [368]: import string
In [369]: dict2  = {(key： ord(key)) for key in string.uppercase}
In [370]: dict2
Out[370]:
{('A', 65),
 ('B', 66),
 ('C', 67),
 ('D', 68),
 ('E', 69),
 ('F', 70),
 ('G', 71),
 ('H', 72),
 ('I', 73),
 ('J', 74),
 ('K', 75),
 ('L', 76),
 ('M', 77),
 ('N', 78),
 ('O', 79),
 ('P', 80),
 ('Q', 81),
 ('R', 82),
 ('S', 83),
 ('T', 84),
 ('U', 85),
 ('V', 86),
 ('W', 87),
 ('X', 88),
 ('Y', 89),
 ('Z', 90)}

# 自己思考的方法
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-22 10:37
# @Author  : anChow
# @File    : test.py

import string
import random

str = string.uppercase
num = range(65, 90)               # 方向有无

dict1 = {}
for i in str:
    dict1[i] = ord(i)
    # print('%s : %d' % (i, ord(i)))

print(dict1)
```
PS： 参考文档
     http://blog.csdn.net/mtbaby/article/details/54907454
     https://www.cnblogs.com/diaosir/p/6575891.html
* Example: 将dict2与第一题排序后的dict1合并成一个dict3
```  

```
