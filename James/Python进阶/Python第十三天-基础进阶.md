## Python基础(第十三天)

*  学习目录  

> * 内建函数

## 0x01 内建函数  
> __builtin__
>  

* Example: __builtin__
```
In [106]: __builtin__                          # 类
In [106]: help(__builtin__.all)                # 获取帮助信息
```
* Example: 官网查看
```
https://docs.python.org/2.7/library/functions.html?highlight=open#open
```
> 常用内建函数整理  
```
abs()                              # 绝对值
max()                              # 最大值
min()                              # 最小值
len()                              # 序列长度
divmod()                           # 返回两个数的商和余数，返回元组
pow()                              # 返回一个数的多少次方
round()                            # 四舍五入，返回浮点数
callable()                         # 判断是否允许被调用， 返回True及False
type()                             # 数据类型
isnstance()                        # 判断变量类型， 返回 True 及 False
cmp()                              # 比较两个值， 返回复数
range()                            # 生成序列， 返回列表
xrange()                           # 生成序列， 返回对象， 可以进行遍历操作
int()                              # 整数
long()                             # 长整数
float()                            # 浮点数
complex()                          # 复数
str()                              # 转换成字符串
list()                             # 转换成列表
tuple()                            # 转换成元组
hex()                              # 10进制转换成16进制
oct()                              # 10进制转换成8进制
chr()                              # 数值对应的ASCII
ord()                              # ASCII对应的数值
eval()                             # 将字符串当有效表达式求值
```

* Example: 内建函数实例
```
In [107]: help(abs)                 # 获取帮助

In [108]: abs(-10)                  # 绝对值
Out[108]: 10

In [109]: max('131da', '1234')      # 字符最大值
Out[109]: '131da'

In [111]: max(10, 210)              # 整数最大值
Out[111]: 210

In [112]: min(10, 210)              # 最小值
Out[112]: 10

In [114]: len('dasfsda')            # 取字序列长度
Out[114]: 7
In [115]: len([1, 2, 4])
Out[115]: 3
In [117]: len((1, 4, 5))
Out[117]: 3
In [119]: len({'name':'chow', 'age': 5})
Out[119]: 2

In [120]: divmod(5,3)               # 返回两个数的商和余数，返回元组
Out[120]: (1, 2)

In [121]: pow(2,3)                  # 返回一个数的多少次方
Out[121]: 8
In [122]: pow(2,3,4)                # 返回一个数的多少次方，除以第三个数，取余数
Out[122]: 0

In [125]: round(10.24)              # 四舍五入，返回浮点数
Out[125]: 10.0
In [126]: round(10.24000, 2)        # 四舍五入，返回浮点数， 2为保留小数点后的小数
Out[126]: 10.24

In [3]: a = '123'
In [4]: callable(a)                 # a 为字符串，不被调用
Out[4]: False

In [5]: def a():
   ...:     pass
In [6]: callable(a)                 # a 为函数，可以调用
Out[6]: True

In [7]: l = [1, 2, 3,]
In [8]: type(l)
Out[8]: list
In [9]: if type(l) == type([]):     # 判断列表是否为 空
   ...:     print(ok)

In [10]: isinstance(l, list)        # 判断定义的类是否为列表， 返回 True 和 False
Out[10]: True
In [11]: isinstance(l, str)
Out[11]: False   

In [13]: s = 'dasfsa3131'
In [14]: isinstance(s, (int, tuple, str))  # 判断变量为这几种类型中的一种
Out[14]: True

In [16]: class A(object):            # 定义类
    ...:     pass
In [17]: a = A()                     # 把类赋值给变量
In [18]: isinstance(a, A)            # 判断变量在类内
Out[18]: True

In [19]: cmp(1, 1)                  
Out[19]: 0
In [20]: cmp(1, 3)                   # 1 比 3 小
Out[20]: -1
In [21]: cmp('helload', 'dada')      # 按字符的第一个字母进行比较
Out[21]: 1

In [22]: range(10)                   # 生成序列， 返回列表
Out[22]: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
In [23]: xrange(10)                  # 生成序列， 返回对象
Out[23]: xrange(10)

In [24]: complex(12)                 # 转变成复数
Out[24]: (12+0j)
In [25]: complex('12')
Out[25]: (12+0j)

In [26]: str(123)                    # 数值转换成字符串
Out[26]: '123'
In [27]: str([1,2])                  # 列表转换成字符串
Out[27]: '[1, 2]'
In [28]: str({'1':'1'})              # 元组转换成字符串
Out[28]: "{'1': '1'}"

In [29]: list()                      # 生成空列表
Out[29]: []
In [30]: list('abc')                 # 字符串转换成列表
Out[30]: ['a', 'b', 'c']
In [31]: list('123')                 # 单是字符不能转换成列表，需要用引号
Out[31]: ['1', '2', '3']

In [32]: tuple('123')                # 字符串转换为元组
Out[32]: ('1', '2', '3')
In [33]: tuple([123,4,5])            # 列表转换为元组
Out[33]: (123, 4, 5)

In [34]: hex(10)                     # 整型转换为16进制
Out[34]: '0xa'
In [35]: hex(10L)                    # 长整型转换为16进制
Out[35]: '0xaL'

In [41]: eval(hex(10))               # 将字符串当有效表达式求值
Out[41]: 10
In [43]: eval("['a','b','1']")
Out[43]: ['a', 'b', '1']

In [44]: chr(1)                      # 数字对应的ASCII
Out[44]: '\x01'
In [45]: chr(9)
Out[45]: '\t'
In [46]: chr(94)
Out[46]: '^'
In [47]: chr(97)
Out[47]: 'a'

In [48]: ord('b')                    # ASCII对应的数值
Out[48]: 98
```
> 字符串处理函方法
```
str.capitalize()                     # 返回字符串， 首字母大写
str.replace()                        # 字符串替换
str.split()                          # 分隔字符串
str.join()                           # 字符串连接
string模块

```

