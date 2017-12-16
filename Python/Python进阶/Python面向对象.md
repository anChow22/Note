## Python面向对象

*  Description
>  面向对象
>    
>  
--------------------------------------------------------------------------------


> ## 面向对象  
> * 一切皆对象，包括(变量、元组、函数等)  
> * 面向对象: 实际上是解决问的步骤，通过函数去实现，强调过程
> * 面向过程： 把变量和函数放在一起，作为相互依存的整体。通过变量和函数组成的类。类中的变量称为属性，类中的函数成为方法  
> * 对象 ≠ 类。 类是对象的抽象。类可以根据属性和方法进行抽象，实例化后的对象。

* **@类属性**  
> * 变量称为类的属性，函数称为类的方法  
> * 公有属性：在类中和类外都能调用的属性，与变量定义一致, 如 sex = 'Men'  
> * 私有属性：不能再类外及类以外的函数调用，以双下划线开头, 如 __name = 'Chow'       
> * 内置属性：系统定义类，以双下划线构成, 如 __init__

* Example:
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-15 15:20
# @Author  : anChow
# @File    : test.py

class Dog(object):                      # 定义类，object 是超级类，所有类必须继承该类
    color = 'yellow'                    # 类属性
    def think(self):                    # 类方法
        print()"I am a anChow")

ren = Dog()                             # 通过类实例化对象
print(ren.color)                        # 可以通过对象访问类的属性
ren.think()                             # 可以通过对象执行类的方法
```
* Example:
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-16 10:05
# @Author  : anChow
# @File    : test.py

class People(object):                    # 定义类  
    color = 'yellow'                     # 定义公有属性
    __name = 'Men'                       # 定义私有属性
    def think(self):                     # 定义类的方法
        print(self.__name)               # 在类下调用私有属性

ren = People()                           # 通过类实例化对象                 
print(ren.color)                         # 对实例化的公有属性进行输出
ren.think()                              # 调用实例化方法
print(ren.__init__)                      # 调用实例化的内置属性
```
* **@类方法**  
> * 公有方法：在`类中`和`类外`都能调用的方法  
> * 私有方法：`只能在类中`调用，类外不能调用。在类前面加`__`双划线，如`__name(self)`    
> * 类方法：被类直接调用的方法称为类方法，通过classmethod()函数处理后，才能被类直接调用  
> * 静态方法：相当于全局函数，类直接调用。通过staticmethod()处理后才能被直接调用  
> * 注意，静态方法没有`self`参数

* Example: 私用方法与公有方法使用
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-16 11:20
# @Author  : anChow
# @File    : test.py

class People(object):
    color = 'yellow'
    __age = 30

    def __talk(self):                   # 私有方法，方法前面加双下划线
        print "I am talking with Tom"

    def test(self):                     # 公有方法，和函数一样，self参数，表示执行对象本身
        self.__talk()                   # 在类的内部调用私有方法

jack = People()                         # 实例化对象
jack.test()                             # 调用对象公有方法
```
* Example: classmethod() ---> 类方法
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-16 11:20
# @Author  : anChow
# @File    : test.py

class People(object):
    color = 'yellow'
    __age = 30

    def test(self):                     # 公有方法,带有`self`参数
        print('I'am anChow)

    ct = classmethod(test)              # 通过classmethod()函数转换成类方法

jack = People()                         # 实例化对象
People.ct()                             # 公有方法不可以通过类直接调用，只能通过对象调用；转换成类方法后，可直接调用
```
* Example: staticmthod()  --- > 静态方法
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-16 11:20
# @Author  : anChow
# @File    : test.py

class People(object):
    color = 'yellow'
    __age = 30

    def test():                         # 公有方法，`未加self参数`，只能称为`函数`
        print('I'am anChow)

    st = staticmethod(test)             # 通过staticmethod()函数转换成静态方法    

jack = People()                         # 实例化对象
People.st()                             # 静态方法可以通过类直接调用
```
* **@内部类**  
> * 在类的内部定义的类  
> * 目的: 更好的抽象现实世界

* Example: 通过外部类调用内部类实例化对象
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-16 11:20
# @Author  : anChow
# @File    : test.py

class People(object):                   # 定义类
    color = 'yellow'
    __age = 30

    class anChow(object):               # 定义内部类
        print("I’am anChow")

t = People.anChow()                     # 通过外部类调用内部类再实例化对象
```
* Example: 通过外部类调用内部类再实例化对象
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-16 11:20
# @Author  : anChow
# @File    : test.py

class People(object):                   # 定义类
    color = 'yellow'
    __age = 30

    class anChow(object):               # 定义内部类
        print("I’am anChow")

ren = People()                         # 实例化外部类
x = People.anChow()                    # 通过外部类调用内部类再实例化对象
```
* **@内置方法**  
> * __str__ 方法   
> * __init__ 方法  
> * __del__  方法

* Example: __str__ 方法 ---> 返回字符串
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-16 11:55
# @Author  : anChow
# @File    : test.py

class People(object):
    pass

    def __str__(self):                 # 返回字符串
        return "This is a people"

ren = People()                         # 实例化对象
print ren
```
* Example: __init__ 方法 ---> 用于类的初始化  
> * 当实例化对象是，自动执行__init__下面的属性及方法  
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-16 12:10
# @Author  : anChow
# @File    : test.py

class People(object):
    color = 'yellow'

    def __init__(self):
        self.color = 'black'

ren = People()                        # 实例化对象，执行__init__下属性，对color重新赋值
print(ren.color)                      # 调用实例化下面的__init__方法及属性
print(People.color)                   # 调用类时，类下的方法不做改变
```

* Example: __del__ 方法 ---> 用于释放对象所占用资源
> * 在脚本要退出之前执行
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2017-12-16 12:30
# @Author  : anChow
# @File    : test.py

class People(object):
    color = 'yellow'

    def __init__(self):
        self.fd = open('/etc/passwd')  # 打开passwd文件

    def __del__(self):
        self.fd.close()                # 通过__del__关掉打开的文件

ren = People()
print(ren)
```
> ## 面向对象思想  
> * 封装：封装实质是类的定义，把变量和函数封装在一起组成类  
> * 继承：可以使得子类具有父类的属性和方法。重新定义、追加属性和方法  
> * 多态：相同操作作用于不同对象，有不同解释和产生不同执行结果  
* **@类的继承**


* **@多重继承**


* **@类的重写**
