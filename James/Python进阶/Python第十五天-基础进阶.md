## Python基础(第十五天)

*  学习目录  
> * 类的属性  
> * 类的方法  
> * 类的内置方法  

---
## 0x01 类的属性  
>  类的组成  
    -- 由属性和方法组成    
    -- 属性是对数据的封装  
    -- 方法是对类行为的封装  
        --- 成员变量 -- 静态属性   
        --- 成员函数 -- 动态方法    
>  对象的创建  
   -- 创建对象的过程称为实例化  
   -- 对象被创建后， 包含三个特性： 对象  句柄   属性和方法  
   -- 对象属性和方法与类中的成员变量和成员函数对应  
   -- obj = MyClass()   # 实例化类对象   
   -- 通过对象来调用方法和属性  
>  类的属性  
   -- 分类： 公有属性  私有属性  
      --- 公有属性: 在类中和类外都能调用的属性   
      --- 私有属性： 不能再类外及被类以外的函数调用  
      --- 定义方式: 以"__"双下划线开始的成员变量就是私有属性    
      --- 可通过instance._classname__attribute方式访问     
   -- 属性范围取决于属性名称      
   -- 内置属性： 由系统在定义类的时候默认添加  
      --- 由前后双下划线构成: __dic__  及  __module__  

* Example: 公有属性 私有属性 内置方法  
```
#!/usr/bin/env python

class People(object):
    color = 'yellow'                # 公有属性
    __age = 30                      # 私有属性

    def think(self):                # 方法， 相当于函数，self为类本身， 默认值
        self.color = "Black"        # 调用类属性， 进行重新赋值
        print("I am a %s" % self.color)
        print("I am a thinker")
        print self.__age            # 输出私有属性

ren = People()                      # 对People进行实例化为ren对象
ren.color = '白色恋人'               # 通过对象修改属性值  
print(ren.color)                    # 通过对象调用类的属性  
ren.think()                         # 通过对象调用类的方法  
print ren.__dict__                  # 通过对象访问私有属性
print '#' * 30
print People.color                  # 调用类访问属性, 私有属性不能通过类访问
print '-' * 30
print People.__dict__               # 通过类调用私有属性
```

## 0x02 类的方法  
>  公有方法  
   --- 在类中和类外都能调用的方法  
>  私有方法   
   --- 不能被类的外部调用，在方法前面加"__"双下划线  
>  self参数  
   --- 用于区分函数和类的方法  
   --- 表示执行对象本身     
>  类方法  
   --- 被classmethod() 函数处理过的函数，能被类调用， 也能被对象调用(继承关系)  
>  静态方法  
   --- 相当于 "全局函数" 可被类直接调用，可悲所有实例化对象共享  
   --- 通过staticmethod()定义  
   --- 没有 "self" 参数  
>  装饰器  
   --- @classmethod  
   --- @staticmethod    

* Example:
```
#!/usr/bin/env python

class People(object):
    color = 'yellow'                # 公有属性
    __age = 30                      # 私有属性

    def think(self):                # 方法， 相当于函数，self为类本身， 默认值
        self.color = "Black"        # 调用类属性， 进行重新赋值
        print("I am a %s" % self.color)
        print("I am a thinker")
        print self.__age            # 输出私有属性

    def __talk(self):               # 私有方法
       print('I am talking with Tom')

    def test(self)：                # 公有方法
        self.__talk()               # 调用方法

Chow = People()                     # 实例化对象
Chow.test()                         # 实力调用方方法执行
```

* Example: 动态类方法 及  静态类方法  
```
#!/usr/bin/env python

class People(object):
    color = 'yellow'                # 公有属性
    __age = 30                      # 私有属性

def test(self)：                    # 把test()变成动态类方法      
    print('Testing...')

    cm = classmethod(test)          # 通过classmethod()函数变成动态类方法

def robin()：                       # 把test()变成静态类方法      
    print('This is func')

    sm = staticmethod(test)         # 通过classmethod()函数变成动态类方法    

People.sm()                         # 调用静态类方法
```
* Example: 装饰器  
```

```

## 0x03 类的内置方法  
> 内部类  
  -- 在类的内部定义类  
  -- 主要目的是为了更好抽象现实世界   
