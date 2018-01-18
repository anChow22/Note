## Python基础(第十六天)

*  学习目录  
> * 类的继承   
> * 类的属性总结  
> * 类方法总结  

---
## 0x01 类的继承  
> 继承是面向对象重要特性之一  
> 继承关系: 继承是相对两个类而言的父子关系，子类继承了父类所有公有属性和方法    
> 继承实现代码重用   
> 继承可以重用已经存在的数据和行为，减少代码重复编写。使用一对括号表示继承关系，括号中的类即为父类  
> class Myclass(ParentClass)  
  -- 父类定义__init__方法，子类必须显示调用父类的__init__方法  
> ParentClass.__init__(self,[args...])  
  -- 子类需要扩展父类行为，可以添加__init__方法  

* Example: 类的继承示例
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-17 2:12
# @Author  : anChow
# @File    : 创建内部类.py

class People(object):
    color = 'yellow'
    __age = 30

    def __init__(self,c):
        print("Init.....")
        self.dwell = 'Earth'

    def think(self):
        print("I am a %s" %self.color)
        print("I am a thinker")

class Chinese(People):
    def __init__(self):
        People.__init__(self, 'red')
    pass

cn = Chinese()
# print(cn.color)
# print(cn.color)
# print(cn.dwell)
# cn.think()
```

> super函数  

* Example: super内置函数  
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-17 2:12
# @Author  : anChow
# @File    : 创建内部类.py

class People(object):
    color = 'yellow'
    __age = 30

    def __init__(self,c):
        print("Init.....")
        self.dwell = 'Earth'

    def think(self):
        print("I am a %s" %self.color)
        print("I am a thinker")

class Chinese(People):
    def __init__(self):
        super(Chinese, self).__init__( 'read')
        People.__init__(self, 'red')
    pass

cn = Chinese()
cn.think()
```

> 多重继承  
  --- 一个类可以继承多个父类  
> 语法  
  --- class class_name(Parent_c1, Parent_c2....)  
> 注意  
  ---  父类出现多个自定义__init__方法时，多重继承只执行第一个类的__init__方法，其它不执行      

* Example: 多重继承
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-17 2:12
# @Author  : anChow
# @File    : 创建内部类.py

#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-17 23:45
# @Author  : anChow
# @File    : 多重继承.py

class People(object):
    color = 'yellow'

    def __init__(self):
        self.dwell = 'Earth'
        self.color = 'yellow'

    def think(self):
        print("I am a %s" %self.color)
        print("My home is %s" %self.dwell)

class Martian(object):
    color = 'red'

    def __init__(self):
        self.dwell = 'Martian'

    def talk(self):
        print("I like talking")

class Chinese(Martian, People):
    def __init__(self):
        People.__init__(self)

cn = Chinese()
cn.think()
cn.talk()
```

## 0x02 类的属性总结  
> 类属性，也是共有属性    
> 私有属性    
> 对象共有属性    
> 对象私有属性   
> 内置属性   
> 函数的局部变量   
> 全局变量   

* Example: 类的属性
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-18 0:02
# @Author  : anChow
# @File    : 类的属性.py

var5 = "全局变量 var5"
class MyClass(object):
    var1 = '类属性，类的公有属性 var1'
    __var2 = '类的私有属性 __var2'

    def func1(self):
        self.var3 = '对象的公有属性 var3'
        self.__var4 = '对象的私有属性 __var4'
        var5 = '函数的局部变量'
        print(self.__var4)
        print(var5)

    def func2(self):
        print(self.var1)
        print(self.__var2)
        print(self.var3)
        print(self.__var4)

mc = MyClass()                  # 实例化类
print(mc.var1)                 # 访问公有属性
# print(mc.__MyClass__var2)     # 访问私有属性，不推荐这样使用
mc.func1()                      # 调用方法
mc.func2()
print(mc.var3)                 # 访问方法
```

## 0x03 类方法总结
> 公有方法    
> 私有方法     
> 类方法    
> 静态方法    
> 内置方法   

* Example: 类方法
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-18 9:44
# @Author  : anChow
# @File    : 类方法总结.py

class MyClass(object):
    name = 'Test'

    def __init__(self):                 # 内置方法，构造函数
        self.func1()
        self.__func2()
        self.classFun()
        self.staticFun()

    def func1(self):
        print(self.name,)
        print("公有方法")
        self.__func2()                   # 调用私有方法， 只能内部调用

    def __func2(self):
        print(self.name,)
        print("私有方法")

    @classmethod                         # 装饰器
    def classFun(self):
        print(self.name,)
        print("类方法")

    @staticmethod                       # 装饰器
    def staticFun():
        print(MyClass.name,)
        print("静态方法")

mc = MyClass()
# 这里已经被__init__内方法调用
# mc.func1()                                 # 调用公有方法
# MyClass.classFun()                         # 调用类方法，需要借用@classmethod 装饰器完成
# MyClass.staticFun()                        # 调用静态方法， 需借用@staticmethod装饰器完成
```
