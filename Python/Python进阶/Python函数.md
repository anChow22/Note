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
* **@函数返回值**  
> * 无参数，无返回值  
> * 无参数，有返回值  
> * 有参数, 无返回值  
> * 有参数，有返回值

1、无参数，无返回值  --->  `主要用于显示提示信息`  
* Example:
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-15 15:11
# @Author  : anChow
# @File    : test.py

def fun():
    """ 无参数， 无返回值 """
    print('#############################')
    print('     人生苦短  我用Python    ')
    print('')
    print('     1、启动     ')
    print('     2、停止     ')
    print('#############################')

fun()    
```
2、无参数，有返回值  --->  `可以返回数据，主要用于采集数据`  
* Example:
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-15 15:20
# @Author  : anChow
# @File    : test.py

def fun():
    """ 无参数， 有返回值 """
    return 20

result = fun()                             # 把函数的返回值，复制给result
print('返回值为:%d' %result)
```
3、有参数，无返回值  --->  `能接收参数， 不返回数据。用于某些变量设置数据而不需要结果`  
* Example:
```
使用不多
```
4、有参数，无返回值  --->  `能接受参数，返回某个数据。用于数据处理并需要结果的应用`  
* Example:
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-15 15:20
# @Author  : anChow
# @File    : test.py

def fun(num):
    """ 计算累加和 """

    # 初始化变量值
    result = 0
    i = 1
    # 循环判断i与形参值之间大小
    while i < num:
        result = result + i
        i += 1
    return result

result = fun(100)
print('1~100累加和为:%d' %result)
```
5、函数return返回值  
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-15 15:20
# @Author  : anChow
# @File    : test.py

def fun(a, b):
    test =  a // b                 # 余
    text = a % b                   # 商
    return test, text              # 返回多个值

x, y = fun(6, 3)                   # 分别把函数值赋给变量
print(x)
print(y)
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

* Example:
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-15 15:11
# @Author  : anChow
# @File    : test.py

def fun(x, y=5):
    """ 带有return返回值的函数 """
    return x+y

result = fun(4)                              # 调用函数，把return返回值赋值给result
print(result)
```
* **@函数默认参数**  
1、默认参数同时也称为`缺省参数`  
2、必选参数放在最前，默认参数放在其后   
3、一般情况下， 参数值变化小的为默认参数   
4、若形参在传递新值时，则会替`换掉`默认参数

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
* **@函数不定长参数**  
* Example:
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-15 15:20
# @Author  : anChow
# @File    : test.py

def fun(a, b, *args, **kwargs):
    """ 可变参数 """
    print("a = ", a)
    print("b = ", b)
    print("args  = ", args)
    print("kwargs: ")
    for key, value in kwargs.items():
        print(key, "=", value)

res = fun(1, 2, 3, 4, 5, m=6, n=7, p=8)
print(res)
```
* **@函数引用传参**
> * 函数参数是引用传递(注意，不是值传递)
> * 对于可变类型，变量不能修改，所以不会影响到变量自身
> * 对于可变类型，函数体中的运算有可能会更改传入参数变量

* Example:
```

```
* **@函数嵌套调用**  
1、函数内调用另外一个函数  
* Example:
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-15 15:20
# @Author  : anChow
# @File    : test.py

def testB():
    """ 函数嵌套调用 """
    print('---- 调用testA函数后，调用到testB函数执行时 ---- ')
    print('执行testB函数时输出 ... ...')
    print('---- 函数testB执行完成后----')

def testA():
    print('---- 调用testA函数开始 ----')
    testB()                                # 调用函数testB()
    print('---- 执行完testB后，返回执行testA函数，结束 ----')

testA()
```
* Example:
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-15 15:20
# @Author  : anChow
# @File    : test.py

# 打印横线
def printOneLine():
    """ 打印一条横线 """
    print('#'*30)

# 循环打印多条横线
def printNumLine(num):
    """ 通过循环，调用printOneLine()函数打印多条横线 """
    i = 0
    while i < num:
        printOneLine()
        i += 1

printNumLine(3)                            # 调用函数，传递实参
```
* Example:
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-15 15:20
# @Author  : anChow
# @File    : test.py

# 打印横线
def sum(x, y, z):
    """  求三个数之和 """
    sum = x + y + z                        # 求和
    print('三个数之和为:%d' % sum)
    return sum

def avg(x, y, z):
    """ 求三个数的平均值 """
    sumRes = sum(x, y, z)                  # 调用sum()函数，传参
    avgRes = sumRes / 3                    # 求平均值
    return avgRes

res = avg(10, 20, 30)                      # 实参传值
print('三个数平均值为:%d' % res)
```
* **@函数变量**    
1、局部变量  
> * 函数内部定义，只对当前函数起用
> * 不同函数，可以定义相同名字局部变量，互不影响  
> * 作用: 临时保存数据

* Example:
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-15 15:20
# @Author  : anChow
# @File    : test.py

# 打印横线
def sum():
    """ sum()函数的局部变量 """
    i = 20
    print('sum()函数局部变量的值为:%d' % i)
    i = 30
    print('sum()函数局部变量变更值后为:%d' % i)

def avg():
    """ avg()函数的局部变量 """
    i = 20
    print('avg()函数局部变量的值为:%d' % i)

# 调用函数执行
sum()
avg()
```
2、全局变量
> * 函数体外定义的变量  
> * 在所有函数中可以访问  
> * 在函数内修改全局变量，需要使用`global`声明  
> * 全局变量和局部变量`名字相同`使用局部变量名字

* Example: 全局变量及global全局变量
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-15 15:20
# @Author  : anChow
# @File    : test.py

x = 10                          # 全局变量
def fun(a):
    global x                    # 局部定义的全局变量
    x += 1
    print x

fun(20)
```

* Example: global全局变量
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-15 15:20
# @Author  : anChow
# @File    : test.py

a = 1010

def test1():
    global a
    print('---- test1 -- 修改前 --- a = %d' % a)
    a = 200
    print('---- test1 -- 修改后 --- a = %d' % a)

def test2():
    print('---- test1 --- a = %d' % a)

test1()
test2()
```
> * 注意:  
> * 函数只对全局变量做print操作  
> * 若做其他操作，需要用global声明全局变量  
> * 在函数外部使用函数内部的全局变量，x需要使用global声明  
> * 对于不可变类型的全局变量，指向的数据不能修改，所以不使用global时无法修改全局变量  
> * 对于可变类型的全局变量，指向的数据可以修改，所以不使用global时无法修改全局变量

3、扩展: locals()函数
> * 以字典的方式打印所有变量
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-15 15:20
# @Author  : anChow
# @File    : test.py

a = 1                         # 全局变量
b = 2
def fun():
    x = 1
    y = 2
    print locals()           # locals()定义在函数内，会打印出函数内部的变量（局部变量）

fun()
print locals()               # locals()定义在函数外，会打印出整个程序所有的变量
```

> ## 函数进阶
* **@递归函数**




* **@匿名函数**
