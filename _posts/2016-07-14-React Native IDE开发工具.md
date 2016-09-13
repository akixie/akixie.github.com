---
layout: post
title: "React Native IDE开发工具"
comments: true
description: ""
keywords: "React Native"
---

## IDE开发工具
开发工具安装与配置


## Atom + Nuclide

1. 先下载Atom
https://atom.io/
atom
2. 然后利用 Atom 的包管理器 apm 安装安装nuclide插件
$ apm install nuclide

或直接源码安装

*git clone <https://github.com/facebook/nuclide.git>*
cd nuclide

或在atom设置中安装nuclide

Preferences -> Install -> nuclide
![](http://ww3.sinaimg.cn/mw690/6314d064gw1f69db333tkj21j40u0agi.jpg)


<div style="page-break-after: always;"></div>

Atom自动代码揭示  
Atom > Open Your Keymap 文件添加

'atom-text-editor':
  'cmd-alt-l': 'editor:auto-indent'

 ![](http://ww3.sinaimg.cn/mw690/6314d064gw1f69dbme5dmj20xm0q0tdb.jpg)
 ![](http://ww2.sinaimg.cn/mw690/6314d064gw1f69dcaramuj210c14yn5a.jpg)


 <div style="page-break-after: always;"></div>

## WebStorm

Web前端开发神器 -JetBrains

下载WebStorm:

<http://www.jetbrains.com/webstorm/>

<http://soft.macx.cn/5813.htm>

下载ReactNative插件：

*git clone <https://github.com/virtoolswebplayer/ReactNative-LiveTemplate>*

打开web storm导入插件Jar包

file -> import settings -> ReactNative.jar

WebStorm不识别React Native语法解决方案
只需要开启JSX语法支持即可，具体解决方案如下:
Preferences -> Languages and Frameworks -> JavaScript -> language version下拉框里选JSX

![](http://ww2.sinaimg.cn/mw690/6314d064gw1f69d95toh9j21b40viwo6.jpg)
