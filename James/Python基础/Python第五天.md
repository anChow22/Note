## Python基础(第五天)

*  学习目录  
> * 流程控制-if条件(一)  
> * 流程控制-if条件(二)  

---
## 0x01 if
> * if语法格式
> * if ... elif
> * if ... elif ... else

* if语法格式
```
if expression:
    statement(s)
```
PS:
   缩进采用4个空格  
   1   表示 True
   0   表示 False

* 逻辑值(bool)  
   --- True： 表示非空的值,所有非零数  
   --- False: 表示0, None, 空值   

* if ... else语法格式
```
if expression:
    statement(s)
else:
    statement(s)
```
* if ... elif ... else语法格式
```
if expression:
    statement(s)
elif:
    statement(s)
else:
    statement(s)
```
* Example: if 判断条件是否成立
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-20 22:37
# @Author  : anChow
# @File    : test.py

if not 1 < 2 and 1 == 1:              # 1>2 并且 1 == 1 , 才进行输出
    print('Hello Python')
    print('True')
```
* Example: if ... else
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-20 22:37
# @Author  : anChow
# @File    : test.py

if not 1 < 2 and 1 == 1:
    print('Hello Python')
    print('条件成立时 ......')
else:
    print('条件不成立时 ......')
print('不在条件判断内,不管是否成立都会输出 .....')    
```    
* Example: 判断成绩
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-20 22:37
# @Author  : anChow
# @File    : test.py

Score = int(input('请输入分数: '))
if Score >= 90 and Score <= 100:
    print('A')
    print('优秀')
elif Score >= 89 and Score <= 80:
    print('B')
    print('良好')
elif Score >= 79 and Score <= 70:
    print('C')
    print('一般')
elif Score >= 69 and Score <= 60:
    print('D')
    print('合格')
else:
    print('E')
    print('不合格')
print('不在条件判断内,不管是否成立都会输出 .....')
```
* Example: 字符串转换成int
```
In [270]: type('14')
Out[270]: str
In [268]: int('10')
Out[268]: 10
In [269]: type(int('10'))
Out[269]: int
```
* Example: 判断输入字母为大小
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-20 22:37
# @Author  : anChow
# @File    : test.py

inp = raw_input('Please input [Yes/No]: ')
inp = inp.lower()                 # 输入的字符转换为小写

if inp.lower() == 'y' or inp == 'yes':
    print("Programe is runing ...")
elif inp.lower() == 'n' or inp == 'no':
    print("Programe is exit")
else:
    print("Please input [Yes/No]")
```
* Example: 大小写转换方法
```
In [271]: a = 'abcABC'
In [272]: a.lower()                # 转换为小写
Out[272]: 'abcabc'
In [273]: a.upper()                # 转换为大写
Out[273]: 'ABCABC'
```

## 0x02 扩展习题
> 输入三个整数x,y,z，请把这三个数由小到大输出。
> 企业发放的奖金根据利润提成

* Description
```
1. 输入三个整数x,y,z，请把这三个数由小到大输出。   1.程序分析：我们想办法把最小的数放到x上，先将x与y进行比较，如果x>y则将x与y的值进行交换，   然后再用x与z进行比较，如果x>z则将x与z的值进行交换，这样能使x最小。

2. 企业发放的奖金根据利润提成。
利润(I)低于或等于10万元时，奖金可提10%；
利润高于10万元，低于20万元时，低于10万元的部分按10%提成，高于10万元的部分，可提成7.5%；
20万到40万之间时，高于20万元的部分，可提成5%；
40万到60万之间时高于40万元的部分，可提成3%；
60万到100万之间时，高于60万元的部分，可提成1.5%，
高于100万元时，超过100万元的部分按1%提成，
从键盘输入当月利润I，求应发放奖金总数？
```

* Example: 第一题
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-25 10:37
# @Author  : anChow
# @File    : test.py

x = input("请输入数值x：")
y = input("请输入数值y：")
z = input("请输入数值z：")

tmp = 0
if x > y:
    tmp = x
    x = y
    y = tmp
if x > z:
    tmp = x
    x = z
    z = tmp
print("x = %d, y = %d, z = %d" % (x, y, z))
```
PS: 参考文档
    http://blog.csdn.net/weixin_38889645/article/details/76652271
* Example: 第二题
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-25 10:37
# @Author  : anChow
# @File    : test.py

i = input("请输入当月利润：")

if i >= 100000 and i <= 2000000:
    if i >= 100000:
        j = i * 0.1
    else:
        j = i * 0.75
elif i >= 2000000 and i <= 400000:
    j = i * 0.5
elif i >= 400000 and i <= 600000:
    j = i * 0.3
elif  i > 600000 and i <= 1000000:
    j = i * 1.5
elif i > 1000000:
    j = i * 1
print("i = %d, j = %d" % (i, j))
```
