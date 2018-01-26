## Python基础(第一天)

*  学习目录  
> * if
> * while

---
## 0x01 if条件判断
* Example: if格式
```
if 判断条件：
    执行语句
elif 判断条件：
    执行语句
else:
    执行语句
```

## 0x02 while判断  
* Example: while格式
```
while 判断条件：
    执行语句

break      # 跳出循环
continue   # 跳到下一循环
```

* Example: 打印小于100的数
```
a = 100
while a>1:
    print(a)
    a -= 1
    if a == 50:
      break
    elif a == 25:
      print("gogogogogogo")
      continue
```

## 0x03 决解数学问题
"""
题目： 输入一行字符， 分别统计出其中英文字母、空格、数字和其它字符的个数  
1、程序分析：利用while语句，条件为输入字符不为'\n'  
2、乘法口诀  
ABCD乘9=DCBA，A=？ B=？ C=？ D=？  
答案： a=1, b=0, c=8， d=9    1089*9=9801  
3、/etc/passwd查找用户， 对用户优先级进行排序  
1! + 2! + 3! + 4! + 5! + 6! + n!  
"""

* Example: Python示例  
```
"""
题目： 输入一行字符， 分别统计出其中英文字母、空格、数字和其它字符的个数
1、程序分析：利用while语句，条件为输入字符不为'\n'
2、乘法口诀
ABCD乘9=DCBA，A=？ B=？ C=？ D=？
答案： a=1, b=0, c=8， d=9    1089*9=9801
3、/etc/passwd查找用户， 对用户优先级进行排序
1! + 2! + 3! + 4! + 5! + 6! + n!
"""

#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-26 13:17
# @Author  : anChow
# @File    : operation.py

"""
Python解决数学难题
ABCD乘9=DCBA，A=？ B=？ C=？ D=？ 答案： a=1, b=0, c=8， d=9    1089*9=9801
"""
for A in range(1, 10):
    for B in range(0, 10):
        for C in range(0, 10):
            for D in range(0, 10):
                start = 1000*A + 100*B + 10*C + D
                end = 1000*D + 100*C + 10*B + A
                if start * 9 == end:
                    print("A = {0}".format(A))
                    print("B = {0}".format(B))
                    print("C = {0}".format(C))
                    print("D = {0}".format(D))
                    print("{0} * 9 == {0}".format(start，end))
```

* Example: 阶乘
```
"""
题目： 阶乘
1! + 2! + 3! + 4! + 5! + 6! + n!
1! = 1
2! = 2*1 = 2
3! = 3*2*1 = 6
"""

#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-26 20:36
# @Author  : anChow
# @File    : Factorial.py

def one(n):
    total = 1
    if n == 1:
        total = 1
    else:
        for i in range(1, n+1):
            total *= i
    return total

status = 1
while status:
    result = 0
    n = input("Please input a number(n>1): ")
    for i in n:
        if not i.isdigit():
            print("The number of you input is error.")
            exit(1)
    if int(n) < 0:
        print("The number of you input is not int num.")
        break
    for i in range(0, int(n)+1):
        result += one(i)
    print("0! + 1! + 2! + ... + n! = {0}".format(result))
```
