## Python基础(第六天)

*  学习目录  
> * 流程控制-for序列  
> * 流程控制-for字典  

---
## 0x01 for
> * 循环  
> * for 循环  
> * range() 方法
> * xrange() 方法
> * for 循环字典
> * for ... else
> * 其它

* 循环
  -- 一个结构，导致程序要重复一定次数  
  -- 条件循环也如此， 条件为假，循环结束

* for 循环
  -- 序列里，for循环遍历

* range() 方法  
   -- 快速生成系列  
   -- range(起始位置， 结束为止， 步长)  
      --- 创建对象为`整数`    
      --- 起始位置，不选默认为`0`  
      --- 结束位置，不包括在范围内  
      --- 步长默认为`1`  

* xrange() 方法  
  -- 生成迭代对象  
  -- 不占用内存资源  
  -- 不会直接返回值  
  -- 通过for循环遍历输出值  

* 迭代遍历  
   -- 遍历序列： 将序列中各个元素取出  
       --- 直接从序列取值  
       --- 通过索引取值  
PS:
   `迭代` 指重复执行一个指令  

* for ... else  
  -- for循环如果正常结束， 才会执行else语句  

* 其它  
  -- break  退出所有循环体  
  -- continue  退出本层循环  
  -- pass      占位符  
  -- exit()    sys模块下退出方法    

> * 语法格式
```
for iterationg_var in sequence:
    statement(s)
```

* Example: for循环打印字符串
```
In [281]: a = 'abc'

In [282]: for i in a:
     ...:     print(i)  
a
b
c
```
* Example: range()生成一组序列
```
In [283]: range(10)               # 生成0 - 9序列
Out[283]: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
In [284]: help(range)             # 获取帮助
range(start, stop[, step]) -> list of integers  # range(起始位置, 结束位置, 步长)

In [285]: for i in range(10):     # 生成0 - 9序列, 并输出
     ...:     print(i)

In [286]: for i in range(10, 100, 5):   # 打印10 - 99步长为5的数
    ...:     print(i)
```
* Example: 打印偶数
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-20 22:37
# @Author  : anChow
# @File    : test.py

for i in range(1, 11):
    if i % 2 == 0:                # 取余数    
        print(i)
```
* Example: 列表推导
```
In [288]: print([ i for i in range(1, 11)])    # 把循环出的书放入列表
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

In [289]: print([ i for i in range(1, 11) if i % 2 == 0])  # 取余
[2, 4, 6, 8, 10]

In [290]: print([ i**2 for i in range(1, 11)])  # i的乘方
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```
* Example: 求和
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-20 22:37
# @Author  : anChow
# @File    : test.py

sum = 0
for i in range(1, 101):
    sum += i
print(sum)
```
* Example: xrange() 方法
```
Out[291]: xrange(10)
In [292]: a = xrange(10)
In [295]: for i in a:
     ...:     print(i)
In [296]: help(xrange)     
```
* Example: for循环遍历字典
```
In [297]: dic = {'name': 'Chow', 'age': 26}    # 定义字典
In [298]: dic.fromkeys('abcde', 100)           # 定义字典
Out[298]: {'a': 100, 'b': 100, 'c': 100, 'd': 100, 'e': 100}
In [299]: for k in dic:                        # 遍历字典keys
     ...:     print(k)
In [300]: for k in dic:                        
    ...:     print(k, dic[k])                  # 输出keys value

In [303]: for k in dic:
    ...:     print('%s ---> %s' % (k, dic[k])) # 格式化输出keys及value
In [304]: dic.items()                          # 调用字典items() 方法输出
Out[304]: [('age', 26), ('name', 'Chow')]   

In [307]: for i in dic.items():print(i)        # 通过items() 方法获取元组
('age', 26)
('name', 'Chow')

In [308]: for k, v in dic.items():print(k, v)  # 通过k v接收值
('age', 26)
('name', 'Chow')

In [309]: for k, v in dic.iteritems():print(k, v)  # 通过k v接收值
('age', 26)
('name', 'Chow')
```
* Example: 循环打印乘法口诀
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-20 22:37
# @Author  : anChow
# @File    : test.py

for i in xrange(1, 10):
    for j in xrange(1, i+1):
        print('%s x %s = %s' % (j, i, j*i)),
    print
```
* Example: 循环打印序列
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-20 22:37
# @Author  : anChow
# @File    : test.py

import time

for i in xrange(10):
    print(i)
    time.sleep(1)                    # 休眠1秒
else:                                # 当序列被遍历完, 才执行
    print('main end')
```
* Example: 循环打印序列，break跳出所有循环
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-20 22:37
# @Author  : anChow
# @File    : test.py

import time

for i in xrange(10):
    print(i)
    if i == 5:                       # 当 i 等于 5 时
        break                        # 跳出所有循环
else:
    print('main end')
