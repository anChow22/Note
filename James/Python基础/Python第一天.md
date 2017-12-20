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
