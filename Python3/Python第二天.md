## Python基础(第二天 Python基础)

*  学习目录  
> * 运算符  
> * 数据类型   
> * 列表  

---
## 0x01 运算符    
> 数字运算符    
> 关系运算符    
> 赋值运算符    
> 逻辑运算符  
  --- and  or  not   

## 0x02 数据类型  
> 整型(int)   
> 布尔类型(bool)   值为 True 或 False    
> 浮点型(float)    例: 3.1415926  
> 字符串(str)  


* Example: 字符串find查找下标  
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-23 10:13
# @Author  : anChow
# @File    : 字符串find查找下标.py

string = "abcdefghigh"
print(string)

# find查找
print(string[:])
result = string.find('def')       # 注意find用法
print(result)
```

* Example: 字符串replace()替换字符
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-23 10:17
# @Author  : anChow
# @File    : replace替换字符.py

string = "abcdefghigh"
print(string)

# replace
print(string.replace('a', "AAAA"))
```

* Example: 字符串split()分隔符,以列表形式存储
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-23 10:21
# @Author  : anChow
# @File    : split分隔符.py

string = "abcadefaghiagh"
print(string)

# split() 分隔符
print(string.split('a'))
```

* Example: 字符串strip()去掉字符串前后空字符
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-23 10:24
# @Author  : anChow
# @File    : strip去掉字符串前后空字符.py

string = "    abcadefaghiagh   "
print(string)
print("My string is: %s" %string)
print("My string is: {0}".format(string))      # 推荐使用
print("Hello" + "World" + "Python")            # 字符串拼接
print(string.strip())                          # 去掉字符串左右空格
```

* Example: 字符串链接方法
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-23 10:34
# @Author  : anChow
# @File    : 字符串连接方法.py

string = "    abcadefaghiagh   "
print(string)
print("My string is: %s" %string)
print("My string is: {0}".format(string))      # 推荐使用
print("Hello" + "World" + "Python")            # 字符串拼接
NewList = string.split('a')                    #
print(NewList)
## join(可迭代对象)，一般是list
print(" ### ".join(NewList))                   # 以# 作为字符串分隔符，join()进行连接
```

## 0x03 列表(List)
> 列表由一序列特定顺序排列的元素组成。把字符串、数字、字典都可以加入到列表。下标默认从0开始  
> 列表方法应用


* Example: 创建列表  
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-23 11:49
# @Author  : anChow
# @File    : 列表.py

l = [1,2,3.1415926,'a','b','c',True,{"name":"Chown"}]
print(l)
```

* Example: append() 追加元素  
```
l = [1,2,3.1415926,'a','b','c',True,{"name":"Chown"}]
l.append({"age":30})                        # 追加元素
print(l)
```

* Example: pop移除元素，默认移除最后一位  
```
l = [1,2,3.1415926,'a','b','c',True,{"name":"Chown"}]
m = l.pop(2)                                   # 移除下表为2的元素
print("m = {0}".format(m))                     
print(l)
```

* Example: index() 返回元素下标   
```
print(l.index('b'))
```

* Example: sort()排序    
```
m = [1, 34, 12, 231, 34423, 3, 11, 54]
m.sort()                                      # 排序
print(m)
m.reverse()                                   # 反转
print(m)
```

* Example: insert() 插入  
```
m.insert(1,6546)                              # 在下表为1的地区插入值
print(m)
```
