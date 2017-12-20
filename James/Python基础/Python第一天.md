## Python基础(第一天)

*  学习目录
> * 为什么学习python
> * Python安装
> * Ipython安装

---
## 0x01  为什么学习Python

一、什么是python？
Python是一种解释型、面向对象、动态数据类型的计算机设计语言。
* 解释型语言： 开发过程中没有了编译环节。
* 交互式语言： 可以在一个Python提示符，直接互动执行程序。
* 面向对象语言: 支持面向对象的风格或代码封装在对象的编程技术。

二、python由来、设计思想、及协议
* python由Guido van Rossum(吉多·范罗苏姆)于1989年底发明。
* python设计哲学:“优雅”、“明确”、“简单”。
* Python 源代码遵循 GPL协议。

三、特点
* 易于学习：较少的关键字，结构简单，语法定义明确，学习简单。
* 易于阅读：代码定义清晰易读。
* 易于维护：源代码容易维护。
* 广泛的标准库：最大优势之一是丰富的库，跨平台的，在UNIX，Windows兼容性很好。
* 互动模式：互动模式的支持，可以从终端输入执行代码并获得结果，测试和调试代码片断。
* 可移植：基于开放源代码的特性，Python已经被移植到许多平台。
* 可扩展：python可以调用其它语言编写的代码。
* 数据库：提供所有主要商业数据库接口。
* GUI编程：支持GUI可以创建和移植到许多系统调用。
* 可嵌入: 可以将Python嵌入到C/C++程序，实现程序脚本化的能力。

四、python应用领域及范围
* 系统编程
* 用户图形接口
* Internet脚本
* 组件集成
* 数据库编程
* 游戏、图像、人工智能、XML 、机器人

五、python哲学思想
在Python解释器中,通过import this获取
* 优美胜于丑陋（以编写优美的代码为目标）
* 明了胜于晦涩（命名规范，风格相似）
* 简洁胜于复杂（简洁清晰，不以复杂的内部实现目标）
* 复杂胜于凌乱（避免复杂，代码间不能有难懂的关系，保持接口简洁，多加注释！）
* 扁平胜于嵌套（代码应当是扁平化，不能有太多嵌套）
* 间隔胜于紧凑（有适当的间隔，杜绝一行代码解决问题，一行代码不能超过80个字符，可以换行或起一个新的逻辑）
* 可读性很重要
* 即便假借特例的实用性之名，不可违背这些规则（这些规则至高无上），觉对不允许特列必须按照这个规则
* 不要包容所有错误，除非你确定需要这样做（捕获异常精确，不写 except:pass 风格的代码）
* 当存在多种可能，不要尝试去猜测！
* 而是尽量找一种，最好是唯一一种明显的解决方案（如果不确定，就用穷举法）
* 虽然这并不容易，因为你不是 Python 之父（这里的 Dutch 是指 Guido ）
* 做也许好过不做，但不假思索就动手还不如不做（动手之前要细思量）
* 如果你无法向人描述你的方案，那肯定不是一个好方案；反之亦然（方案测评标准）
* 命名空间是一种绝妙的理念

六、语言对比及种类
[1] 比较
* C和Python、Java、C#
     1. C语言： 代码编译得到机器码 ，机器码在处理器上直接执行，每一条指令控制CPU工作
     2. 其他语言： 代码编译得到字节码，虚拟机执行字节码并转换成机器码后在处理器上执行
