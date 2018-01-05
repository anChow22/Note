## Python基础(第十二天)

*  学习目录  
> * 递归列出目录里的文件
> * 匿名函数

---
## 0x01 递归列出目录里的文件
>  打印目录下所有文件

* Example: 模块及方法学习
```
In [75]: import os                      # 导入模块
In [78]: os.listdir('/etc')             # 列出目录下所有文件(包括目录)，以列表形式展示

In [80]: os.path.isdir('/etc/')         # 判断文件是否为目录
Out[80]: True                           # 目录， 返回True
In [82]: os.path.isfile('/etc/passwd')  # 判断是否为文件
Out[82]: True
In [81]: os.path.isdir('/etc/passwd')
Out[81]: False                          # 文件(即使文件不存在)， 返回False

In [84]: os.path.join('/etc/passwd','aliases')   # 连接文件，不判断文件是否存在
Out[84]: '/etc/passwd/aliases'
```

* Example: 递归打印目录下所有文件
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-26 14:16
# @Author  : anChow
# @File    : test.py

import os
import sys

def printFiles(path):
    lsdir = os.listdir(path)
    dirs = [ i for i in lsdir if os.path.isdir(os.path.join(path, i)) ]
    files = [ i for i in lsdir if os.path.isfile(os.path.join(path, i)) ]
    if dirs:
        for d in dirs:
            printFiles(os.path.join(path, d))
    if files:
        for f in files:
            print(os.path.join(path, f))            
printFiles(sys.argv[1])
```
## 0x02 匿名函数  
>  lambda函数是一种快速定义单行的最小函数，可以用在任何需要函数的地方  
>  优点：  
   -- 写脚本时，lambda可以省区定义函数的过程，代码更加精简  
   -- 对于抽象函数，不会被别的地方在重复使用函数，使用lambda不需要考虑命名问题  
   -- 使用lambda 在某些时候让代码更容易理解    
>  lambda 基础   
   -- lambda语句中，冒号前是参数，可以有多个逗号隔开，冒号右边是返回值  
   -- lambda语句构建的是`函数对象`     

* Example: 常用函数 与 lambda函数 切换  
```
### 普通函数
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-26 14:16
# @Author  : anChow
# @File    : test.py

def fun(x, y):
    return x * y
print(fun(2, 3))

### lambda函数
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-26 14:16
# @Author  : anChow
# @File    : test.py

r = lambda x, y: x * y
print(r(2, 3))
```
* Example: reduce()内置函数   
```
In [85]: help(reduce)                            # 获取帮助
reduce(function, sequence[, initial]) -> value   # reduce(函数名， 序列[迭代])
For example, reduce(lambda x, y: x+y, [1, 2, 3, 4, 5])    # 例子

### 默认函数实例
In [87]: def add(x, y):
    ...:     return x + y
In [88]: reduce(add, range(1, 101))
Out[88]: 5050

### lambda函数 求和 实例
In [90]: reduce(lambda x, y: x + y, range(1, 101))
Out[90]: 5050

### lambda函数 计算阶乘 实例
In [91]: reduce(lambda x, y: x * y, range(1, 5))
Out[91]: 24
```
