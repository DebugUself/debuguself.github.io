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


