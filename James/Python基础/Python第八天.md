## Python基础(第八天)

*  学习目录  
> * 使用for循环遍历文件
> * 使用while循环遍历文件

---
## 0x01 for
> * 循环  
> * for 循环  

* 循环
  -- 一个结构，导致程序要重复一定次数  
  -- 条件循环也如此， 条件为假，循环结束

* for 循环
  -- 序列里，for循环遍历

* range() 方法  
   -- 快速生成系列  
   -- range(起始位置， 结束为止， 步长)  
      --- 创建对象为`整数`    
      --- 起始位置，不选默认为`0`  
      --- 结束位置，不包括在范围内  
      --- 步长默认为`1`  

* xrange() 方法  
  -- 生成迭代对象  
  -- 不占用内存资源  
  -- 不会直接返回值  
  -- 通过for循环遍历输出值  

* 迭代遍历  
   -- 遍历序列： 将序列中各个元素取出  
       --- 直接从序列取值  
       --- 通过索引取值  
PS:  
   `迭代` 指重复执行一个指令  

* for ... else  
  -- for循环如果正常结束， 才会执行else语句  

  > * 语法格式
  ```
  for iterationg_var in sequence:
      statement(s)
  ```

  * Example: for循环打印字符串
  ```
  In [281]: a = 'abc'

  In [282]: for i in a:
       ...:     print(i)  
  a
  b
  c
  ```
  * Example: range()生成一组序列
  ```
  In [283]: range(10)               # 生成0 - 9序列
  Out[283]: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
  In [284]: help(range)             # 获取帮助
  range(start, stop[, step]) -> list of integers  # range(起始位置, 结束位置, 步长)

  In [285]: for i in range(10):     # 生成0 - 9序列, 并输出
       ...:     print(i)

  In [286]: for i in range(10, 100, 5):   # 打印10 - 99步长为5的数
      ...:     print(i)
  ```
  * Example: 打印偶数
  ```
  #!/usr/bin/env python
  # -*- coding: utf-8 -*-
  # @Time    : 2017-12-20 22:37
  # @Author  : anChow
  # @File    : test.py

  for i in range(1, 11):
      if i % 2 == 0:                # 取余数    
          print(i)
  ```
  * Example: 列表推导
  ```
  In [288]: print([ i for i in range(1, 11)])    # 把循环出的书放入列表
  [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

  In [289]: print([ i for i in range(1, 11) if i % 2 == 0])  # 取余
  [2, 4, 6, 8, 10]

  In [290]: print([ i**2 for i in range(1, 11)])  # i的乘方
  [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
  ```
  * Example: 求和
  ```
  #!/usr/bin/env python
  # -*- coding: utf-8 -*-
  # @Time    : 2017-12-20 22:37
  # @Author  : anChow
  # @File    : test.py

  sum = 0
  for i in range(1, 101):
      sum += i
  print(sum)
  ```
  * Example: xrange() 方法
  ```
  Out[291]: xrange(10)
  In [292]: a = xrange(10)
  In [295]: for i in a:
       ...:     print(i)
  In [296]: help(xrange)     
  ```
  * Example: for循环遍历字典
  ```
  In [297]: dic = {'name': 'Chow', 'age': 26}    # 定义字典
  In [298]: dic.fromkeys('abcde', 100)           # 定义字典
  Out[298]: {'a': 100, 'b': 100, 'c': 100, 'd': 100, 'e': 100}
  In [299]: for k in dic:                        # 遍历字典keys
       ...:     print(k)
  In [300]: for k in dic:                        
      ...:     print(k, dic[k])                  # 输出keys value

  In [303]: for k in dic:
      ...:     print('%s ---> %s' % (k, dic[k])) # 格式化输出keys及value
  In [304]: dic.items()                          # 调用字典items() 方法输出
  Out[304]: [('age', 26), ('name', 'Chow')]   

  In [307]: for i in dic.items():print(i)        # 通过items() 方法获取元组
  ('age', 26)
  ('name', 'Chow')

  In [308]: for k, v in dic.items():print(k, v)  # 通过k v接收值
  ('age', 26)
  ('name', 'Chow')

  In [309]: for k, v in dic.iteritems():print(k, v)  # 通过k v接收值
  ('age', 26)
  ('name', 'Chow')
  ```
  * Example: 循环打印乘法口诀
  ```
  #!/usr/bin/env python
  # -*- coding: utf-8 -*-
  # @Time    : 2017-12-20 22:37
  # @Author  : anChow
  # @File    : test.py

  for i in xrange(1, 10):
      for j in xrange(1, i+1):
          print('%s x %s = %s' % (j, i, j*i)),
      print
  ```
  * Example: 循环打印序列
  ```
  #!/usr/bin/env python
  # -*- coding: utf-8 -*-
  # @Time    : 2017-12-20 22:37
  # @Author  : anChow
  # @File    : test.py

  import time

  for i in xrange(10):
      print(i)
      time.sleep(1)                    # 休眠1秒
  else:                                # 当序列被遍历完, 才执行
      print('main end')
  ```
  * Example: 循环打印序列，break跳出所有循环
  ```
  #!/usr/bin/env python
  # -*- coding: utf-8 -*-
  # @Time    : 2017-12-20 22:37
  # @Author  : anChow
  # @File    : test.py

  import time

  for i in xrange(10):
      print(i)
      if i == 5:                       # 当 i 等于 5 时
          break                        # 跳出所有循环
  else:
      print('main end')
  ```
  * Example: 循环打印序列，continue跳出本层循环
  ```
  #!/usr/bin/env python
  # -*- coding: utf-8 -*-
  # @Time    : 2017-12-20 22:37
  # @Author  : anChow
  # @File    : test.py

  import sys
  import time

  for i in xrange(10):
      print(i)
      if i == 3:
          continue                     # 跳出本层循环
      elif i == 5:                     # 当 i 等于 5 时
          break                        # 跳出所有循环
      elif i == 6:                     # 当 i 等于 6 时
          pass                         # 占位， 什么都不做
      elif i == 7:                     # 当 i 等于 7 时
          sys.exit()                    # 调用sys模块的exit() 方法退出
      print(i)
  else:
      print('main end')
  print('Hello Python')    
  ```
  * Example: 猜数字游戏(存在问题)
  ```
  """
  1、系统生成一个20以内的随机整数
  2、玩家有6次机会进行猜猜看， 每次猜测都有反馈(猜大了， 猜小了， 猜对了， 结束)
  3、6次中， 猜对了， 玩家赢了
  4、否则系统赢了
  """
  #!/usr/bin/env python
  # -*- coding: utf-8 -*-
  # @Time    : 2017-12-26 10:37
  # @Author  : anChow
  # @File    : test.py

  import random

  num = random.randint(0,20)
  prt = int(raw_input("输入你猜的数值为："))

  i = 0
  while i < 6:
      if prt > num:
          print("猜大了")
          i += 1
      elif prt < num:
          print("猜小了")
          continue
      elif prt == num:
          print("猜对了")
          continue
      else:
          print("结束")
          break
  ```
