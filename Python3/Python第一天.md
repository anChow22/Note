## Python基础(第一天)

*  学习目录   
> * Python的安装
> * Python工具
> *
> *

---
## 0x01 Python的重要性

## 0x02 Python的安装
* Example: Linux
```
# tar xf Python-3.6.14.tgz
# cd Python-3.6.14
# ./configure --ssprefix=/usr/local/python3.6
# make && make install
## 修改yum
vim /usr/bin/yum
#!/usr/bin/python_old2
```

## 0x03 Python工具
* Example: 工具选择
```
sublime text
vim
Pycharm
文本编辑器
```
* Example: Pycharm的破解方法
```
设置python的License server
http://52.221.191.41:1017
http://xidea.online
源程序:
链接:https://pan.baidu.com/s/1kVGKE8n 密码:t3qj
```
* Example: Pycharm设置
```
File -> Settings -> Project test -> ProjectInterpreter   # 设置字体及样式
## 设置python文件抬头
File -> Setting ->Editot -> CodeStyle -> File and Code Templates -> Python Script
## 格式
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-21 10:37
# @Author  : anChow
# @File    : test.py
```
* Example: Pycharm快捷键
```
Ctrl + Z               # 撤销
Ctrl + A               # 全选
Ctrl + C               # 复制
Ctrl + V               # 粘贴
Ctrl + X               # 剪切
Alt + p                # 浏览历史命令(上一条)
Alt + n                # 浏览历史命令(下一条)
Ctrl + F6              # 重启shell,之前定义的对象和导入模块全部失效
F1                     # 打开python帮助文档
Alt + /                # 自动补全曾经出现过的单词
Ctrl + ]               # 缩进代码块
Ctrl + [               # 取消代码块
Alt + 3                # 注释代码快
Alt + 4                # 取消代码块注释
Tab                    # 补全
```
* Example: 导入模块并输出
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-21 23:22
# @Author  : anChow
# @File    : 第一课.py

import sys

name = input("Please input your name:")
print("hello {0}".format(name))
```
* Example: 调试模式
```
# 断电： 程序执行到调试地方进行停下来
F7： 进入到代码
F8:  跳到下一步
F9:  恢复程序或执行下一个断点
```
* Example: 配置上传github
```
settings里面搜索github关键字
Host: github.com
Login: 用户
Password：密码

## 推送
VCS -> Checkout form version Control -> github
## 拉取
```
