---
layout: post
comments: true
author: zq
title: Aoi-无线网络固定 ip
description: ~ 大妈笔记,每周不一定
categories: Log
tags: scm ubuntu wifi
---

# 如何在 wifi 连接下固定 IP 地址?

作为家庭内网服务器的工控机, 预安装的是 Ubuntu,
很好的默认支持了 wifi.

问题在, 默认的连接是用 `DHIP` ~ 即每次重启时, 可能 ip 地址不同.

这令从远程 SSH 连接来工作, 非常不方便....

怎么嗯哼呢?!


<!--more-->

## 调研
快速 google 并查询了以下关键文章:

- [使用固定 IP 地址创建连接](https://help.ubuntu.com/stable/ubuntu-help/net-fixed-ip-address.html)
- [How to Set Static IP Address on Ubuntu 13.04 (both Wireless & Wired) | UbuntuHandbook](http://ubuntuhandbook.org/index.php/2013/07/set-static-ip-address-ubuntu-13-04/)
- [networking - Setting up Static IP Address for Wireless in Ubuntu 14.04 - Ask Ubuntu](https://askubuntu.com/questions/729200/setting-up-static-ip-address-for-wireless-in-ubuntu-14-04)
- [wireless - Setting a Static Ip on Ubuntu - Ask Ubuntu](https://askubuntu.com/questions/530522/setting-a-static-ip-on-ubuntu)
- ...


## 嗯哼

根据其中使用图形网络控制界面中的提示, 完成了配置,并成功固定了 IP 地址,
这样, 在本地的 `~/.ssh/config` 中就可以固定远程主机的配置, 随时用 ssh 进入来操作了.

关键点:

- address: 192.168.1.200
- netmask: 255.255.255.0
- gateway: 192.168.1.1
- dns-nameservers: 8.8.8.8,8.8.4.4,192.168.1.1


# TODO

其实吧, 通过神器: [ngrok - secure introspectable tunnels to localhost](https://ngrok.com/) 可以快速将内网应用发布到外网;

- 但是, 更加嗯哼的是通过路由器的配置将指定主机暴露到外部, 
- 这时, 内网主机的外部地址是什么, 又是一个新问题了...
- 当然, 至少3+种方法可以嗯哼...


# 用时

- .5h blogging
- 1.h 研究并完成配置