* Example: 字符串方法
```
In [49]: s = 'hello'
In [52]: help(s.capitalize)
    S.capitalize() -> string
In [55]: s.capitalize()              # 字符串首字母变大写
Out[55]: 'Hello'

In [56]: help(s.replace)             # 获取帮助
    S.replace(old, new[, count]) -> string
In [57]: s.replace('hello','Hello World')    # 字符串替换
Out[57]: 'Hello World'    

In [58]: help(s.split)                # 获取帮助
    S.split([sep [,maxsplit]]) -> list of strings
In [62]: s = 'hello a\tb'             # 定义带空格字符串
In [63]: s.split()                    # 默认按空格进行切分
Out[63]: ['hello', 'a', 'b']
In [65]: s.split(' ')                 # 按空格进行切分
Out[65]: ['hello', 'a\tb']
In [67]: ip = '192.168.10.111'
In [68]: ip.split('.')                # 以 . 进行切分
Out[68]: ['192', '168', '10', '111']
In [69]: ip.split('.', 2)             # 2 为切分次数
Out[69]: ['192', '168', '10.111']


In [70]: help(s.join)
    S.join(iterable) -> string        # 可迭代对象， 返回为字符串
In [72]: s1 = 'abc'
In [73]: s1.join('123')               # 字符串连接
Out[73]: '1abc2abc3'

In [76]: ''.join([str(i) for i in range(10)])    # 生成字符串并进行连接
Out[76]: '0123456789'
In [77]: '#'.join([str(i) for i in range(10)])   # 字符串间用指定字符分割
Out[77]: '0#1#2#3#4#5#6#7#8#9'
In [78]: int(''.join([str(i) for i in range(10)]))   # 把生成的字符串转换为整型
Out[78]: 123456789
```
* Example: 字符串模块
```
In [83]: import string
In [84]: string.lowercase              # 打印所有小写
Out[84]: 'abcdefghijklmnopqrstuvwxyz'
In [86]: string.uppercase              # 打印所有大写
Out[86]: 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
In [87]: help(string.capitalize)       # 获取帮助
```

> 处理序列函数
```
filter()                               # 过滤， 返回序列元素
zip()                                  # 把多个序列组合成一个大序列变成列表
map()                                  # 调用函数对序列进行处理
reduce()                               # 调用函数对序列进行处理

```

* Example: 处理序列
```
In [88]: help(filter)
   filter(function or None, sequence) -> list, tuple, or string

In [89]: filter(None, 'abc')          # 定义为None， 不做处理
Out[89]: 'abc'
In [90]: filter(None, range(10))
Out[90]: [1, 2, 3, 4, 5, 6, 7, 8, 9]

In [91]: def f(x):                    # 对函数进行处理
    ...:     if x % 2 == 0:
    ...:         return True
In [92]: filter(f, range(10))
Out[92]: [0, 2, 4, 6, 8]

In [94]: l1 = [1,2,3]
In [95]: l2 = ['a','b','c']
In [96]: zip(l1, l2)                 # 把两个列表组合成一个大的列表
Out[96]: [(1, 'a'), (2, 'b'), (3, 'c')]
In [96]: dict(zip(l1, l2))           # 把生成的序列转换成字典
Out[97]: {1: 'a', 2: 'b', 3: 'c'}


In [103]: map(None, l1, l2, l3)      # 当列表缺少值时， 用None填充
Out[103]: [(1, 'a', 'a'), (2, 'b', 'b'), (3, 'c', None)]
In [104]: l1 = [1, 2, 3]
In [105]: def f(x):
     ...:     return x ** 2
```
* Example: map函数
```
In [106]: map(f, l1)                 # 在l1的基础上，进行传值进行乘方计算
Out[106]: [1, 4, 9]

In [107]: l1 = [1, 2, 3]
In [108]: l2 = [4, 5, 6]
In [110]: def f(x, y):
  ...:     return x * y
In [113]: map(f, l1, ls)             # 调用函数， 执行两个列表数值相乘
Out[113]: [4, 10, 18]
```
* Example: 结合lambda函数进行处理
```
In [114]: filter(lambda x: x % 2 == 0, range(10))
Out[114]: [0, 2, 4, 6, 8]

In [122]: map(lambda x,y:x*y, range(1,10),range(1,10))   # 两个序列，每个元素想乘
Out[122]: [1, 4, 9, 16, 25, 36, 49, 64, 81]

In [124]: reduce(lambda x,y:x+y, range(1,101))   # 1 - 100相加
Out[124]: 5050
```
> 列表表达式

* Example: 列表推导
```
In [125]: [i for i in range(10)]                 # 取 0 - 9 序列
Out[125]: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]


In [126]: [i*2+10 for i in range(10)]
Out[126]: [10, 12, 14, 16, 18, 20, 22, 24, 26, 28]

In [127]: [i*2+10 for i in range(10) if i % 3 == 0]
Out[127]: [10, 16, 22, 28]
```
