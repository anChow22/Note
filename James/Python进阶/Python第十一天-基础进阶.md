## Python基础(第七天)

*  学习目录    
> * 多类型传值和冗余参数  
> * 函数递归调用  

---
## 0x01 多类型传值和冗余参数  
>  多类型传值  
   -- 可以通过 int、元组、字典value进行传参  
>  冗余参数  
   -- 多余实参处理def fun(x, y, *args, **kwargs):  

* Example: 普通传值
```
In [46]: def fun(x, y):               # 定义函数(形参)
    ...:     return x + y             # 返回 x 与 y 的和
In [47]: print fun(3, 6)              # 调用函数传参(实参)

In [48]: t = (1, 4)                   # 定义元组
In [49]: print fun(t)                 # 报错, 只传了1个参数
In [50]: print fun(t, 12)             # 报错，类型错误， 元组不是整型
```
* Example: 多类型传值
```
In [46]: def fun(x, y):               # 定义函数(形参)
    ...:     return x + y             # 返回 x 与 y 的和

In [48]: t = (1, 4)                   # 定义元组
In [51]: fun(*t)                      # 按元组形式进行传值
Out[51]: 5    
```
* Example: 另函数传参
```
In [60]: def fun(x, y, z):
    ...:     return x + y + z
In [61]: fun(x=1, y=3, z=5)           # 传参方式一
Out[61]: 9

In [62]: dic = {'x':1, 'y':3, 'z':5}  # 定义字典
In [63]: fun(**dic)                   # ** 表示传递字典
Out[63]: 9
```
* Example: 整数、列表、 字典传值
```
In [64]: def fun(x, *args, **kwargs):
    ...:     print(x)
    ...:     print(args)
    ...:     print(kwargs)
    ...:     

In [65]: fun(1, 2, 'a', [1, 2,])      # 1 传给x 2，'a', [1,2,] 传给args作为列表
1                                     # 整数传值
(2, 'a', [1, 2])                      # 列表传值
{}                                    # 字典传值，由于该实例未传入 字典 ，因此，输入空字典
```
* Example: 字典传值
```
In [64]: def fun(x, *args, **kwargs):
    ...:     print(x)
    ...:     print(args)
    ...:     print(kwargs)

In [73]: fun(1, 2, 'a', [1, 2,], name='chow', age=20)   # name 及 age 为字典传值
1
(2, 'a', [1, 2])
{'age': 20, 'name': 'chow'}                             # 字典传值

In [74]: fun(1, 2, 'a', [1, 2,], *t, a=3, **{'c': 11} )   # 注意 * 传列表  ** 传字典
1
(2, 'a', [1, 2], 1, 4)                # 1，4 为 *t 传值  
{'a': 3, 'c': 11}                     # 为 ** 字典传值  
```

## 0x02 函数递归调用
>  计算阶乘
   -- 循环
>  递归调用
   -- 必须有最后的默认结果
   -- 递归参数必须向默认结果收敛

* Example: 计算阶乘
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-26 14:16
# @Author  : anChow
# @File    : test.py

def factorial(n):
    sum = 1
    for i in range(1, n+1):
        sum *= i
    return sum

print(factorial(5))
```
* Example: 求和
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-26 14:16
# @Author  : anChow
# @File    : test.py

def factorial(n):
    sum = 0
    for i in range(1, n+1):
        sum += i
    return sum
print(factorial(100))
```
* Example: 递归乘法
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-26 14:16
# @Author  : anChow
# @File    : test.py

def factorial(n):
    if n == 0:                          # 递归默认参数为 0
        return 1                        # 返回值为 1
    else:
        return n * factorial(n-1)       # 递归参数，逐渐收敛

print(factorial(5))
```
* Example: 递归求和
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-26 14:16
# @Author  : anChow
# @File    : test.py

def factorial(n):
    if n == 0:                          # 递归默认参数为 0
        return 0                        # 返回值为 0
    else:
        return n + factorial(n-1)       # 递归参数，逐渐收敛

print(factorial(100))
```
