title: python的pip修改默认源
author: felix1982
tags:
  - pip
categories:
  - python
date: 2018-12-27 08:28:00
---
一、在windows环境下修改pip镜像源的方法(以python3.5为例)

(1):在windows文件管理器中,输入 %APPDATA%

(2):会定位到一个新的目录下，在该目录下新建pip文件夹，然后到pip文件夹里面去新建个pip.ini文件

(3):在新建的pip.ini文件中输入以下内容，搞定
~~~
[global]
timeout = 6000
index-url = http://pypi.douban.com/simple
trusted-host = pypi.douban.com
~~~


二、在linux系统中更新pip源的方式(以centos,python2.7为例)

在linux环境下的修改方式和在windows环境下修改方式基本相同，这里简单总结一下:

(1):在用户的家目录下面创建名为.pip文件夹

(2):在创建好的.pip文件夹中创建名为pip.conf的文件

(3):在pip.conf文件中输入以下内容，ok!!!

~~~
[global]
timeout = 6000
index-url = http://pypi.douban.com/simple
trusted-host = pypi.douban.com
~~~