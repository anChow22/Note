## Python基础(第一天)

*  学习目录  
> * 读写文件  
> * 文件方法  
> * Python2编码问题  
> * Python对passwd文件进行排查

---
## 0x01  读写文件  
* Example: 读文件操作  
```
f = open("1.txt", "r")
text = f.readlines()
print(text)
f.close()
```

* Example: 写文件操作  
```
f = open("1.txt", "w")
f.write("Hello World")
f.close()
```

* Example: 文件常用方法  
```
with
codecs
```

* Example: 读写文件操作示例  
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-27 14:06
# @Author  : anChow
# @File    : demonWrite.py

if __name__ == '__main_':
    filename = input("Please input the name of file: ")
    f = open(filename, "w")
    while 1:                     # 写成"1"效率高过"True"
        context = input("cplease input context('EOF' will close file): ")
        if context == "EOF":     # 文件结束描述符
            f.close()
            # exit(1)            # 若不需要读出，直接退出
            break
        else:
            f.write(context)
            f.write("\n")

    fRead = open(filename,encoding="utf-8")
    readContext = fRead.read()
    print("###################### start #######################")
    print(readContext)
    print("###################### end #######################")
    fRead.close()
```

## 0x02 文件方法  
* Example: 文件常用方法  
```
readline()
readlines()
next()
read()
write()                     # 写入字符串
writelines()                # 参数是系列，会迭代写入
```

* Example: 文件属性    
```
f.name
f.closed
f.endoding
f.mode
```

* Example: 文件属性    
```
ENCODING = "utf-8"              # 宏定义
f = open("1.log", encoding=ENCODING)
print(dir(f))                  # 显示文件属性  
print(f.name)                  # 读取文件名称  
print(f.mode)                  # 查看文件模式(r w x)  
print(f.readline())            # 一行一行读取  
print(f.readlines())           # 读取所有， 以列表形式展示  
print(f.next())                # python3已取消  
print(f.closed)                # 关闭文件
```

* Example: with方法   
```
with open("1.log", "r", encoding=ENCODING) as f:
    print(f.read())            # 使用with方法不需要close关闭
```

* Example: with 及 codecs用法   
```
import codecs               # 注意,使用时需要导入模块
with codecs.open("1.log", "r", encoding=ENCODING) as f:
    print(f.read())
```

## 0x03 Python2编码问题  
> 编码  
  --- 支持中文编码: utf-8  gbk   gb2312  
  --- decode       # 解码  
  --- encode       # 编码  
> 定义编码支持中文格式  
  --- #_*_ conding:utf-8 _*_
  --- #conding:utf-8
> 转码过程  
  --- 源有编码 --> unicode编码 --> 目的编码  

* Example: 编码第一种方式
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-                # 指定编码格式
```

* Example: 编码第二种方式
```
s = u"大家好！"                        # 指定为unicode格式
print(s)
```

* Example: 控制台乱码  
```
## 第一种方式
#!/usr/bin/env python
# _*_ coding:utf-8 _*_
s = "你好！"
print(s)


## 第二种方式
# _*_ coding:utf-8 _*_
s = u"你好"
print(s)
print(type(s))            # unicode
m = "不太好"
```

* Example: 编码转码
```
s = "你好!"
print(s.decode("utf-8"))         # 解码
print(s)
print(type(s))
l = [1, 2, 3, "大家好才是真的好"]
print(l[4].decode("utf-8"))      # 解码
print(l)
```

* Example: 编码转码
```
m = "中文"
print(m.encode("utf-8").encode("gbk"))      # 先解码，后编码
```

## 0x04 Python对passwd文件进行排序 
* Example: 对passwd文件排序  
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-28 17:33
# @Author  : anChow
# @File    : sortUidPasswd.py

import codecs

file = "passwd"
sortfile = "sortpasswd.txt"

filecontext = []
sortuid = []

with codecs.open(sortfile, "wb") as fsort:
    with codecs.open(file, encoding="utf-8") as f:
        filecontext += f.readlines()
        for line in filecontext:
            sortuid.append(int(line.split(":")[2]))
        sortuid.sort()
        for uid in sortuid:
            for line in filecontext:
                if str(uid) == line.split(":")[2]:
                    print(line)
                    fsort.write(line.encode("utf-8"))
```