* Python和CPython是由C开发而来
　   1. 使用：Python的类库齐全且使用简洁，如果实现同样的功能，Python10行代码解决，C可能需要100行甚至更多.
　   2. 速度：`ython的运行速度相较与C，慢
* Python和Java、C#
     1. 使用：Linux原装Python，其他语言没有；以上几门语言都有非常丰富的类库支持
　   2. 速度：Python在速度上稍显逊色  
[2] 种类
* Cpython
     * Python的官方版本，C语言实现，使用广泛，CPython实现会将源文件（py文件）转换成字节码文件（pyc文件），然后运行在Python虚拟机上。
* Jyhton
     * Python的Java实现，Jython会将Python代码动态编译成Java字节码，然后在JVM上运行。
* IronPython
     * Python的C#实现，IronPython将Python代码编译成C#字节码，然后在CLR上运行。（与Jython类似）
* PyPy（特殊）
     * Python实现的Python，将Python的字节码字节码再编译成机器码。
* 其它python

## 0x02  Python安装

一、 linux下安装Python(基于CentOS6.x)
> 查看默认Python版本
```
python -V
```

> 安装Python2.7.13
```
# yum install -y openssl-devel readline-devel unzip gcc gcc-c++
# wget https://www.python.org/ftp/python/2.7.13/Python-2.7.13.tgz --no-check-certificate
# tar xf Python-2.7.13.tgz
# cd Python-2.7.13
# ./configure --prefix=/usr/local/python27
# make && make install
# /usr/local/python27/bin/python
```

> 安装Python3.6.3
```
# yum install -y openssl-devel readline-devel unzip gcc gcc-c++
# wget https://www.python.org/ftp/python/3.6.3/Python-3.6.3.tgz --no-check-certificate
# tar xf Python-3.6.3.tgz
# cd Python-3.6.3
# ./configure --prefix=/usr/local/python36
# make && make install
# /usr/local/python36/bin/python3
```

> 查看安装后版本
```
/usr/local/bin/python2.7 -V
```
> 修改默认Python版本
```
mv /usr/bin/python /usr/bin/python2.6
ln -s /usr/local/bin/python27 /usr/bin/python
```

> 防止yum执行异常，修改yum使用的Python版本
```
vi /usr/bin/yum
将头部 #!/usr/bin/python 修改为 #!/usr/bin/python2.6
```
二、 windows下安装Python(基于win10)
> Windows下安装Python
```
* 下载安装包
* 安装
* 默认安装路径：C:\python27
* 配置环境变量
【右键计算机】-->【属性】-->【高级系统设置】-->【高级】-->【环境变量】-->【在第二个内容框中找到 变量名为Path 的一行，双击】--> 【Python安装目录追加到变值值中，用`;`分割】
PS：系统默认值`;``C:\python27`，切记前面有`分号`
```
三、安装ipython
> * 下载安装
```
# wget https://pypi.python.org/packages/09/2e/870d1058768f5240062beb0bd2ff789ac689923501b0dd6b480fb83314fc/ipython-5.0.0.tar.gz#md5=9c00df2f7e2e2636aba02671f45eea6b
# tar xf ipython-5.0.0.tar.gz
# cd ipython-5.0.0
# /usr/local/python27/bin/python2.7 setup.py build
# /usr/local/python27/bin/python2.7 setup.py install
```
> * 创建软链接
```
# ln -sv /usr/local/python27/bin/python2.7 /usr/bin/python27
# ln -sv /usr/local/python27/bin/ipython /usr/bin/ipython
```
> * 安装ipython扩展库
```
# /usr/local/python27/bin/ipython
# /usr/local/python27/bin/pip traitlets
# /usr/local/python27/bin/pip install traitlets
# /usr/local/python27/bin/pip install pygments
# /usr/local/python27/bin/pip install pexpect
# /usr/local/python27/bin/pip install --upgrade backports.shutil_get_terminal_size
# /usr/local/python27/bin/pip install pathlib2
# /usr/local/python27/bin/pip install pickleshare
# /usr/local/python27/bin/pip install enums
# /usr/local/python27/bin/pip install prompt_toolkit
# /usr/local/python27/bin/pip install simplegeneric
```
> * 运行ipython
```
# ipython
```
> * 参考安装文档
```
https://www.cnblogs.com/zhaojiedi1992/p/zhaojiedi_python_001.html
```


## Python基础(第二天)

学习目录
>  的文件类型
>  变量

一、Python的文件类型
1、扩展名
2、编写脚本，实现输出

* 扩展名
# py扩展名,由Python程序解释，不需要编译
# pyc扩展名，源码文件经过编译后生成的扩展名
# pyo扩展名，经过优化后的源码文件

* Example: 创建py文件
```
# vim hello.py

#!//usr/bin/env python
# -*- conding:utf-8 -*-                #指定字符编码

print “Hello World”                    #打印输出

python ./hello.py                      #运行行脚本
```

* Example:  编译生成pyc文件
```
# vim hello.py

#!//usr/bin/env python
# -*- conding:utf-8 -*-

import py_compile                     # 导入编译模块

py_compile.compile('hello.py')        # 调用编译模块compile()方法      
```

* Example:  查看编译后的文件信息
```
file hello.py
```

* Example: 生成pyo文件
```
python -O -m py_compile hello.py
```
PS：执行脚本方式
   * 进入脚本存放目录执行脚本
   * 全路径执行脚本
   * 给脚本赋予执行权限,执行脚本


二、变量
1、变量命名
2、变量赋值
3、运算符与表达式

* 变量命名
  -- 由字母、数字、下划线组成
  -- 不能与数字开头
  -- 不能使用关键字

* 变量赋值
  -- 变量的声明和定义过程

* Example: 变量赋值
```
# name1 = 10
# name2 = name1
# print("name1的值为：",name1)
# print("name2的值为：",name2)