> 内部类的实例化方法    
  -- 方法1： 直接调用外部类调用内部类  
     --- object_name = Outclass_name.inclass_name()  
  -- 方法2： 先对外部类进行实例化，然后再实例化内部类  
     --- out_name = Outclass_name()  
     --- in_name = out_name.inclass_name()  
     --- in_name.method()      
> 魔术方法  
  -- __str__(self)    
> * 构造函数与析构函数  
    --- 构造函数： 用于初始化类内部状态  
      --- __init__():
            可选，不提供，会给出默认__init__方法  
    --- 析构函数: 用于释放对象占用资源
       --- __del__():  
             可选，不提供，会在后台提供默认析构函数    
> 垃圾回收机制
  -- 清理不再使用对象。提供gc模块释放不再使用对象。
  -- 采用"引用计数"算法方式处理回收
  -- gc模块的collect()可以一次性收集所有待处理对象(gc.collect)

* Example: 创建内部类,三种方法访问
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-17 2:12
# @Author  : anChow
# @File    : 创建内部类.py

# class People(object):
#     color = 'yellow'
#     __age = 30
#
#     ## 第一种类的嵌套
#     class Chiness(object):        # 创建内部类
#         print('I am chiness')
#
# ## 第一种方法类调用
# jack = People.Chiness()             # 调用内部类

# class People(object):
#     color = 'yellow'
#     __age = 30
#
#     ## 第二种类的嵌套
#     class Chiness(object):        # 创建内部类
#         name = "I am chinese"
#
# ## 第二种方法类调用
# jack = People.Chiness()             # 调用内部类
# print(jack.name)


class People(object):
    color = 'yellow'
    __age = 30

    ## 第三种类的嵌套
    class Chiness(object):        # 创建内部类
        name = "I am chinese"

## 第三种方法类调用
# print(People.Chiness().name)
print(People.Chiness.name)
```

* Example：普通用法与__str__()方法用法
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-17 2:12
# @Author  : anChow
# @File    : 创建内部类.py

# class People(object):
#     color = 'yellow'
#     __age = 30
#
#     ## 第三种类的嵌套
#     class Chiness(object):        # 创建内部类
#         name = "I am chinese"
#
# ## 第三种方法类调用
# ren = People()
# print(ren)

class People(object):
    color = 'yellow'
    __age = 30

    ## 第三种类的嵌套
    class Chiness(object):        # 创建内部类
        name = "I am chinese"

    def __str__(self):
        return "This is People class"

## 第三种方法类调用
ren = People()
print(ren.__str__())
```

* Example：__init__()初始化类
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-17 2:12
# @Author  : anChow
# @File    : 创建内部类.py

class People(object):
    color = 'yellow'
    __age = 30

    ## 第三种类的嵌套
    class Chiness(object):        # 创建内部类
        name = "I am chinese"

    def __str__(self):
        return "This is People class"

    def __init__(self, C = 'Python'):     # 初始化时，传递参数
        self.color = C

## 第三种方法类调用
ren = People()
print(ren.__str__())
print(ren.color)
print(People.color)
```

* Example：__del__()
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-17 2:12
# @Author  : anChow
# @File    : 创建内部类.py

class People(object):
    color = 'yellow'
    __age = 30

    ## 第三种类的嵌套
    class Chiness(object):        # 创建内部类
        name = "I am chinese"

    def __init__(self, C = 'Python'):     # 初始化时，传递参数
        print("Init .......")
        self.color = C
        self.talk()

    def __talk(self):
        print("I am talking with Tom")

    def __del__(self):
        print("Del......")
        self.fd.close()

## 第三种方法类调用
ren = People('Green')
print(ren.__str__())
print(ren.color)
print(People.color)
print("Main end")
```

* Example：gc模块用法
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-17 2:12
# @Author  : anChow
# @File    : 创建内部类.py

import gc

class People(object):
    color = 'yellow'
    __age = 30

    ## 第三种类的嵌套
    class Chiness(object):        # 创建内部类
        name = "I am chinese"

    def __init__(self, C = 'Python'):     # 初始化时，传递参数
        print("Init .......")
        self.color = C
        self.talk()

    def __talk(self):
        print("I am talking with Tom")

    def __del__(self):
        print("Del......")
        self.fd.close()

print(gc.collect())
jack = People('green')
print("Jack.color")
print("People.color")       
```
