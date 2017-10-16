---
layout: post
comments: true
author: zq
title: 在 ipynb 中运行 Scheme
description: ~ 大妈笔记,每周不一定
categories: Log
tags: ipynb scheme py3
---

# 如何在 Jupyter 界面中调试 Scheme 代码?

看到视频 [Scheme Debug Demo in Jupyter, now with Inspector \- YouTube](https://www.youtube.com/watch?v=2w-iO701g_w) 太嗯哼了,

当然要切换过去!

只是没想到...



<!--more-->

## 调研
快速 google 并查询了以下关键文章:

- [Calysto/calysto\_scheme: A Scheme kernel for Jupyter that can use Python libraries](https://github.com/Calysto/calysto_scheme)
- [rainyear/A-sketch-of-SICP: SICP in IPython Notebook with Scheme kernel.](https://github.com/rainyear/A-sketch-of-SICP)
- [JupyterでScheme処理系を動かしてSICPを勉強する ｜ Developers.IO](http://dev.classmethod.jp/etc/sicp-study-on-jupyter/)
- [No such kernel named calysto\_scheme · Issue \#6 · Calysto/calysto\_scheme](https://github.com/Calysto/calysto_scheme/issues/6)
- ...


## 嗯哼

- pyenv 中安装 3.6.3/3.4.3
- 然后虚拟化出对应的 scm343/scm363
- 尝试部署 ipyn-jupyter-calysto\_scheme
- 结果, 启动后, 依然没有见到新 kernel ~ `Calysto Scheme 3`
- 再搜索对应的 error: `No such kernel named calysto_scheme`
- 才从官方 Issue 中理解:
    + 这类对于 jupyter 内核的扩展
    + 要有一个明确的新内核挂载的指令!


才嗯哼明白:

- calysto\_scheme 已经稳定, 用 pip 安装没有问题
- calysto\_scheme 已经稳定, 和 py3 版本没有直接关系
- 最最要紧的是, 先安装对应模块, 再加载新 kernel 才能在 juypter 界面中看到...

官方文档最核心的正确的操作,要依次执行:

    pip3 install --upgrade calysto-scheme --user
    python3 -m calysto_scheme install --user

原先以为第二步是相同的作用, 结果, 在第一步成功后, 就没有继续,然后就没有了然后...


# TODO

其实吧, [Calysto Project: Libraries and Languages for Python and Jupyter](http://calysto.github.io/) 也是大神器

- 通过对 Jupyter 的合法扩展, 已经可以支持近10种其它语言来享受 ipynb 的交互
- 所以, 接下来 mma 怎么也在 ipynb 中嗯哼? 虽然这个非常没有必要...


# 用时

- .5h blogging
- 1.h 研究并完成配置






