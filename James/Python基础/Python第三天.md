## Python基础(第三天)

*  学习目录
> * 序列
> * 元组
> * 列表
> * 作业

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

## 0x04 作业
> * 题目
```
现有列表
list1 = ['XXXX', 'b', 3, 'c', '&', 'a', 3, '3', 3, 'aa', '3', 'XXXX']
list2 = ['e', 'f', 'g']
要求对其做以下操作：
1. 取出 ‘XXXX’ 中间的部分，形成一个新的列表list3
2. 对list3 做一下几部操作
1）删除特殊符号
2）统计 3 在list3中出现的次数
3）用最简短的代码去除list3中 26个字母以外的元素(要求只能对list3操作)
4）对list3排序
5）在末尾追加'd',并把list2追加到list3
3. 现有两个变量
a = ('h',)
b = ('h')
1）将a和b分别追加到上一题的list3中，观察有什么区别
2）将1生成的list3转换成元组(扩展：自己搜索方法)
3）打印出只有一个元素'h'的元组，在2中生成的元组中的索引
```

* Example: 取出 ‘XXXX’ 中间的部分，形成一个新的列表list3
```
In [192]: list1 = ['XXXX', 'b', 3, 'c', '&', 'a', 3, '3', 3, 'aa', '3', 'XXXX']
In [195]: list3 = list1[1:11]        #  列表切片操作
In [196]: list3
Out[196]: ['b', 3, 'c', '&', 'a', 3, '3', 3, 'aa', '3']
```
* Example: 对list3 做一下几部操作
```
# 删除特殊符号
In [199]: del list3[3]               # del实现
In [203]: list3.pop(3)               # pop() 方法
In [206]: list3.remove('&')          # remove() 方法

# 统计 3 在list3中出现的次数
In [208]: list3.count(3)             # 统计int类型
Out[208]: 3

# 用最简短的代码去除list3中 26 个字母以外的元素(要求只能对list3操作)
In [232]: list3 = ['b', 3, 'c', '&', 'a', 3, '3', 3, 'aa', '3']
In [233]: list3.remove(3)
In [235]: list3.remove('&')
In [246]: list3.pop(3)
Out[246]: '3'
In [247]: list3
Out[247]: ['b', 'c', 'a', 3, 'aa', '3']
In [248]: list3.pop(3)
Out[248]: 3
In [249]: list3
Out[249]: ['b', 'c', 'a', 'aa', '3']
In [250]: list3.pop(4)
Out[250]: '3'

# 对list3排序
In [211]: list3.sort()               # sort() 排序
In [212]: list3
Out[212]: [3, 3, 3, '&', '3', '3', 'a', 'aa', 'b', 'c']

# 在末尾追加'd',并把list2追加到list3
In [213]: list3.append('d')          # append() 追加方法
In [214]: list3
Out[214]: [3, 3, 3, '&', '3', '3', 'a', 'aa', 'b', 'c', 'd']

In [217]: list2 = ['e', 'f', 'g']
In [218]: list3 = ['b', 3, 'c', '&', 'a', 3, '3', 3, 'aa', '3']
In [219]: list3.extend(list2)        # extend() 扩展方法
In [220]: list3
Out[220]: ['b', 3, 'c', '&', 'a', 3, '3', 3, 'aa', '3', 'e', 'f', 'g']
```
* Example: 将a和b分别追加到上一题的list3中，观察有什么区别  
      ---- 现有两个变量  
           a = ('h',)  
           b = ('h')  
```
In [256]: list3 = ['b', 3, 'c', '&', 'a', 3, '3', 3, 'aa', '3']
In [257]: a = ('h',)
In [258]: b = ('h')
In [259]: list3.append(a)
In [260]: list3.append(b)
In [261]: list3
Out[261]: ['b', 3, 'c', '&', 'a', 3, '3', 3, 'aa', '3', ('h',), 'h']
```
* Example: 将上题生成的list3转换成元组(扩展：自己搜索方法)
```
In [262]: tup = tuple(list3)
In [263]: tup
Out[263]: ('b', 3, 'c', '&', 'a', 3, '3', 3, 'aa', '3', ('h',), 'h')
```
PS： 参考文档
     https://www.cnblogs.com/linjiqin/p/3674356.html  
* Example: 打印出只有一个元素'h'的元组，在b中生成的元组中的索引
```
In [274]: tup = tuple(list3)
In [275]: tup
Out[275]: ('b', 3, 'c', '&', 'a', 3, '3', 3, 'aa', '3', ('h',), 'h')
In [276]: print(tup[-1])
h

In [280]: b.index('h')                  # 获取元组下标
Out[280]: 0
```
