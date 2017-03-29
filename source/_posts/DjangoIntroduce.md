---
title: Django 教程
date: 2017-03-29 17:12:34
toc: true
tags:
- 服务器
- 开发学习
- 编程语言
categories:
- Django
---

Python下有许多款不同的 Web 框架。Django是重量级选手中最有代表性的一位。许多成功的网站和APP都基于Django。
Django是一个开放源代码的Web应用框架，由Python写成。
Django遵守BSD版权，初次发布于2005年7月, 并于2008年9月发布了第一个正式版本1.0 。
Django采用了MVC的软件设计模式，即模型M，视图V和控制器C。

<!----more---->

内容来源：http://www.runoob.com/django/django-tutorial.html    

# 1. Digngo教程    
## 1.1 谁适合阅读本教程？  
本教程适合有Python基础的开发者学习。    

## 1.2 学习本教程前你需要了解  
学习本教程前你需要了解一些基础的 Web 知识及 [Python 2.x 基础教程](http://www.runoob.com/python/python-tutorial.html) 或 [Python 3.x 基础教程](http://www.runoob.com/python3/python3-tutorial.html)。   

Django 版本对应的 Python 版本：

| Diango版本  | Python版本                |
| --------- | ----------------------- |
| 1.8       | 2.7, 3.2, 3.3, 3.4, 3.5 |
| 1.9, 1.10 | 2.7, 3.4, 3.5           |
| 1.11      | 2.7, 3.4, 3.5, 3.6      |
| 2.0       | 3.5+                    |

# 2. Diango安装  

在安装 Django 前，系统需要已经安装了Python的开发环境。接下来我们来具体看下不同系统下Django的安装。

## 2.1 Window 下安装 Django

如果你还未安装Python环境需要先下载Python安装包。

1、Python 下载地址：[https://www.python.org/downloads/](https://www.python.org/downloads/)

2、Django 下载地址：[https://www.djangoproject.com/download/](https://www.djangoproject.com/download/)

**注意：**目前Django 1.6.x以上版本已经完全兼容Python 3.x。

### 2.1.1 Python 安装(已安装的可跳过)

安装Python你只需要下载python-x.x.x.msi文件，然后一直点击"Next"按钮即可。

![](install1.png)

安装完成后你需要设置Python环境变量。 右击计算机->属性->高级->环境变量->修改系统变量path，添加Python安装地址，本文实例使用的是C:\Python33，你需要根据你实际情况来安装。

![](install2.png)

### 2.1.2 Django安装

下载 Django 压缩包，解压并和Python安装目录放在同一个根目录，进入 Django 目录，执行python setup.py install，然后开始安装，Django将要被安装到Python的Lib下site-packages。

![](install3.jpg)

然后是配置环境变量，将这几个目录添加到系统环境变量中： C:\Python33\Lib\site-packages\django;C:\Python33\Scripts。 添加完成后就可以使用Django的django-admin.py命令新建工程了。

![](install4.jpg)

### 2.1.3 检查是否安装成功

输入以下命令进行检查:

```
>>> import django
>>> print django.get_version()
```

![](install5.jpg)

如果输出了Django的版本号说明安装正确。

## 2.2 Linux上安装Django

### 2.2.1 yum 安装方法

以下安装位于 Centos Linux 环境下安装，如果是你的 Linux 系统是 ubuntu 请使用 apt-get 命令。

默认情况下 Linux 环境已经支持了Python。你可以在终端输入Python命令来查看是否已经安装。

```
Python 2.7.3 (default, Aug  1 2012, 05:14:39) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 
```

#### 安装setuptool

命令

```
yum install setuptool
```

完成之后，就可以使用 easy_install 命令安装 django

```
easy_install django
```

之后我们在python解释器输入以下代码：

```
[root@localhost django]# python
Python 2.7.5 (default, Nov 20 2015, 02:00:19)
[GCC 4.8.5 20150623 (Red Hat 4.8.5-4)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import django
>>> django.VERSION
(1, 11, 0, u'rc', 1)
>>>
```

我们可以看到输出了Django的版本号，说明安装成功。

### 2.2.2 pip命令安装方法

```
pip install Django
```

如果pip < 1.4, 安装方法如下：
```
pip install https://www.djangoproject.com/download/1.11a1/tarball/
```

### 2.2.3 源码安装方法
下载源码包：https://www.djangoproject.com/download/
输入以下命令并安装：

```
tar xzvf Django-X.Y.tar.gz    # 解压下载包
cd Django-X.Y                 # 进入 Django 目录
python setup.py install       # 执行安装命令
```

安装成功后 Django 位于 Python 安装目录的 site-packages 目录下。

## 2.3 Mac下安装

### 2.3.1 下载
从[这里](https://www.djangoproject.com/download/)下载最新的稳定版本：DJango-1.x.y.tar.gz，在页面右侧列表下载，如下图：
![](1.jpg)
记住是最新的官方版本哦.其中x.y是版本号。进入你下载该文件的文件夹目录，执行如下命令:（Mac下默认是/Users/xxx/Downloads，xxx是你的用户名）

```
$ tar zxvf Django-1.x.y.tar.gz
```

你也可以从 Github 上下载最新版，地址：https://github.com/django/django：

```
git clone https://github.com/django/django.git
```

### 2.3.2 安装
进入解压后的目录：

```
cd Django-1.x.y
sudo python setup.py install
```

安装成功后会输出以下信息：

```
……
Processing dependencies for Django==1.x.y
Finished processing dependencies for Django==1.x.y
```

再进入我们的站点目录，创建 Django 项目：

```
$ django-admin.py startproject testdj
```

启动服务：

```
$ cd testdj # 切换到我们创建的项目
$ python manage.py runserver
……
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
```

以上信息说明，项目已启动，访问地址为http://127.0.0.1:8000/。

# 3. Diango创建第一个项目  

本章我们将介绍Django 管理工具及如何使用 Django 来创建项目，第一个项目我们以 HelloWorld 来命令项目。
测试版本说明：
* Python 2.7.5
* Django 1.11.0

## 3.1 Django管理工具

安装 Django 之后，您现在应该已经有了可用的管理工具 django-admin.py。我们可以使用 django-admin.py 来创建一个项目:
我们可以来看下django-admin.py的命令介绍:
```
[root@localhost ~]# django-admin.py

Type 'django-admin.py help <subcommand>' for help on a specific subcommand.

Available subcommands:

[django]
    check
    compilemessages
    createcachetable
    dbshell
    diffsettings
    dumpdata
    flush
    inspectdb
    loaddata
    makemessages
    makemigrations
    migrate
    runserver
    sendtestemail
    shell
    showmigrations
    sqlflush
    sqlmigrate
    sqlsequencereset
    squashmigrations
    startapp
    startproject
    test
    testserver
Note that only Django core commands are listed as settings are not properly configured (error: Requested setting INSTALLED_APPS, but settings are not configured. You must either define the environment variable DJANGO_SETTINGS_MODULE or call settings.configure() before accessing settings.).
```

## 3.2 创建第一个项目

使用 django-admin.py 来创建 HelloWorld 项目：

```
django-admin.py startproject HelloWorld
```

创建完成后我们可以查看下项目的目录结构：

```
[root@localhost ~]# cd HelloWorld
[root@localhost HelloWorld]# tree
.
├── HelloWorld
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
└── manage.py

1 directory, 5 files
```

目录说明：
* HelloWorld: 项目的容器。
* manage.py: 一个实用的命令行工具，可让你以各种方式与该 Django 项目进行交互。
* HelloWorld/__init__.py: 一个空文件，告诉 Python 该目录是一个 Python 包。
* HelloWorld/settings.py: 该 Django 项目的设置/配置。
* HelloWorld/urls.py: 该 Django 项目的 URL 声明; 一份由 Django 驱动的网站"目录"。
* HelloWorld/wsgi.py: 一个 WSGI 兼容的 Web 服务器的入口，以便运行你的项目。
接下来我们进入 HelloWorld 目录输入以下命令，启动服务器：

```
python manage.py runserver 0.0.0.0:8000
```

0.0.0.0 让其它电脑可连接到开发服务器，8000 为端口号。如果不说明，那么端口号默认为 8000。
在浏览器输入你服务器的ip及端口号，如果正常启动，输出结果如下：
![](2.jpg)

## 3.3 视图和URL配置


# 4. Diango模板  
# 5. Diango模型  
# 6. Diango表单  
# 7. Diango Admin管理工具  
# 8. Diango Nginx+uwsgi安装配置  