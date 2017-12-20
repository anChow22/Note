## Python基础(第二天)

* 学习目录  
> 文件类型  
> 变量
> 数值和字符串

一、Python的文件类型  
1、扩展名  
2、编写脚本，实现输出

* 扩展名  
> * py扩展名,由Python程序解释，不需要编译  
> * pyc扩展名，源码文件经过编译后生成的扩展名  
> * pyo扩展名，经过优化后的源码文件

* Example: 创建py文件
```
# vim hello.py

#!//usr/bin/env python
# -*- conding:utf-8 -*-                # 指定字符编码

print “Hello World”                    # 打印输出

# python ./hello.py                    # 运行行脚本
```

* Example:  编译生成pyc文件
```
# vim hello.py

#!//usr/bin/env python
# -*- conding:utf-8 -*-

import py_compile                     # 导入编译模块

py_compile.compile('hello.py')        # 调用编译模块compile()方法      
```

* Example:  查看编译后的文件信息
```
file hello.py
```

* Example: 生成pyo文件
```
python -O -m py_compile hello.py
```
PS：执行脚本方式
   * 进入脚本存放目录执行脚本
   * 全路径执行脚本
   * 给脚本赋予执行权限,执行脚本


二、变量
1、变量命名
2、变量赋值
3、运算符与表达式

* 变量命名  
  -- 由字母、数字、下划线组成  
  -- 不能与数字开头  
  -- 不能使用关键字

* 变量赋值  
  -- 变量的声明和定义过程  

* Example: 变量赋值
```
# name1 = 10
# name2 = name1
# print("name1的值为：",name1)
# print("name2的值为：",name2)

输出结果
name1的值为： 10
name2的值为： 10
```

* Example: 通过ID查看内存值
```
# name1 = 10
# name2 = name1
# print("name1的值为：",id(name1))
# print("name2的值为：",id(name2))

输出结果
name1的值为： 1676475168   
name2的值为： 1676475168
```
PS：
  通过ID可以查看name1和name2在内存中的值相同

* Example:  重新赋值变量
```
# name1 = 10
# name2 = name1
# name1 = 100                                # name1重新赋值后
# print("name1的值为：",name1)
# print("name2的值为：",name2)
# print("重新赋值后name1的值为：",name1)

输出结果
name1的值为： 100                             # 值已更新
name2的值为： 10                              # 值未变
重新赋值后name1的值为： 100
```

* Example: id查看内存值
```
# name1 = 10
# name2 = name1
# name1 = 100
# print("name1的值为：",id(name1))
# print("name2的值为：",id(name2))
# print("重新赋值后name1的值为：",id(name1))

输出结果
name1的值为： 1676478048                      # 重新赋值后，内存值发生改变
name2的值为： 1676475168                      # 内存值未发生改变
重新赋值后name1的值为： 1676478048   
```

* Example: 查看字符是否是关键字
```
>>> keyword.iskeyword('False')
True
>>> keyword.iskeyword('for')
True
>>> keyword.iskeyword('else')
True
>>> keyword.iskeyword('in')
True
>>> keyword.iskeyword('aaa')                 # 不是关键字
False
>>> keyword.iskeyword('ccc')                 # 不是关键字
False
```
PS：
   python中，为系统关键字为True,不是系统关键字为False


* 运算符与表达式
> * 运算符
  -- 赋值运算符
  -- 算术运算符
  -- 关系运算符
  -- 逻辑运算符
> * 表达式
  -- 将不同的数据(包括变量、函数)用运算符号按一定规则连接起来的一种式子

* 赋值运算符
```
=         # 赋值
+=        # 在变量值上做加法运算
-=        # 在变量值上做剑法运算
*=        # 在变量值上做乘法运算
/=        # 在变量值上做除法运算
%=        # 在变量值上做取余运算
```
* 算术运算符
```
+         # 加
-         # 减
*         # 乘
/         # 除
//        # 整除
%         # 取余
**        # 乘方
```
* 关系运算符
```
>          # 大于
<          # 小于
>=         # 大于等于
<=         # 小于等于
==         # 等于
!=         # 不等于
```
PS:
  该运算符的值为: True 和 False  