输出结果
name1的值为： 10
name2的值为： 10
```

* Example: 通过ID查看内存值
```
# name1 = 10
# name2 = name1
# print("name1的值为：",id(name1))
# print("name2的值为：",id(name2))

输出结果
name1的值为： 1676475168   
name2的值为： 1676475168

PS：通过ID可以查看name1和name2在内存中的值相同
```

* Example:  重新赋值变量
```
# name1 = 10
# name2 = name1
# name1 = 100                                # name1重新赋值后
# print("name1的值为：",name1)
# print("name2的值为：",name2)
# print("重新赋值后name1的值为：",name1)

输出结果
name1的值为： 100                             # 值已更新
name2的值为： 10                              # 值未变
重新赋值后name1的值为： 100
```

* Example: id查看内存值
```
# name1 = 10
# name2 = name1
# name1 = 100
# print("name1的值为：",id(name1))
# print("name2的值为：",id(name2))
# print("重新赋值后name1的值为：",id(name1))

输出结果
name1的值为： 1676478048                      # 重新赋值后，内存值发生改变
name2的值为： 1676475168                      # 内存值未发生改变
重新赋值后name1的值为： 1676478048   
```

* Example: 查看字符是否是关键字
```
>>> keyword.iskeyword('False')
True
>>> keyword.iskeyword('for')
True
>>> keyword.iskeyword('else')
True
>>> keyword.iskeyword('in')
True
>>> keyword.iskeyword('aaa')                 # 不是关键字
False
>>> keyword.iskeyword('ccc')                 # 不是关键字
False
```
PS：python中，为系统关键字为True,不是系统关键字为False


* 运算符与表达式
> * 运算符
  -- 赋值运算符
  -- 算术运算符
  -- 关系运算符
  -- 逻辑运算符
> * 表达式
  -- 将不同的数据(包括变量、函数)用运算符号按一定规则连接起来的一种式子

* 赋值运算符
```
=         # 赋值
+=        # 在变量值上做加法运算
-=        # 在变量值上做剑法运算
*=        # 在变量值上做乘法运算
/=        # 在变量值上做除法运算
%=        # 在变量值上做取余运算
```
* 算术运算符
```
+         # 加
-         # 减
*         # 乘
/         # 除
//        # 整除
%         # 取余
**        # 乘方
```
* 关系运算符
```
>          # 大于
<          # 小于
>=         # 大于等于
<=         # 小于等于
==         # 等于
!=         # 不等于
```
PS: 该运算符的值为: True 和 False
* 逻辑运算符
```
and        # 与         True and False
or         # 或         False or True
not        # 非         not True
```

* Example: type()查看变量类型
```
In [1]: x = 'Chow'
In [2]: type(x)
Out[2]: st
```
* 运算符优先级
```
Lambda --> 逻辑运算符(or) --> 逻辑运算符(and) --> 逻辑运算符(not) --> 成员测试(in， not in) --> 同一性测试(is, is not) --> 比较运算符 --> 按位或(|) --> 按位异或(^) --> 按位与(&) --> 移位(<< , >>) --> 加法与减法 --> 乘法、除法(/)、取余(%) --> 正负号(+x , -x) --> 按位翻转(~x) --> 指数(**)             
```


作业：
    -- 要求从键盘读取数字

* Example: 写一个四则运算符    
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-19 22:40
# @Author  : anChow
# @File    : test.py

a = int(input("请输入第一个数字: "))
b = int(input("请输入第二个数字: "))

print("a + b = %s" %(a + b))
print("a - b = %s" %(a - b))
print("a * b = %s" %(a * b))
print("a / b = %s" %(a / b))
```

* Example: 在未看视频前写出来
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-19 22:40
# @Author  : anChow
# @File    : test.py

a = int(input("请输入第一个数字: "))
b = int(input("请输入第二个数字: "))
c = int(input("请输入第三个数字: "))
d = int(input("请输入第四个数字: "))

num = a + b * c / d
print("计算的结果为: %s" %num)
```
PS： input() 与 raw_input() 区别
   -- 都是内建函数
   -- 通过控制台输入与用户实现交互
   -- 接收字符串
   -- raw_input() 返回字符串类型
   -- input() 返回数值类型
