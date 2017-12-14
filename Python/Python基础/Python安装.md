## Python安装

*  描述
> 环境: CentOS 6   
> CentOS 基础 (yum源及时钟同步配置)   
> Python 安装  
> Setuptools安装  
> pip 安装  
> Virtualenv 安装  
> Ipython 安装
--------------------------------------------------------------------------------

* CentOS基础
```
> ## yum源配置
# echo $LANG
# yum install -y wget
# mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
# wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-6.repo
# yum makecache
## 时钟同步配置
# cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
# yum install -y ntpdate
# date
# ntpdate -s time.windows.com
```
* **@Python2**
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
* **Python3**
> 安装Python3.6.3
```
# yum install -y openssl-devel readline-devel unzip gcc gcc-c++
# wget https://www.python.org/ftp/python/3.6.3/Python-3.6.3.tgz --no-check-certificate
# tar xf Python-3.6.3.tgz
# cd Python-3.6.3
# ./configure --prefix=/usr/local/python36
# make && make install
# /usr/local/python36/bin/python
```
* **Setuptools安装**
```
# wget https://pypi.python.org/packages/dc/8c/7c9869454bdc53e72fb87ace63eac39336879eef6f2bf96e946edbf03e90/setuptools-33.1.1.zip#md5=7963d41d97b94e450e3f8a217be06ffe
# unzip setuptools-33.1.1.zip
# cd setuptools-33.1.1
# /usr/local/python27/bin/python setup.py install
```
* **pip 安装**
```
## 配置豆瓣源
# vi /etc/pip.conf    
[global]  
trusted-host = pypi.douban.com
index-url = http://pypi.douban.com/simple

[list]                   # 警告配置
format=columns

## pip安装
# /usr/local/python27/bin/easy_install pip
# /usr/local/python27/bin/pip list  # 若不配置安装源， 会出现警告
```
* **Virtualenv安装**
> 若不需要使用Django开发， 则可以不用安装
```
# /usr/local/python27/bin/pip install virtualenv
# mkdir /data
# cd /data
# /usr/local/python27/bin/virtualenv ./python27env
# source /data/python27env/bin/activate
pip list
```
* **Ipython**
```
# pip install ipython
http://www.itnpc.com/news/web/1470750628101654.html
https://www.cnblogs.com/zhaojiedi1992/p/zhaojiedi_python_001.html
http://blog.csdn.net/dahaiyudong/article/details/71737174
```
