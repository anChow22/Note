## Python基础(第十天)

*  学习目录    
> * 函数的变量  
> * 函数的返回值  

---
## 0x01 函数定义  
> 就是完成特定功能的语句组， 作为一个单位使用  
> 可以通过函数名在程序的不同地方多次执行(称为函数调用)  
> 预定义函数 --- 可直接使用  
> 自定义函数 --- 用户自己编写  
> 函数定义  
  -- def 函数名([参数列表])  
> 函数调用  
  -- 函数名([参数列表])      

* Example: 定义函数
```
In [23]: def fun():                   # 定义函数
    ...:     print('Hello Python')

In [24]: fun()                        # 调用函数
Hello Python
```
* Example: 判断从键盘输入的字符是否为数字
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-22 10:37
# @Author  : anChow
# @File    : test.py

def fun():
    sth = raw_input("Please input something: ")  # 从键盘获取
    try:                                         # 捕获异常
        if type(int(sth)) == type(1):            # 判断类型是否相等
            print("%s is a number" %sth)
    except ValueError:
        print("%s is not number" %str)

fun()                                            # 调用函数
```

## 0x02 函数参数
> * 形式参数和实际参数  
    -- 定义函数时， 函数名后面括号中的变量名称为 “形式参数” 或 “形参”  
    -- 调用函数时， 函数名后面括号中的变量名称为 "实际参数" 或 “实参”   

* Example: 形参 与 实参 区别
```
In [23]: def fun(x, y):                     # 形参
    ...:     print('%d + %d = %d' %(x + y))

In [24]: fun(10, 20)                        # 实参
```
* Example: 带参数执行脚本
```
[root@p6 python]# vi number.py
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-24 10:37
# @Author  : anChow
# @File    : test.py

import sys                                 # 导入模块

def isNum(s):
    for i in s:                            # for ... else格式
        if i in '0123456789':              # 判断 i 值是否为数值且在0 - 9 内
            pass
        else:
            print('%s is not a number' % s)
            sys.exit()                     # 退出
    else:
        print("%s is a number" % s)

isNum(sys.argv[1])                          # sys.argv获取文件路径 [1] 参数

[root@p6 python]# python number.py aaaa     # 注意 参数 aaaa
aaaa is not a number
```
## 0x03 默认参数  
> * 缺省参数(默认参数)  

* Example: 默认参数用法  
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-22 10:37
# @Author  : anChow
# @File    : test.py

def fun(x, y = 100):                # y 为默认参数
    print(x, y)

fun(1, 2)                           # 分别为x y赋值
fun(1)    
```
* Example: 练习(打印系统所有PID)
```
"""
1、打印系统所有PID
2、要求从/proc读取
3、os.listdir()
"""

#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-22 10:37
# @Author  : anChow
# @File    : test.py

import sys                             # 导入sys os 模块
import os

def isNum(s):                          # 定义函数
    for i in s:                        # 遍历形参 s
        if i in '0123456789':          # 判断 i 是否为 0 - 9
            pass
        else:
           break                       # 不在 0 - 9 跳出 if 循环
    else:
        print(s)


for i in os.listdir('/proc'):         # 调用os.listdir从'/proc'文件获取PID
    isNum(i)                          # 调用函数传值 判断
```
## 0x04 函数变量  
> 局部变量  
  -- 函数中定义的变量为 局部变量,只能在该函数内部使用  
> 全局变量  
  -- 在文件顶部定义的变量可以供文件中任何函数调用， 称为 全局变量  

* Example: 局部变量
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-22 10:37
# @Author  : anChow
# @File    : test.py

def fun():
    x = 100                          # 函数内部定义，
    print(x)

fun()                                # 调用函数执行，会调用内部变量
print(x)                             # 因全局变量为定义 x ,则会报错
```
* Example: 全局变量
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-22 10:37
# @Author  : anChow
# @File    : test.py

y = 200                              # 全局变量
def fun():
    x = 100                          # 局部变量
    print(x)

fun()                                # 调用函数执行，会调用内部变量
print(y)                             # y 已被定义为全局变量
```
* Example: global申明局部变量为全局变量
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-22 10:37
# @Author  : anChow
# @File    : test.py

x = 10                               # 全局变量
def fun():
    global x                         # 申明 局部变量为全局变量
    x += 1                           # 变量累加， 计数器
    print(x)

fun()
print(x)                             # 只有调用函数后，x 才会改变， 不然不改变
```
* Example: locals在函数内的用法
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-22 10:37
# @Author  : anChow
# @File    : test.py

x = 10                               # 全局变量
def fun():
    y = 1
    x = 1
    print(locals())                  # 返回字典

fun()
print(locals())                      # 返回函数的内置变量信息
```
## 0x05 函数返回值  
> 返回值  
  -- 函数被调用后，返回一个指定值   
  -- 函数调用后默认返回None  
  -- return 返回值  
  -- 返回值可以是任意类型  
  -- return 执行后，函数终止  
  -- return 与 print区别  

* Example: 函数返回值及return  
```
# -*- coding: utf-8 -*-
# @Time    : 2017-12-22 10:37
# @Author  : anChow
# @File    : test.py

def fun():
    print('Hello World')
    return True                     # 函数遇到return,则函数结束

print(fun())                        # 若没有return ，则函数返回None
```
* Example: 打印Linux系统PID
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-22 10:37
# @Author  : anChow
# @File    : test.py

import sys
import os

def isNum(s):
    for i in s:
        if i not in '0123456789':
            return False
        return True

for i in os.listdir('/proc'):
    if isNum(i):
        print(i)
```
* Example: isdigit()函数用法
```
In [44]: a = 'abc'
In [45]: help(a.isdigit)          # isdigit返回bool值，判断是否为字符串
```
* Example: isdigit()判断是否为数值，打印Linux系统PID
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-22 10:37
# @Author  : anChow
# @File    : test.py

import sys
import os

def isNum(s):
    if s.isdigit():
        return True
    return False

for i in os.listdir('/proc'):
    if isNum(i):
        print(i)
```