* 逻辑运算符
```
and        # 与         True and False
or         # 或         False or True
not        # 非         not True
```

* Example: type()查看变量类型
```
In [1]: x = 'Chow'
In [2]: type(x)
Out[2]: st
```
* 运算符优先级
```
Lambda --> 逻辑运算符(or) --> 逻辑运算符(and) --> 逻辑运算符(not) --> 成员测试(in， not in) --> 同一性测试(is, is not) --> 比较运算符 --> 按位或(|) --> 按位异或(^) --> 按位与(&) --> 移位(<< , >>) --> 加法与减法 --> 乘法、除法(/)、取余(%) --> 正负号(+x , -x) --> 按位翻转(~x) --> 指数(**)             
```


作业：  
    -- 要求从键盘读取数字

* Example: 写一个四则运算符    
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-19 22:40
# @Author  : anChow
# @File    : test.py

a = int(input("请输入第一个数字: "))
b = int(input("请输入第二个数字: "))

print("a + b = %s" %(a + b))
print("a - b = %s" %(a - b))
print("a * b = %s" %(a * b))
print("a / b = %s" %(a / b))
```

* Example: 在未看视频前写出来
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-19 22:40
# @Author  : anChow
# @File    : test.py

a = int(input("请输入第一个数字: "))
b = int(input("请输入第二个数字: "))
c = int(input("请输入第三个数字: "))
d = int(input("请输入第四个数字: "))

num = a + b * c / d
print("计算的结果为: %s" %num)
```
PS：input() 与 raw_input() 区别  
     -- 都是内建函数  
     -- 通过控制台输入与用户实现交互  
     -- 接收字符串  
     -- raw_input() 返回字符串类型  
     -- input() 返回数值类型

三、数值和字符串  
> * 数据类型  
    -- 数值  
    -- 字符串  
    -- 列表  
    -- 元组  
    -- 字典

* Example:
```
In [3]: a = 123       # 定义变量
In [4]: type(a)       # type()查看变量数据类型
Out[4]: int           # 变量数据类型为整型

In [3]: a = 123

In [5]: 0x34al        # 0x 表示16进制   34a 表示16进制  l 表示长整型
Out[5]: 842L          # 转换后的10进制

In [6]: 3/2           # 整数相除
Out[6]: 1

In [7]: 3.0/2         # 浮点数相除， 只要除数和被除数其中一个为浮点数，值都为浮点数
Out[7]: 1.5
```

> * 字符串类型 -- string

* 三种方法定义字符串类型  
    -- str = 'String'  
    -- str = "String"  
    -- str = '''String'''  

* 三重引号作用  
    -- 定义字符串  
    -- 注释  

> * 格式化操作符
```
%c     字符
%s     通过str()字符串转换来格式化
%i     有符号十进制整数
%d     有符号十进制整数
%u     无符号十进制整数
%o     八进制整数
%x     十六进制整数(小写字母)
%X     十六进制整数(大写字母)
%e     索引符号(小写'e')
%E     索引符号(大写"E")
%f     浮点实数
%g     %f和%e简写
%G     %f和%E简写
```

> * 索引  
  -- 从 0 开始  
  -- 末尾字符为 -1  

> * 切片   
  -- 切片是对操作的对象截取其中一部分操作。字符串、列表、元组都支持切片操作  
  -- 切片语法:[起始:结束:步长]  

PS: 选取区间属于左闭右开型,即从"开始"位置到"结束"位的前一位结束(不包含结束位本身)  

