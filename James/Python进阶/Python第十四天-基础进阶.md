## Python基础(第九天)

*  学习目录  
> * 模块使用  
> * 面向对象介绍  

---
## 0x01 模块使用
> 模块  
  -- 组织代码的基本方式  
  -- 可独立运行，也可以导入到其它脚本运行  
  -- .py文件都可以作为一个模块导入  
  -- 名称与脚本文件名相同  
  -- 通过import导入  
> 包  
  -- 模块可以按目录组织为包  
  -- 创建包的步骤   
     --- 创建名字为包名的目录   
     --- 该目录下创建__init__.py文件  
     --- 根据需求，在目录下存放脚本文件或便宜的扩展及子包  
     --- imoprt pack1, pack2, pack3  
> 获取Python路径  
   -- sys.path  
   -- export PYTHONPATH     

* Example: 查看当前系统模块路径
```
In [128]: import sys              # 导入模块
In [129]: sys.path                # 获取系统模块路径
```
* Example：定义python开发环境路径
```
[root@p6 python]# mkdir /root/soft        # 创建文件路径
In [130]: sys.path.append('/root/soft')   # 加入系统模块
In [131]: sys.path                        # 查看系统模块加载情况
[root@p6 python]# vi /root/.bashrc        # 加入系统开发环境变量
export PYTHONPATH=/root/soft              # 加入开发路径
[root@p6 python]# . /root/.bashrc         # 生成文件路径
[root@p6 python]# echo $PYTHONPATH        # 查看加入的环境变量
/root/soft
In [1]: import sys                        # 导入模块
In [2]: sys.path                          # 查看加入python环境路径
```
* Example：统计文件字符及单词、行数
```
#!/usr/bin/env python

#!/usr/bin/env python

def wordCount(s):
    chars = len(s)
    words = len(s.split())
    lines = len(s.split('\n'))
    print(lines, words, chars)

if __name__ == '__main__':            # 判断是main 调用当前函数
    s = open('/etc/passwd').read()
    wordCount(s)
```
* Example：引用上面模块
```
#!/usr/bin/env python

import world                          # 导入world自定义模块

s = """Hello World Python"""

world.wordCount(s)                    # 获取字符串字数
```
* Example：包的引用及用法
```
from 文件目录 import 模块

from python import world
from python.world import wordcount
from python.world import wordcount as world
import python.world
python.world.wordcount('Hello world\n')
```

## 0x02 面向对象
>  面向过程  
>  面向对象  
>  类和对象  

> * 类的内置方法  
```
class 类名:
    成员变量 - 属性
    成员函数 - 方法
```

* Example: 定义类
```
#!/usr/bin/env python

class People(object):               # 定义类
    color = 'yellow'                # 公有属性， 相当于变量

    def think(self):                # 方法， 相当于函数，self为类本身， 默认值
        self.color = "Black"        # 调用类属性， 进行重新赋值
        print("I am a %s" % self.color)
        print("I am a thinker")

ren = People()                      # 对People进行实例化为ren对象
print(ren.color)                    # 通过对象调用类的属性
ren.think()                         # 通过对象调用类的方法
```
