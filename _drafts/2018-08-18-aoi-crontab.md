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

只是...

<!--more-->

定期的嗯哼


[etc_cron.sh](https://github.com/zoom-quiet/scm/blob/master/sh/cron/etc_cron.sh)


    # m h dom mon dow user  command
    1 * * * * zoomq /opt/cron/updates.sh

[updates.sh](https://github.com/zoom-quiet/scm/blob/master/sh/cron/updates.sh)

## 整体图谱


                                du.zoomquiet.io
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
                













