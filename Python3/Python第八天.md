## Python基础(第八天)

*  学习目录  
> * 参数匿名函数字典排序  
> * 生成式和生成器  
> * 装饰器的作用  

---
## 0x01 参数匿名函数字典排序  
> 匿名函数  
  --- 没有名字的函数  
> lambda  
  --- 一种快速定义单行的最小函数，可以用在任何需要函数的地方  
> 函数参数   
  --- def(*arg, **kwargs)  
> 高阶函数    
  --- map(f,[1, 2, 3, 4])      # 返回每个元素通过f计算玩的value的list
  --- reduce(f,[1, 2, 3, 4, 5])                #
  --- filter(lamdba x:x%2 == 1, [1,2,3,4,5])   # 过滤
> sorted函数  
  sorted(iterable, cmp=None,key=None, reverse=False)

* Example: 函数定义
```
def fun(x, y):
    return x * y
```

* Example: lambda函数
```
r = lambda x, y:x*y
```

* Example: *args 及 **keargs  
```
*args               # tuple(1,)
**keargs            # dict{"k": "v"}
```

* Example: *args 及 **keargs 用法   
```
fun(*args, **keargs)
fun(1, 2, 3, 4, 5, a=10, b=40)
```

* Example: *args用法   
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-29 20:30
# @Author  : anChow
# @File    : paramArgs.py

def add(*args):
    total = 0
    for i in args:
        total += i
    print("total = {0}".format(total))

if __name__ == '__main__':
    add(1, 2, 3, 4, 5)
```

* Example: lambda用法   
```
def add(*args):
    total = 0
    for i in args:
        total += i
    print("total = {0}".format(total))

if __name__ == '__main__':
    add(1, 2, 3, 4, 5)
    s1 = lambda x, y: x + y
    print(s1(10, 20))
```

* Example: 示例(未调试成功)
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-29 20:30
# @Author  : anChow
# @File    : paramArgs.py

def add(*args):
    total = 0
    for i in args:
        total += i
    print("total = {0}".format(total))

def sortDictValue(dict1):
  printsorted(dict1.items(), key=lambda d:d[0], reverse=False)


if __name__ == '__main__':
    add(1, 2, 3, 4, 5)
    s1 = lambda x, y: x + y
    print(s1(10, 20))
    aaa = dict(a=100, b=10, c=50, d=321)
    for i in aaa.items():
        print(i)
    l =list()
    l = sortDictValue(aaa)
    print(l)
```

## 0x02 生成式和生成器  
> 生成式和生成器  
  --- [exp for valin collection if condition]  
  --- [x*x for x in xrange(10) if x*x%2 == 0]  
> 生成器  
  --- 方法一: (exp for val in collection if condition)  
  --- 方法二: 使用yield关键字，包含yield语句的函数会被特地编译成生成器  
  --- yield可以理解为return,但并不退出，只是挂起，恢复的时候从yield下面开始  
> 生成式和生成器区别  
  --- 列表生成式直接返回表达式结果列表
  --- 生成器返回一个对象，该对象包含对表达式结果的计算引用，通过循环直接输出
  --- 生成器不会一次性列出所有数据， 当用到时，在列出。节省内存使用
  --- 类似range(1,0)   xrange(1,10)的区别， 但类型不同

* Example: 生成式
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-29 23:14
# @Author  : anChow
# @File    : production.py

a = [x*x for x in range(1, 30) if  x%2 == 0]
print(a)
print(type(a))

y = list()
x = [1, 2, 3, 4, 5]
y += x
y.append(100)
print(x)
print(y)
```
* Example: 生成器
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-29 23:14
# @Author  : anChow
# @File    : production.py

b = (x*x for x in range(1, 30) if  x%2 == 0)
print(b)
print(type(b))
for i in b:
    print(i)
```

* Example: 列表生成式
```
def test(l):
    for i in l:
        yield i
        print("i = {0}".format(i))

test([1, 2, 3, 4,5,6,7,8,9])
print(type(m))
print(m.__next__)
for i in m:
    print(i)
```

## 0x03 装饰器的作用   
> 装饰器本质是一个python函数，可以让其他函数在不需要做任何代码变动的前提下增加额外功能  
> 装饰器的返回值也是一个函数对象。经常用于有切面需求的场景    
> 不改变原来函数本身，在函数的前面或者后面增加额外功能  

* Example: 常规函数调用  
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-29 23:37
# @Author  : anChow
# @File    : demonDecorator.py

def hello():
    print("Hello world")


def test():
    print("####### start ########")
    hello()
    print("####### end ########")

test()
```
