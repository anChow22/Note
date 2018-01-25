## Python基础(第三天元组及字典)

*  学习目录   
> * 计算器  
> * tuple元祖  
> * dict字典  
> * 其他常用操作

---
## 0x01 计算器
* Example: 计算器  
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-23 17:30
# @Author  : anChow
# @File    : 计算器项目.py

def add(string):
    total = 0
    numbers = []
    numbers += string.split("+")
    for num in numbers:
        total += int(num.strip())
    print("{0} = {1}".format(string, total))

def reduce(string):
    result = 0
    numbers = []
    numbers += string.split("-")
    result = int(numbers[0].strip())
    numbers.pop(0)
    for num in numbers:
        result -= num.strip()
    print("{0} = {1}".format(string, result))

def ride(string):
    total = 1
    numbers = []
    numbers += string.split("*")
    for num in numbers:
        total *=int(num.strip())
    print("{0} = {1}".format(string, total))

def division(string):
    result = 0
    numbers = []
    numbers += string.split("/")
    result = int(numbers[0].strip())
    numbers.pop(0)
    for num in numbers:
        result /= int(num.strip())
    print("{0} = {1}".format(string, result))

if __name__ == '__main__':
    print(" #################################### ")
    print(" ##########     计算器    ########### ")
    print(" #################################### ")
    print("1: 加法")
    print("2: 减法")
    print("3: 乘法")
    print("4: 除法")
    method = int(input("Please input number(1/2/3/4): "))
    if method == "1":
        string = input("请输入你的表达式：")
        add(string)
    elif method == "2":
        string = input("请输入你的表达式：")
        reduce(string)
    elif method == "3":
        string = input("请输入你的表达式：")
        ride(string)
    elif method == "4":
        string = input("请输入你的表达式：")
        division(string)
    else:
        print("输入有误，重新输入。。。")
```

## 0x02 tuple元祖
> tuple为单元素时，一定要写','否则识别为tuple类型   
> count(value)      # 统计value个数  
> index(value)      # 返回第一个value元素的下标  

* Example: 方法使用
```
l = list()
print(l)

t = tuple()
print(t)

a1 = (1)
a2 = (1,)                    # 特别注意
print(type(a1))
print(type(a2))              # 注意数据类型

## 方法
m = (1, 2, 3, 4, 5, 1, 2, 3, 4, 5, 1, 2)
print(m.count(1))            # 统计元素个数
print(m.index(5))            # 返回第一个value元素的下标
```

## 0x03 dict字典
> 字典格式{key: value}  
> 字典可以存储任意对象，数据类型可以不相同  
> 字典定义  

* Example: 字典定义
```
d1 = dict(name = "Chow", age = 25)
A = {"ID": 10001, "name":"Chow"}
A = dict([("IP", "127.0.0.1"), ("address", "CQ")])
```

* Example: 字典方法
> get(keys)方法
> setdefault(k,v)方法
```
print(d1.get("name"))
print(d2.setdefault("name"))
print(d3.setdefault("address", "beijing"))
print(d2.keys())
print(d2.values())
```

* Example: 递归循环
> keys()方法  
> items()方法  

```
for i in d2.keys():
    print(i)
print(d2.values())    

for x, y in d3.items():
    print("key = {0}, value = {1}".format(x, y))
```

* Example: update()用法
> 与list相似  
```
x = list()
y = [1, 2, 3, 4, 5, 6]
x += y
print(x)

m = dict()
n = dict(name = "Robin", age = 20)
m.update(n)
print(m)
```

* Example: pop(key)用法
> 删除key所对应的元素,返回key所对应的返回值     
```
print(m)
keyDelete = m.pop("name")
print(keyDelete)
print(m)
```

## 0x04 其他常用操作
* Example: 常用方法操作
```
## help()
s = "dafsadafefsdaf"  
help(s.split)                # 注意方法不带括号  
restult = s.startswith("sa")  
print(restult)  

## dir()  
print(dir(s))                # 查看方法  

## type()                     # 查看类型  
a = '123'  
print(type(a))  
print(type(int(a)))  

## len()                      # 查看字符串长度  
print(len(a))  

## isinstance(a, type)        # 判断字符串类型，返回值为bool类型  
print(isinstance(s, str))  
print(isinstance(s, list))  

## print()  
python2     支持 print s1,s2,s3     代指不回车  
python3     函数, print(s, end="")  代指不回车  

## xrange()  
python2    存在 xrange()  range()  d.iteritems() d.items()  
python3    只存在range()  items()  

## input()  
python2  输入必须是整数， raw_input()自动输入的改成字符类型  
python3 输入的自动都转换为字符串类型  
```
