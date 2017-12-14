## Python安装

*  描述
> 环境: CentOS 6 
> 对当前Python版本安装
> 对Ipython安装
--------------------------------------------------------------------------------

* **@Python2**
> 安装Python2.7.13
```
yum install -y openssl-devel readline-devel unzip gcc gcc-c++
wget https://www.python.org/ftp/python/2.7.13/Python-2.7.13.tgz --no-check-certificate
tar xf Python-2.7.13.tgz
cd Python-2.7.13
./configure --prefix=/usr/local/python27
make && make install
/usr/local/python27/bin/python
```


* **Python3**


* **Ipython**
