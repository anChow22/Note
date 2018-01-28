## Python基础(第一天)

*  学习目录  
> * 统计  
> * 乘法口诀  

---
## 0x01 统计  
* Example: 统计  
```
"""
题目： 输入一行字符， 分别统计出其中英文字母、空格、数字和其它字符的个数
"""

#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-26 20:56
# @Author  : anChow
# @File    : countnums.py

status  = 1
while status:
    strings = input("Please input a string('Quit' will exit): ")
    if strings  == "quit":
        exit(1)
    digit = pha = space = other = 0
    for i in strings:
        if i.isdigit():
            digit += 1
        elif i.isalpha():
            pha += 1
        elif i.isspace():
            space += 1
        else:
            other += 1
    print("数字有{0}个， 字母有{1}个， 空格有{2}个， 其它有{3}个".format(digit, pha, space, other))
```

## 0x02 乘法口诀
* Example: 乘法口诀
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-27 10:59
# @Author  : anChow
# @File    : Multipication.py

"""
题目：乘法口诀表
分析思路:
# 1 x 1 = 1
# 1 x 2 = 2 2 x 2 = 4
# 1 x 3 = 3 2 x 3 = 6 3 x 3 =9
"""

# Python2.7版本
for i in range(1, 10):
    for j in range(1, i+1):
        print"{0} x {1} = {2} ".format(j, i, i *j),         # 2.0版本与3.0版本区别
        if i == j:
            print("")

# Python3.0版本
for i in range(1, 10):
    for j in range(1, i+1):
        print("{0} x {1} = {2} ".format(j, i, i *j), end="")  # 2.0版本与3.0版本区别
        if i == j:
            print("")            
```
