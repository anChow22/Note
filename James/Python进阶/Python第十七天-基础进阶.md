## Python基础(第十七天)

*  学习目录  
> * rc脚本(类的定义与脚本结构)  
> * rc脚本(start方法)  
> * rc脚本(stop和status方法)  
> * rc脚本(以daemon方式启动)  

---
## 0x01  rc脚本(类的定义与脚本结构)
> 启动脚本主体框架
> start启动方法
> stop和status方法
> restart方法实现


* Example: 启动memcached程序脚本主体框架结构
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-18 10:37
# @Author  : anChow
# @File    : rc启动脚本.py

import sys

class Process(object):
    """ memcached rc script """
    def __init__(self, name, program, args, workdir):
        self.name = name
        self.program = program
        self.args = args
        self.workdir = workdir

    def __init(self):


    def start(self):



    def stop(self):


    def restart(self):
        self.stop()
        self.start()

    def status(self):


    def help(self):


def main():
    name = 'memcached'
    prog = '/usr/bin/memcached'
    args = '-u nobody -p 11211 -c 1024 -m 64'
    wd = '/var/tmp/memcached'
    pm = Process(name = name,
                 program = prog,
                 args = args,
                 workdir = wd)
    try:
        cmd = sys.argv[1]
    except IndexError, e:
        print("Option Error")
        sys.exit()

    if cmd == 'start':
        pm.start()
    elif cmd == 'stop':
        pm.stop()
    elif cmd == 'restart':
        pm.restart()
    elif cmd == 'status':
        pm.status()
    else:
        pm.help()

if __name__ == '__main__':
    main()
```

## 0x02 rc脚本(start方法)  
> _pidFile()  
> _writhPid()   
> start()  

* Example: start()启动方法  
```
def _pidFile(self):         ## 获取PID
    """" /var/tmp/memcached/memcached.pid """"
    return os.path.join(self.workdir, "%s.pid" %self.name)

def _writhPid(self):        ## 把PID写入文件
    if self.pid:
        with open(self._pidFile(), 'w') as fd:
            fd.write(str(self.pid))

def start(self):            ## 启动程序
    self._init()
    cmd = self.program + ' ' + self.args
    p = Popen(cmd, stdout=PIPE, shell=True)
    self.pid = p.pid
    self._writhPid()
    print("%s start Sucessful" %self.name)
```

## 0x03 rc脚本(stop和status方法)
> _getPid获取进程PID
> stop停止服务
> status查看状态

* Example: 停止服务和查看服务状态
```
def _getPid(self):
    p = Popen(['pidof', self.name], stdout=PIPE)
    pid = p.stdout.read().strip()
    return pid

def stop(self):
    pid = self._getPid()
    if pid:
        os.kill(int(pid), 15)
        if os.path.exists(_self._pidFile()):
            os.remove(self._pidFile())
            print("%s is stopped" %self.name)

def status(self):
    pid = self._getPid()
    if pid:
        print("%s is already running" % self.name)
    else:
        print("%s is not running" % self.name)
```


## 0x04 rc脚本(以daemon方式启动)
> daemon方式
>

* Example: 完整脚本
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time    : 2018-1-18 10:37
# @Author  : anChow
# @File    : rc启动脚本.py

import sys
import os
from subprocess import Popen, PIPE

class Process(object):
    """ memcached rc script """
    args = {'USER': 'memcached',
            'PORT': '11211',
            'MAXCONN': 1024,
            'CACHESIZE': 64,
            'OPTIONS': ''}
    def __init__(self, name, program, workdir):
        self.name = name
        self.program = program
        self.workdir = workdir

    def _init(self):     ## 判断目录是否存在，不存在则创建目录并进入目录
        """ /var/tmp/memcached """
        if not os.path.exists(self.workdir):
            os.mkdir(self.workdir)
            os.chdir(self.workdir)

    def _pidFile(self):
        """ /var/tmp/memcached/memcached.pid """
        return os.path.join(self.workdir, "%s.pid" %self.name)

    def _writhPid(self):
        if self.pid:
            with open(self._pidFile(), 'w') as fd:
                fd.write(str(self.pid))

    def _readConf(self, f):
        with open(f) as fd:
            lines = fd.reads()
            return dict([i.strip().replace('"','').split('=') for i in lines])

    def _parseArgs(self):
        conf = self._readConf('/etc/sysconfig/memcached')
        if 'USER' in conf:
            self.args['USER'] = conf['USER']
        if 'PORT' in conf:
            self.args['PORT'] = conf['PORT']
        if 'MAXCONN' in conf:
            self.args['MAXCONN'] = conf['MAXCONN']
        if 'CACHESIZE' in conf:
            self.args['CACHESIZE'] = conf['CACHESIZE']
        options = ['-u', self.args['USER'],
                    '-p', self.args['PORT'],
                    '-m', self.args['CACHESIZE'],
                    '-c', self.args['MAXCONN']]
        return options

    def start(self):
        ## 判断PID是否存在
        pid = self._getPid()
        if pid:
            print("%s is running..." % self.name)
            sys.exit()
        self._init()
        cmd = [ self.program ] + self._parseArgs() + ['-d', '-P', self._pidFile()]
        print(cmd)
        p = Popen(cmd, stdout=PIPE)
        self.pid = p.pid
        self._writhPid()
        print("%s start Sucessful" %self.name)

    def _getPid(self):
        p = Popen(['pidof', self.name], stdout=PIPE)
        pid = p.stdout.read().strip()
        return pid

    def stop(self):
        pid = self._getPid()
        if pid:
            os.kill(int(pid), 15)
            if os.path.exists(self._pidFile()):
                os.remove(self._pidFile())
                print("%s is stopped" %self.name)

    def restart(self):
        self.stop()
        self.start()

    def status(self):
        pid = self._getPid()
        if pid:
            print("%s is already running" % self.name)
        else:
            print("%s is not running" % self.name)

    def help(self):
        print("Usage: %s {start|stop|status|restart}" % __file__)

def main():
    ## 定义变量
    name = 'memcached'
    prog = '/usr/bin/memcached'
    wd = '/var/tmp/memcached'
    ## 变量传参
    pm = Process(name = name,
                 program = prog,
                 workdir = wd)
    ##
    try:
        cmd = sys.argv[1]
    except IndexError, e:
        print("Option Error")
        sys.exit()

    ## 判断启动服务方式
    if cmd == 'start':
        pm.start()
    elif cmd == 'stop':
        pm.stop()
    elif cmd == 'restart':
        pm.restart()
    elif cmd == 'status':
        pm.status()
    else:
        pm.help()

## 调用主体函数执行
if __name__ == '__main__':
    main()
```
