---
layout: post
comments: true
author: leilayanhui
title: 用 ShareX qiniu 一键截图上传
description: 
categories: Log
tags: sharex qiniu
---

# 用 ShareX qiniu 一键截图上传
[sharex](https://getsharex.com/) 是一个截屏工具

[qiniu](https://portal.qiniu.com/) 七牛云

以七牛云作图床，截屏后自动上传图片，获得外链地址

<!--more-->


环境：
- win10
- python 3.6.0

## 看图配置 sharex
![sharex_upload_setting](http://osloqpukl.bkt.clouddn.com/201717051546-t.png)

打开 shareX -> 目的地 -> 目的地设置 -> 自定义上传（最底下）

图片来源：[ShareX使用七牛文件上传 东方星痕](http://ystyle.top/2017/07/05/share-the-use-of-qiniu-file-upload/)
### 上传者
填入 qiniu，点击添加
### 请求 URL
进入自己的「对象存储」-> 空间设置 -> 存储区域，查看自己所在地区。根据 [存储区域 - 七牛开发者中心](https://developer.qiniu.com/kodo/manual/1671/region-endpoint) 选择自己的地址，我是华南，填入 `http://up-z2.qiniup.com`
### URL（右侧靠下）
自己的外链默认域名 + `$json:key$` -> `xxxxx.bkt.clouddn.com/$json:key$`
### 生成 token
根据[上传凭证](https://developer.qiniu.com/kodo/manual/1208/upload-token) 建议使用七牛的 SDK。从示例中选择自己的语言，我用的 python，进入 [qiniu/python-sdk: Qiniu Resource (Cloud) Storage SDK for Python](https://github.com/qiniu/python-sdk)，克隆本地后安装

    $ (选择一个文件夹)
    $ git clone https://github.com/qiniu/python-sdk.git
    $ cd python-sdk
    $ pip install qiniu

再根据 [Python SDK_生成上传 token](https://developer.qiniu.com/kodo/sdk/1242/python#token) 拷贝代码，复制到本地，修改相应的 key

    $ cd python-sdk
    $ touch generate_token.py  # 文件名可另取
    $ atom generate_token.py   # 编辑该文件

`access_key = ''`, `secret_key = ''`，进入七牛 -> 个人中心 -> 密钥管理，复制自己的 AccessKey and SecretKey，填入

`bucket_name = ''` 为自己创建的 bucket 存储空间名，如 `bucket_name = 'photo'`，不是 URL

`key = ''`，我设置为 `key = None`

保存文件回终端，运行脚本 `python generate_token.py`，即可获得 token

### 参数
在「参数」下有两个输入空框

左框 | 右框
---|---
token | 上部生成的 token
key | %yy%d%h%mi%s.png
file | $input$

分别输入后点击添加

key 为上传时用的文件名，`%yy%d%h%mi%s.png` 是指年月日小时分钟秒，如  `20180213165812.png`

### 测试
都配置完后，点击左侧「图片上传」-「测试」，若测试结果返回一个正常的连接地址那就是配置成功了。

最后，**sharex -> 目的地 -> 图片上传 -> 自定义图像上传**

**截图后的动作 -> 上传图片**

### 参考
- [ShareX使用七牛文件上传 东方星痕](http://ystyle.top/2017/07/05/share-the-use-of-qiniu-file-upload/)
- [配合使用ShaseX与七牛云 松风起兮](http://day.liuxuan.net/2017/11/use_sharex_with_qiniu/)
- [七牛返回 key doesn't match with scope问题出在哪？](https://segmentfault.com/q/1010000010508965)

### Change-Log
- 查资料，尝试 3h
- 笔记 .7h
