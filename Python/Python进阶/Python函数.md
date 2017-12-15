## Python函数

*  Description
>  函数基础
>  函数进阶
>  函数高级
--------------------------------------------------------------------------------

> ## 函数基础
* **@函数定义**
1、函数代码块以`def`关键字开头，后接函数标识符号和`()`,以`:`结尾
2、函数的描述
3、函数体内需要执行的表达式
4、调用函数，执行函数体

* Example:
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-15 15:00
# @Author  : anChow
# @File    : test.py

def fun():                                     # 定义函数
    """ Function Description """               # 函数描述部分
    print("Hello World!")

fun()                                          # 调用函数
```
* **@函数参数**
1、函数括号内定义的参数
2、形式参数：定义函数时，函数括号内定义的变量，简称`形参`  
3、实际参数：调用函数是，函数括号内传递的参数，简称`实参`  

* Example:
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-15 15:11
# @Author  : anChow
# @File    : test.py

def fun(x, y):                                 # x,y为形参
    """ Sum """                                # 函数描述部分
    print('x = %d' %x)                         # %d 整形
    print('y = %d' %y)
    return x+y                                 # 求和并返回

fun(1，2)                                      # 传递实参
```
* **@函数默认参数**
1、必选参数放在最前，默认参数放在其后
2、一般情况下， 参数值变化小的为默认参数
3、若形参在传递新值时，则会替`换掉`默认参数

* Example:
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-15 15:11
# @Author  : anChow
# @File    : test.py

def fun(x, y=5):                              # y=5为默认参数
    """ Sum """
    print('x + y = %d' %(x+y))

fun(1)
```






> ## 函数进阶
* **@函数**
