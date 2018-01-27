---
layout: post
comments: true
author: bear
title: 熊本怼圈感受:泽鱼与溪鱼
description:  熊本怼圈感受
categories: Log
tags: summary
---

```
渔父词 唐.储光羲

泽鱼好鸣水,溪鱼好上流.
渔梁不得意,下渚潜垂钩.
乱荇时碍楫,新芦复隐舟.
...
素发随风扬,远心与云游.
逆浪还极浦,信潮下沧洲.
非为徇形役,所乐在行休.

注:渔梁为捕鱼工程,古时在上流建木闸,可诱捕进出闸门的鱼.
```

- 怼圈与开智不同,花样繁多.本熊在自怼圈第1期招新时来到自怼圈.第1期怼员大体有3种玩法:
    + 1.立刻启动自己小项目,比如AI作音乐、统计怼员commit次数等作品；
    + 2.尝试参与小组项目
    + 3.参与维护、运营怼圈
- 本文记录了本熊加入自怼圈来30w的3个阶段,3个阶段本熊参与的项目各有不同,且角色不同.从摸索git的小白,到参与小队项目,再到参与怼圈维护.
- 每个角色有各自的乐趣,即使同为怼员,也有泽鱼与溪鱼之分.泽鱼喜好平静湖水,溪鱼喜好热闹溪流.愿大家都能体验怼圈不同角色带来的乐趣.

<!--more-->

### 第一阶段:神秘的Git！
- 本熊的背景
    + 0 ~ 10w
    + 刚加入自怼圈时,还不会使用git,github将本地diff推送到远程库.
    + 进入自怼圈干得第一件大事是,学习用git和github将本地目录与远程库进行ssh配置、连接；学习将本地diff推送到远程库.