```
* Example: 循环打印序列，continue跳出本层循环
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-20 22:37
# @Author  : anChow
# @File    : test.py

import sys
import time

for i in xrange(10):
    print(i)
    if i == 3:
        continue                     # 跳出本层循环
    elif i == 5:                     # 当 i 等于 5 时
        break                        # 跳出所有循环
    elif i == 6:                     # 当 i 等于 6 时
        pass                         # 占位， 什么都不做
    elif i == 7:                     # 当 i 等于 7 时
        sys.exit()                    # 调用sys模块的exit() 方法退出
    print(i)
else:
    print('main end')
print('Hello Python')    
```
* Example: 猜数字游戏(存在问题)
```
"""
1、系统生成一个20以内的随机整数
2、玩家有6次机会进行猜猜看， 每次猜测都有反馈(猜大了， 猜小了， 猜对了， 结束)
3、6次中， 猜对了， 玩家赢了
4、否则系统赢了
"""
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-26 10:37
# @Author  : anChow
# @File    : test.py

import random

num = random.randint(0,20)
prt = int(raw_input("输入你猜的数值为："))

i = 0
while i < 6:
    if prt > num:
        print("猜大了")
        i += 1
    elif prt < num:
        print("猜小了")
        continue
    elif prt == num:
        print("猜对了")
        continue
    else:
        print("结束")
        break
```
## 0x01  扩展习题
> 有1、2、3、4个数字，能组成多少个互不相同且无重复数字的三位数？都是多少？  
 1、程序分析：可填在百位、十位、个位的数字都是1、2、3、4。组成所有的排列后再去  掉不满足条件的排列。  

> 打印出所有的“水仙花数”,所谓“水仙花数”是指一个三位数,其各位数字立方和等于该数本身。例如：153是一个“水仙花数”,因为153=1的三次方＋5的三次方＋3的三次方。  
程序分析：利用for循环控制100-999个数,每个数分解出个位,十位,百位。  

> 两个乒乓球队进行比赛,各出三人。甲队为a,b,c三人,乙队为x,y,z三人。已抽签决定比赛名单。有人向队员打听比赛的名单。a说他不和x比,c说他不和x,z比,请编程序找出三队赛手的名单。  

* Example: 第1题
```
"""
有1、2、3、4个数字，能组成多少个互不相同且无重复数字的三位数？都是多少？
1、程序分析：可填在百位、十位、个位的数字都是1、2、3、4。组成所有的排列后再去  掉不满足条件的排列。
"""
#### 第一种方法
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-26 10:37
# @Author  : anChow
# @File    : test.py

i = 0
for x in range(1, 5):
    for y in range(1, 5):
        for z in range(1, 5):
            if (x != y) and (y != z) and (x != z):
                print("%d%d%d" %(x,y,z))
            i += 1
print("排列组合后不重复三位数为: %d 个 " %i)
print('组合完成')

#### 第二种方法
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-26 15:36
# @Author  : anChow
# @File    : test.py

res = []
for i in range(1,5):
    for j in range(1,5):
        for k in range(1,5):
            res.append(i*100+j*10+k)
print(res)

#### 第三种方法(此种方法感觉更贴近题目)
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-26 10:37
# @Author  : anChow
# @File    : test.py

d = [1, 2, 3, 4]

def getnum(num, digit, length):
    num1 = num

    for i in range(len(digit)):
        num = num1 * 10 + digit[i]
        if length == 3:
            yield num
        elif length < 3:
            for j in getnum(num, digit[:i] + digit[i + 1:], length + 1):
                yield j

digit = list(getnum(0, d, 1))
print "%r 共可以组成%d个三位数字 " % (d, len(digit))
print "它们是:%r" % digit
```
PS: 参考文档
    http://blog.csdn.net/u013901768/article/details/75448177  
    https://zhidao.baidu.com/question/329856308887127725.html  
* Example: 第2题
```
"""
打印出所有的“水仙花数”,所谓“水仙花数”是指一个三位数,其各位数字立方和等于该数本身。例如：153是一个“水仙花数”,因为153=1的三次方＋5的三次方＋3的三次方。
程序分析：利用for循环控制100-999个数,每个数分解出个位,十位,百位。
"""
### 方法一
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-26 15:36
# @Author  : anChow
# @File    : test.py

for i in range(100,1000):
    j = i / 100
    k = i / 10 % 10
    l = i % 10
    if i == j ** 3 + k ** 3 + l ** 3:
        print(i)

### 方法二
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-26 15:14
# @Author  : anChow
# @File    : test.py

import math

for i in range(100, 1000):
    x = math.floor(i / 100)  # 获得百位数
    y = math.floor((i - x * 100) / 10)  # 获得十位数
    z = i - math.floor(i / 10) * 10  # 获得个位数
    if i == x ** 3 + y ** 3 + z ** 3:
        print(i)
```
PS: 参考文档  
    https://www.cnblogs.com/iderek/p/5958568.html
* Example: 第3题
```
"""
两个乒乓球队进行比赛,各出三人。甲队为a,b,c三人,乙队为x,y,z三人。已抽签决定比赛名单。有人向队员打听比赛的名单。a说他不和x比,c说他不和x,z比,请编程序找出三队赛手的名单。
"""
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-26 14:16
# @Author  : anChow
# @File    : test.py

first_list=['x','y','z']
for i in first_list:
    for j in first_list:
        if(j!=i):
            for k in first_list:
                if(k!=i)and(k!=j):
                    if(i!='x')and(k!='x')and(k!='z'):
                        print('a pk %s,b pk %s,c pk %s' %(i,j,k))
```
PS： 参考文档  
     http://blog.51cto.com/yinsuifeng/1906088
