---
layout: post
comments: true
author: zq
title: Aoi-planetDUer
description: ~ 大妈笔记,每周不一定
categories: Log
tags: scm ubuntu python
---

# Planet 是个好同志

![planet_text](http://www.planetplanet.org/img/planet_text.png)

13年前用过,那时, 代码就已经不更新了...
为什么? 实在是一下子就写到完美了!

<!--more-->

毕竟功能异常单纯, 就是将指定的 RSS 之类聚合数据, 按照日期整理为一页 HTML,

- [Planet Python](http://planetpython.org/)
- [Haskell](http://planet.haskell.org/)
- [Lisp](http://planet.lisp.org/)
- [Perl](http://planet.perl.org/)
- [MySQL](http://www.planetmysql.org/)
- [PostgreSQL](http://planet.postgresql.org/)
- ...

当然的自怼圈也应该有!

## pyenv
~ 第一个要配置的还是 python 环境了

当然的 ubuntu 内置了 python 环境,
但是, 必须第一时间将系统 py 运行时和自己的开发环境有效隔离哪...

参考:

- [pyenv/pyenv: Simple Python version management](https://github.com/pyenv/pyenv#installation)
    + [Troubleshooting / FAQ · pyenv/pyenv Wiki](https://github.com/pyenv/pyenv/wiki)
- [pyenv/pyenv-virtualenv: a pyenv plugin to manage virtualenv (a.k.a. python-virtualenv)](https://github.com/pyenv/pyenv-virtualenv)

进行快速配置就好...


    $ sudo apt install git
    $ cd /opt/repo
    $ git clone https://github.com/pyenv/pyenv.git .pyenv
    $ git clone https://github.com/pyenv/pyenv-virtualenv.git .pyenv/plugins/pyenv-virtualenv

配置`~/.bash_profile`

    ##############################################################################
    #   --> PyEnv
    ##############################################################################
    export PYENV_ROOT="/opt/repo/.pyenv"
    export PATH="$PYENV_ROOT/bin:$PATH"

    eval "$(pyenv init -)"
    #   export PYENV_VIRTUALENV_DISABLE_PROMPT=0
    eval "$(pyenv virtualenv-init -)"

激活加载:

    $ source ~/.bash_profile

安装编译工作用 python 环境:

    # 先得安装一堆编译依赖工具/库
    $ sudo apt install -y make build-essential libssl-dev zlib1g-dev \
        libbz2-dev libreadline-dev libsqlite3-dev \
        wget curl llvm libncurses5-dev xz-utils tk-dev

    $ pyenv install --list
    ...
        可以感叹一下支持的发行版有多丰富

    $ pyenv install 3.6.2
    ...
    $ pyenv install 2.7.13
    ...
    $ pyenv rehash

    $ pyenv virtualenv 2.7.13 2713DAMA
    ...
    You are using pip version 6.1.1, however version 9.0.1 is available.
    You should consider upgrading via the 'pip install --upgrade pip' command.
    ...
    $ pyenv virtualenv 3.6.2 362CV3

    $ pyenv rehash

    $ pyenv versions
    * system (set by /opt/repo/.pyenv/version)
      2.7.13
      2.7.13/envs/2713DAMA
      2713DAMA
      3.6.2
      3.6.2/envs/362CV3
      362CV3

实际使用情景:

    zoomq @ aoi in ~
    $ cd /opt
    zoomq @ aoi in /opt on default

    $ pyenv 2712DAMA 

    (2712DAMA)
    zoomq @ aoi in /opt on default
    $ cd app

    (2712DAMA)
    zoomq @ aoi in /opt/app on default
    $ python
    Python 2.7.12 (default, Nov 19 2016, 06:48:10)
    [GCC 5.4.0 20160609] on linux2
    Type "help", "copyright", "credits" or "license" for more information.
    >>>

    zoomq @ aoi in /opt/app on default
    $ cd ../log

    zoomq @ aoi in /opt/log on default
    $ pyenv local 362CV3

    (362CV3)
    zoomq @ aoi in /opt/app on default
    $ python
    Python 3.6.2 (default, Aug 17 2017, 23:28:25)
    [GCC 5.4.0 20160609] on linux
    Type "help", "copyright", "credits" or
    >>>


## 部署 planet
~ 情况并没有想象的那么简单...


毕竟是有快10年没有更新的工程了, 使用配置方式没有变,
快速根据模板完成了配置, 一运行:


    $ python code/planet.py config/du.ini
    Traceback (most recent call last):
      File "code/planet.py", line 24, in <module>
        import planet
      File "/opt/www/planet/code/planet/__init__.py", line 35, in <module>
        import dbhash
      File "/opt/repo/.pyenv/versions/2.7.13/lib/python2.7/dbhash.py", line 7, in <module>
        import bsddb
      File "/opt/repo/.pyenv/versions/2.7.13/lib/python2.7/bsddb/__init__.py", line 67, in <module>
        import _bsddb
    ImportError: No module named _bsddb


嗯哼, 这事儿听说过,因为版权的问题, 从2.5版本后, 将 bsddb 从内置模块中移除了,
所以...

- [python \- "ImportError: No module named \_bsddb" when opening shelve in Docker container \- Stack Overflow](https://stackoverflow.com/questions/28253731/importerror-no-module-named-bsddb-when-opening-shelve-in-docker-container)
- [osx \- Installing bsddb package \- python \- Stack Overflow](https://stackoverflow.com/questions/16003224/installing-bsddb-package-python)
- [Hacking OS X’s Python dbhash and bsddb modules to work \| Marc Abramowitz](http://marc-abramowitz.com/archives/2007/11/28/hacking-os-xs-python-dbhash-and-bsddb-modules-to-work/)
- [bsddb3 6\.2\.4 : Python Package Index](https://pypi.python.org/pypi/bsddb3/6.2.4)
- ...

当然,有很多方式可以弥补, 最简单的:

    $ pip install bsddb3
    Collecting bsddb3
      Using cached bsddb3-6.2.4.tar.gz
        Complete output from command python setup.py egg_info:
        Can't find a local Berkeley DB installation.
        (suggestion: try the --berkeley-db=/path/to/bsddb option)

        ----------------------------------------
    Command "python setup.py egg_info" failed with error code 1 in /tmp/pip-build-ST2bF0/bsddb3/


> /path/to/bsddb

有独立的 bsddb 产品?

- [Berkeley DB\-6\.2\.23](http://www.linuxfromscratch.org/blfs/view/stable/server/db.html)
- [Python "bindings" for Oracle Berkeley DB](https://www.jcea.es/programacion/pybsddb.htm)
- 好吧, 忒复杂了...

于是选择相信 Ubuntu 的软件仓库:

    $ apt search bsddb
    Sorting... Done
    Full Text Search... Done
    python-bsddb3/xenial,now 6.1.0-1build2 amd64 [installed]
      Python interface for Berkeley DB

    python-bsddb3-dbg/xenial 6.1.0-1build2 amd64
      Python interface for Berkeley DB (debug extension)

    python-bsddb3-doc/xenial,xenial 6.1.0-1build2 all
      Documentation for the python Berkeley DB interface module

    python3-bsddb3/xenial 6.1.0-1build2 amd64
      Python interface for Berkeley DB (Python 3.x)

    python3-bsddb3-dbg/xenial 6.1.0-1build2 amd64
      Python interface for Berkeley DB (debug extension, Python 3.x)


那就简单了:

    $ sudo apt install python-bsddb3
    $ pip list
    adium-theme-ubuntu (0.3.4)
    bsddb3 (6.1.0)
    mercurial (3.7.3)
    pip (8.1.1)
    setuptools (20.7.0)
    unity-lens-photos (1.0)
    wheel (0.29.0)

    $ python
    Python 2.7.12 (default, Nov 19 2016, 06:48:10)
    [GCC 5.4.0 20160609] on linux2
    Type "help", "copyright", "credits" or "license" for more information.
    >>> import bsddb3
    >>> dir(bsddb3)
    ['MutableMapping', '_DBWithCursor', '_DeadlockWrap', '__builtins__', '__doc__', '__file__', '__name__', '__package__', '__path__', '__version__', '_checkflag', '_db', '_iter_mixin', '_openDBEnv', '_pybsddb', 'absolute_import', 'btopen', 'collections', 'db', 'dbutils', 'error', 'hashopen', 'os', 'ref', 'rnopen', 'sys']
    >>>


### in pyenv ?
只是比较尴尬的, 这样一来, 只能使用系统 python 2.7.12

之前通过 pyenv 安装的 2.7.14/3.6.2 什么的都无法正常驱动 planet 了...

    $ python code/planet.py config/du.ini
    DEBUG:planet.runner:Socket timeout set to 20 seconds
    INFO:planet.runner:Loading cached data
    INFO:planet:Updating feed <http://du.zoomquiet.io/atom.xml>
    DEBUG:planet:Last Modified: 2017-08-21T10:00:52+00:00
    DEBUG:planet:Items in Feed: 12
    ...
    INFO:planet.runner:Processing template config/index.html.tmpl
    INFO:planet.runner:Writing docs/index.html
    INFO:planet.runner:Processing template config/atom.xml.tmpl
    INFO:planet.runner:Writing docs/atom.xml
    INFO:planet.runner:Processing template config/rss20.xml.tmpl
    INFO:planet.runner:Writing docs/rss20.xml
    INFO:planet.runner:Processing template config/rss10.xml.tmpl
    INFO:planet.runner:Writing docs/rss10.xml
    INFO:planet.runner:Processing template config/opml.xml.tmpl
    INFO:planet.runner:Writing docs/opml.xml
    INFO:planet.runner:Processing template config/foafroll.xml.tmpl
    INFO:planet.runner:Writing docs/foafroll.xml

不过, 没关系先用起来再说 `(￣▽￣)`

好在也额外的学到从 shell 脚本中调用 pyenv 环境的技巧:

- [Is there a preferred way to use pyenv in a shell script? · Issue \#492 · pyenv/pyenv](https://github.com/pyenv/pyenv/issues/492)
- pyenv 原作者的分享:
    + Both PYENV_VERSION and pyenv shell should work even in shell scripts. Latter requires you to add eval "$(pyenv init -)" in your script, though.
    + Personally I like to use PYENV_VERSION since it doesn't require additional shell setup....

e.g:

    #!/bin/bash
    # Set version to 2.7.10
    export PYENV_VERSION=2.7.10

    # DO STUFF
    # python --version # ==> Python 2.7.10

    # Reset version
    unset PYENV_VERSION

> 直接使用环境变量来切换就对了

# 用时

- .5h install pyenv
- 1.5h 各种 py 环境安装/镜像
- 1.h _bsddb_ 问题研究
- .5h 完成 planet 工作驱动


