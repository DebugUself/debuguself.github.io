---
layout: post
comments: true
author: zq
title: Aoi-crontab
description: ~ 大妈笔记,每周不一定
categories: Log
tags: scm ubuntu python
---

# crontab 是位好伙伴

planet 很简单粗暴,只是:

- 如何免费的发布成网站?
- 又如何自动的刷新?

<!--more-->

## github-pages
~ [User, Organization, and Project Pages - User Documentation](https://help.github.com/articles/user-organization-and-project-pages/)

第一时间想到 `github-pages` :

- 只是记忆中要一个特殊的孤子分支什么的...
- 结果官方文档一看:
  + master, gh-pages, or a /docs folder on master
  + 嗯哼?! 可以用约定的一个 master 目录就可以了?

![github_pages_docs.png（PNG 图像，494x548 像素）](http://openmindclub.qiniucdn.com/res/debuguself/github_pages_docs.png)

果然...那就简单了

    output_dir = docs

将相关配置文件中, 指定的输出目录变成 `docs`,
每次 push 到 github 时,就完成了网站的更新.

## 定期的嗯哼
~ 在所有 UNIX/Linux 环境中, 当前是 crontab

参考:[CronHowto \- Community Help Wiki](https://help.ubuntu.com/community/CronHowto)

先在用户 crontab 中配置

    # m h  dom mon dow   command
    */10 *     * * *   /opt/cron/updates.sh

每 10 秒调用一次 [updates.sh](https://github.com/zoom-quiet/scm/blob/master/sh/cron/updates.sh) 以便调试

调试好后, 更新配置为

    # m h  dom mon dow   command
    42 */8     * * *   /opt/cron/updates.sh

每8小时的第42分钟,运行一次, 并将日志输出为:

    opt/log/cron on default
    $ ls -1
    170818-planet.log
    170819-planet.log
    170820-planet.log
    170821-planet.log

这种形式...

## 整体图谱
~ 所以, 最终通过一台家用服务器, 无值守的完成了一大类静态网站的更新和发布


                                du.zoomquiet.io/planet/
                                      ^ 
                                      |
                              [[github-pages]]
    {rss} {rss} ... {rss}             ^
      \     |         /               |
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
            internet                  ^
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
            home wifi                 ^ 
                |                     |
                V                     |
            Ubuntu 16.4               | 
           /[ miniPC ]                |
          /     |                     |
      crontab   |                     |
        |       V                     +
        +--->(Planet) --> HTML -> git push



# TODO
~ 当然的故事远没有可以结束, 等待继续折腾的有:


- 固化 wifi 连接的 ip 
- 在 pyenv 中也能安装使用 baddb
- 将更新成果 email 给自己,以便知晓
- 将失败的更新 通过短信/微信/Slcak 等等渠道提醒自己
- 通过 Slack 或是其它渠道, 可以发布指令给主机进行各种必要的行为
- ...


# 用时

- .5h 研究 github-pages 文档
- 1.h 实验明确 docs 效果
- 1.h 调试 crontab 脚本
- .5h 测试全部自动化行为
- 1.h ASCII 图谱和文档化






