## Python基础(第七天)

*  学习目录  
> * 九宫格  
> * 函数入门  
> * 判断某天为某年的第几天  

---
## 0x01 九宫格  
* Example: 九宫格(python2)
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-27 22:05
# @Author  : anChow
# @File    : 九宫格.py

lines = list()                       # 空列表
for i in xrange(1, 10):             # 循环 第一个数
    for j in xrange(1, 10):         # 循环 第二个数
        if i == j:                   # 判断 i 和 j 是否相等
            continue                # 继续判断 是否相等
        for k in xrange(1, 10):     # 循环 第三个数
            if k == i:               # 判断 k 和 i 是否相等
                continue
            if k == j:               # 判断 k 和 j 是否相等
                continue
            if i+j+k != 15:          # 排除 三个数 的和不等于15 数字
                continue
            lines.append( (i, j, k) )    # 分别把 判断 出来的数值追加到列表， 以元组方式保存

print(lines)

count = 0
for line1 in lines:
    for line2 in lines:
        if line2[0] in line1:
            continue
        if line2[1] in line1:
            continue
        for line3 in lines:
            if line3[0] in line1:
                continue
            if line3[1] in line1:
                continue
            if line3[0] in line2:
                continue
            if line3[1] in line2:
                continue
            if line1[0] + line2[0] + line3[0] != 15:
                continue
            if line1[1] + line2[1] + line3[1] != 15:
                continue
            if line1[2] + line2[2] + line3[2] != 15:
                continue
            if line1[0] + line2[1] + line3[2] != 15:
                continue
            if line1[2] + line2[1] + line3[0] != 15:
                continue
            count += 1
            print("number:{0}\n{1}\n{2}\n{3}\n".format(count,line1,line2,line3))
```

## 0x02 函数入门  
* Example: 函数定义  
```
def a(args):
    pass
```

* Example: 函数定义分析
```
def(关键字)函数名(参数)：
    第一行缩进4字符                # 写代码逻辑
    return                        # 函数执行完，返回值
    pass                          # 什么都不干
    exit                          # 直接退出函数
```

* Example: 函数示例  
```
def add(x, y):
    print("x = {0}".format(x))
    print("x = {0}".format(x))
    print("x + y = {0}".format(x + y))
    return x + y
```

* Example: 计算累加和
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-29 12:50
# @Author  : anChow
# @File    : demon1.py

def add(args):
    total = 0
    for i in args:
        total += i
    return total

def main():
    number = list()
    s = input("Plase input digit like(a + b + c + d + ...):")
    for num in s.split("+"):
        number.append(int(num.strip()))
    print(add(number))

if __name__ == '__main__':
    main()
```

## 0x03 判断某天为某年的第几天
* Example: 实例(存在问题)  
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-29 13:18
# @Author  : anChow
# @File    : countday.py

ruinian = dict()
a = {"1": 31, "2": 28, "3": 31, "4": 31, "5": 31, "6": 30, "7": 31, "8": 30, "9": 31, "10": 30, "11": 31, "12": 30, }
b = {"1": 31, "2": 29, "3": 31, "4": 31, "5": 31, "6": 30, "7": 31, "8": 30, "9": 31, "10": 30, "11": 31, "12": 30, }

runnian["yes"] = b
runnian["no"] = a
print(runnian)

def panduan(year):
    if (year%4 == 0 & year%100 != 0) | year%400 ==0:
        return True
    else:
        return False

def countdays(date):
    days = 0
    year, month, day = date.split("-")
    if panduan(int(year)):
        if int(month) < 3:
            days = 31 + day
            print("{0}是今年的第{1}天".format(date, days))
        else:
           for i in range(1, int(month)):
               days += runnian["yes"][str(i)]
            days += int(day)
            print("{0}是今年的第{1}天".format(date, days))
    else:
            for i in range(1, int(month)):
                days += runnian["no"][str(i)]
            days += int(day)
            print("{0}是今年的第{1}天".format(date, days))

def main():
    date = input("data(linke 1970-10-1): ")
    ok = isint(date)
    if ok:
        countdays(date)
    else:
        print("输入有误！")

def isint(date):
    try:
        year, month, day = date.split("-")
        if int(year) < 0:
            return False
        if int(month) not in range(1, 13):
            return False
        if panduan(int(year)):
            for i in runnian["yes"].keys():
                if month == i:
                    if int(day) > 0 & int(day) < runnian["yes"][i]:
                        return  True
                    else:
                        return False
        else:
            for i in runnian["no"].keys():
                if month == i:
                    if int(day)  > 0 & int(day) <= runnian['no'][i]:
                    if int(day)  > 0 & int(day) <= runnian['no'][i]:
                        return True
                    else:
                        return False
    except Exception as e:
        return False

if __name__ == '__main__':
    main()
```
