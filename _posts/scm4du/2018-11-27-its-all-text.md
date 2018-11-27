---
layout: post
comments: true
author: zq
title: It s all Text 重生
description: ~ 大妈笔记,每周不一定
categories: Log
tags: scm tools logging
---


# 难以割舍的扩展: It's all text

但是, 参考: [嫑升级 FireFox 到 56 以上](http://du.zoomquiet.io/2017-11/ff-no-upgrade/)

![11568](https://addons.cdn.mozilla.net/user-media/previews/thumbs/11/11568.png?modified=1530208138)

为了继续使用这个扩展, 禁止了升级, 

...

<!--more-->


但是,从个月开始, github 宣布不在支持这种低版本的 FireFox, 几乎立即的,
在 FF 56 中, gh 各种不对劲儿了...

## 分析

因为用心使用 FireFox 十多年, 早已将 FF 的扩展组合到形成了肌肉记忆,
而升级速度地球第一的 Chrome 其扩展生态远远没有 FF 自在, 
而且核心的一组扩展, 用8年也没找到合适的相似插件.

但是, github 又是另外一个强依赖环境, 也同样配置了不少习惯响应,
现在, 官方不支持这个版本的 FireFox, 而主要浏览器环境又无法脱离 FF.

只能将 github 的使用场景从 FF 中迁移到 Chrome 中,

唯一一个问题就是:

- `It's all text` 可以指定任何一个外部编辑器
    + 用快捷键召唤起来, 编辑指定的 textare 内容
    + 以免在 网页中缺少各种现代编辑器的支持.
- 必须在 Chrome 中寻求一个对等的扩展

## 搜索

- [It's All Text for Chrome? \- Super User](https://superuser.com/questions/261689/its-all-text-for-chrome)
- [firefox \- Edit any text input shown by a browser \(mostly Chrome\) with Emacs \- Super User](https://superuser.com/questions/488348/edit-any-text-input-shown-by-a-browser-mostly-chrome-with-emacs)
- [Is there a method for making Google Chrome open textareas in vim? \- Unix & Linux Stack Exchange](https://unix.stackexchange.com/questions/99466/is-there-a-method-for-making-google-chrome-open-textareas-in-vim)
- [Editing Content with a Text Editor \- MariaDB Knowledge Base](https://mariadb.com/kb/en/meta/editing-content-with-a-text-editor/)
- [Use Atom to edit in Chrome \| Hacker News](https://news.ycombinator.com/item?id=11022356)
- ["Edit with Emacs" Chrome extension](http://psung.blogspot.com/2010/01/edit-with-emacs-chrome-extension.html)
- [GhostText / It's All Text\! \- Edit text area in standalone text editor app \- Legacy \(Muon\) / Extension Requests \- Brave Community](https://community.brave.com/t/ghosttext-its-all-text-edit-text-area-in-standalone-text-editor-app/10809)
- [GhostText as a Chrome alternative to It's All Text for Firefox · Issue \#25 · GhostText/GhostText](https://github.com/GhostText/GhostText/issues/25)
- ...


果然, 有相同问题的人是大大的有...

而且当然都进行了解决:

- windows only: [Text Editor Anywhere](http://www.listary.com/text-editor-anywhere)
- 特殊编辑器支持的:
    + [Edit in Emacs](https://github.com/stsquad/emacs_chrome)
    + [TextAid \- Chrome 网上应用店](https://chrome.google.com/webstore/detail/textaid/ppoadiihggafnhokfkpphojggcdigllp) -> Vim
    + [danhper/atomic\-chrome: Edit Chrome textareas in Atom](https://github.com/danhper/atomic-chrome) 
- 通用编辑器支持的:
    + [Keyboard Maestro](http://rocketink.net/2013/05/quickcursor-keyboard-maestro.html)
    + [Alfred](http://www.packal.org/workflow/edit-quickcursor-alternative)
    + [GhostText/GhostText: 👻 Use your text editor to write in your browser\. Everything you type in the editor will be instantly updated in the browser \(and vice versa\)\.](https://github.com/GhostText/GhostText)
    + ...


## 方案
> 快速尝试, 果断使用:

![gt_banner](https://raw.githubusercontent.com/GhostText/GhostText/master/promo/gt_banner.png)

效果:

![demo](https://github.com/GhostText/GhostText/raw/master/promo/demo.gif)


支持编辑器也广泛:

- [Sublime Text extension](https://sublime.wbond.net/packages/GhostText)
- [Atom package](https://github.com/GhostText/GhostText-for-Atom)
- [VS Code extension](https://marketplace.visualstudio.com/items?itemName=tokoph.ghosttext)
- [Vim script](https://github.com/falstro/ghost-text-vim)
- [Neovim plugin](https://github.com/raghur/vim-ghost)
- [Emacs package](https://melpa.org/#/atomic-chrome)
- ...


同时也兼容主要浏览器:

- [Chrome extension](https://chrome.google.com/webstore/detail/ghosttext/godiecgffnchndlihlpaajjcplehddca)
- [Firefox add\-on](https://addons.mozilla.org/en-US/firefox/addon/ghosttext/)
- [opera](https://addons.opera.com/en/extensions/details/download-chrome-extension-9/)


使用和 `It's all text` 有点不同:

- 不是通过快捷键
- 而是先进入对应 TextArea
- 然后点击扩展图标:
    + 启动一个 websocket 服务
    + 端口是 `:4001`
    + 并自动打开有对应扩展呼应的编辑器
- 到编辑器中自然编辑:
    + 后台自动同步编辑内容到网页中
- 以上


> 综上当前浏览器使用状态变成:

- FireFox 56 作为主浏览器, 进行主要的浏览和信息管理
- Chrome 进行翻越和 gmail
- Safari 作为调试器, 配合进行各种了 web app 前端检验环境, 以及云盘等需要口令安全记忆的网站



## 是也乎



- 181127 嗯哼到了...
- 181001 第N次尝试
- 171122 起念