- 本熊的行动
    + [DU2w故事:惨案:难以push到master](https://github.com/DebugUself/du4proto/blob/e56db1a41713e105c6b950c37ce3b299943fa461/DU2w.md#惨案-难以-push-到-master)
    + [[ASK]git push origin master报错refusing to merge unrelated histories应该搜索关键词是?](https://github.com/DebugUself/du4proto/issues/27)
- 本熊的感受
    + **大妈常言:用之弗学**.在本阶段,花费接近1个月时间,只为学习git push等5行简单基本命令.为何耽误良久？
        * 特殊原因:由于一开始使用Github时,身在特殊部门,网络连接经过特殊设置,导致git push等命令无法执行.后转移至其他网络环境,git push 成功.
        * 常规原因:花费较多时间试图明白ssh和git push原理,而非真正探索 **如何使用git**.
    - **认知负荷无处不在**
        * 这种负荷主要来自2方面：一方面是,老怼员已经构建起基本的怼圈规则,而新怼员需要服从于该规则,学习新规则已经导致新怼员的 **认知负荷** ；
        * 另一方面,老怼员熟悉怼圈规则是因为其创造/撰写了规则(截止目前怼圈已有56篇wiki),而新怼员熟悉怼圈规则却要依靠阅读文档/wiki来熟悉怼圈.老怼员靠 **动手** 来学习规则,新怼员却要依靠 **看书** 来学习规则.**动手明显优于看书** .
- 本熊的改变
    + 从试图明白它是什么,转向先不管它是什么,先明白怎么用它?
    + 然而,此阶段,本熊还尚未形成 **记录习惯**,所以学习git过程中很多细节都没有可以追查的记录

### 第二阶段:进击的时间账单小队
- 本熊的背景
    + 10 ~ 20w
    + 加入自怼圈第1个小队项目,时间账单小队atl4dama
    + 时间账单项目的目标是,通过分析大妈8年的时间记录数据,衡量大妈效能
- 本熊的行动
    + [DU13w故事:熊本🐻->atl4dama见闻录1:从零开始才放心](https://github.com/DebugUself/du4proto/blob/DUW/DU13w.md#zsy---熊本-atl4u-见闻录1-从零开始才放心)
    + [DU14w故事:熊本🐻->atl4dama见闻录2: good csv可能长啥样（上）？](https://github.com/DebugUself/du4proto/blob/DUW/DU14w.md#熊本--atl4dama见闻录2-good-csv可能长啥样上)
    + [DU14w故事:熊本🐻->atl4dama见闻录2: good csv可能长啥样(下)？](https://github.com/DebugUself/du4proto/blob/DUW/DU14w.md#熊本--atl4dama见闻录2-good-csv可能长啥样下)
    + [DU15w故事:熊本🐻->atl4dama见闻录4:自学, 病在哪里？](https://github.com/DebugUself/du4proto/blob/DUW/DU15w.md#熊本--atl4dama见闻录4自学-病在哪里)
    + [DU16w故事:熊本🐻->怼圈放弃录1:5个42分钟](https://github.com/DebugUself/du4proto/blob/DUW/DU16w.md#熊本---怼圈放弃录1-5个42分钟)
    + [DU17w故事:熊本🐻->atl4dama见闻录5:以功能/管道为线索拆解代码](https://github.com/DebugUself/du4proto/blob/DUW/DU17w.md#熊本-atl4dama见闻录5以功能管道为线索拆解代码)
    + [DU17w故事:熊本🐻->小熊42分钟开发手册之狗六的魔像](https://github.com/DebugUself/du4proto/blob/3f22c0c0cf523d9baff5139563e8371f47c66f20/DU17w_draft.md#熊本-小熊42分钟开发手册之狗六的魔像)
    + [DU20w故事:熊🐻本来稿->时间账单效能小队duwk20进展](https://github.com/DebugUself/du4proto/blob/DUW/DU20w.md#熊本来稿-时间账单效能小队duwk20进展)
    + [DU28w故事:熊本🐻->atl4dama使用手册1：微小的不幸](https://github.com/DebugUself/du4proto/blob/DUW/DU28w.md#熊本-视而不见1微小的不幸)
    + [DU28w成果:atl4dama4UserManual](https://github.com/DebugUself/du4proto/blob/atl4dama/try/bearManual/atl4dama4UserManual.md)
    + [DU30w成果:alt4dama2MakeSET4](https://github.com/DebugUself/du4proto/blob/atl4dama/try/bearManual/alt4dama2MakeSET4.md)
- 本熊的感受
    + **一定要对探索过程形成可追查的记录**
        * 1. 发布issue
        * 2. 怼周会例行怼
        * 3. 怼周刊文章沉淀
    + **记录、控制探索怼圈的成本、风险**
        * 自怼圈不少探索,是需要付出 **更高的时间、精力成本,以及承担作品很可能失败的风险.** 倘若只凭着对创造的喜爱,就随意指定目标、处处播散种子,很容易陷入一事无成且自信全无的困局.(参见怼周刊[DU24w故事:熊本🐻->0902怼周会:探索之'江湖险恶'](https://github.com/DebugUself/du4proto/blob/DUW/DU24w.md#熊本-0902怼周会探索之江湖险恶))
- 本熊的改变
    + 从不记录到,形成了 **记录的习惯**
    + 将atl4dama探索过程,形成了11篇文档,并投稿怼周刊

### 第三阶段:最爱的怼周刊
- 本熊的背景
    + 20 ~ 30w
    + 编辑、发布5期怼周刊
- 本熊的行动
    + [DU26w成果:熊本🐻->怼周刊发布手册](https://github.com/DebugUself/du4proto/blob/DUW/DU26w.md#熊本-怼周刊发布手册)
    + [DU30w成果:熊本🐻->如何在怼周刊任务、成果2个版块形成固定投稿节奏？](https://github.com/DebugUself/du4proto/blob/DUW/DU30w.md#熊本-如何在怼周刊任务成果2个版块形成固定投稿节奏)
- 本熊的感受
    + **自运营**
        * 自怼圈与开智课程显著区别是 **怼圈具备自运营的性质** .在开智,课程运营人员会帮助组织多学员对一教练的答疑,而学员的沉淀笔记也往往是由开智运营人员审定发布在开智app里.**使用一个平台与构建一个平台是两种完全不同的体验.** 在怼圈,怼员自行编辑审定发布怼周刊、自行组织筹办怼周会.由 **使用平台人员升级为构建、维护平台人员, 被赋予更多创造的机会.** 参与的目标由 **完成任务** 到 **制定任务** ,自由性更多,目标也更为多样性.
    + **写自己个儿的使用手册**
        * 不要太过在乎老怼员的文档、建议、操作流程,一定要亲身体会、亲手测试.因为
        老怼员与新怼员之间,**天然存在预期偏差** :老怼员认为文档中理所应当需要记录的事,可能新怼员从来没有注意过.而新怼员认为老怼员在文档里应该给予的提示,老怼员却认为可有可无.久而久之,怼员会发现,**研究怼圈文档不如自己动手撰写新文档好**.
- 本熊的改变
    + 从依赖别人的文档企图尽快完成功能,转变至多问别人当时为什么这样写
    + 然后再写一篇基于自己个儿测试体验的新文档(参见[DU28w故事:熊本🐻->atl4dama使用手册1：微小的不幸](https://github.com/DebugUself/du4proto/blob/DUW/DU28w.md#熊本-视而不见1微小的不幸))