* Example: 切片操作
```
>>> a = [1,2,3,4,5,6,7,8,9]
>>> a[0:4]                   # 取下标0-4的值
[1, 2, 3, 4]
>>> a[0:8:2]                 # 取下标0-4的值，步长为2
[1, 3, 5, 7]
>>> a[:7]                    # # 取下标0-7的值
[1, 2, 3, 4, 5, 6, 7]
>>> a[-1:-5:2]               # 从后往前取时，步长也取负数
[]
>>> a[-1:-5:-2]              # 从后往前取时，步长为-2
[9, 7]
>>> a[2:]                    # 从下标2开始取值，只到值取完
[3, 4, 5, 6, 7, 8, 9]
>>> a[-1:]                   # 取-1到-1的值
[9]
>>> a[-4:]                   # 取-1到-4的值
[6, 7, 8, 9]
```

* Example: 练习题
```
# 将 “123” 转换成整数
In [8]: a = "123"
In [9]: b = int(a)
In [10]: type(b)
Out[10]: int

# 将 “9999999999999999999” 转换成长整数
In [11]: a = 9999999999999999999
In [14]: b = long(a)
In [15]: type(b)
Out[15]: long
In [16]: b
Out[16]: 9999999999999999999L

# 将 “3.1415926” 转换成一个浮点数 (此题存在问题: 浮点型转换为整型)
In [20]: a = 3.1415926
In [21]: a
Out[21]: 3.1415926
In [22]: type(a)
Out[22]: float
In [23]: b = int(a)
In [24]: b
Out[24]: 3
In [25]: type(b)
Out[25]: int

# 将 123 转换成一个字符串
In [26]: a = 123
In [27]: b = str(a)
In [28]: type(b)
Out[28]: str

"""
现有以下字符串
字符串1："   abc  deFGh&*ijkl opq mnrst((uvwxyz   "
字符串2："   ABC#DEF  GH%IJ MNOPQ KLRS&&TUVWX(*&YZ   "
使用字符串的各种方法转换成如下方式
ABCDEFGHIJKLMNOPQRSTUVWXYZzyxwvutsrqponmlkjihgfedcba
"""
In [1]: import re                   # 导入正则模块
In [2]: a = "   abc  deFGh&*ijkl opq mnrst((uvwxyz   "
In [3]: b = "   ABC#DEF  GH%IJ MNOPQ KLRS&&TUVWX(*&YZ   "
In [4]: a1 = re.findall(r'[a-z]', a)     # 通过findall()方法，查找[a-z]的值
In [5]: b1 = re.findall(r'[A-Z]', b)     # 通过findall()方法，查找[a-z]的值
In [6]: a1
Out[6]:
['a',
 'b',
 'c',
 'd',
 'e',
 'h',
 'i',
 'j',
 'k',
 'l',
 'o',
 'p',
 'q',
 'm',
 'n',
 'r',
 's',
 't',
 'u',
 'v',
 'w',
 'x',
 'y',
 'z']
In [7]: b1
Out[7]:
['A',
 'B',
 'C',
 'D',
 'E',
 'F',
 'G',
 'H',
 'I',
 'J',
 'M',
 'N',
 'O',
 'P',
 'Q',
 'K',
 'L',
 'R',
 'S',
 'T',
 'U',
 'V',
 'W',
 'X',
 'Y',
 'Z']
In [8]: a2 = sorted(a1,reverse = True)       # 反转排序
In [9]: a2
Out[9]:
['z',
 'y',
 'x',
 'w',
 'v',
 'u',
 't',
 's',
 'r',
 'q',
 'p',
 'o',
 'n',
 'm',
 'l',
 'k',
 'j',
 'i',
 'h',
 'e',
 'd',
 'c',
 'b',
 'a']
In [10]: a3 = ''.join(a2)                       # 通过join()方法把列表转换成字符串
In [11]: a3
Out[11]: 'zyxwvutsrqponmlkjihedcba'
In [12]: b2 = ''.join(b1)                       # 通过join()方法把列表转换成字符串
In [13]: b2
Out[13]: 'ABCDEFGHIJMNOPQKLRSTUVWXYZ'
In [14]: b2 + a3                                # 字符串连接
Out[14]: 'ABCDEFGHIJMNOPQKLRSTUVWXYZzyxwvutsrqponmlkjihedcba'
```
PS: 参考文档
http://www.jb51.net/article/86187.htm
