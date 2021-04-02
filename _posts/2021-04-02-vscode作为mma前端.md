---
layout:     post
title:      用vscode作为mathematica前端
subtitle:   如果不涉及三维和排版,基本能代替原本的notebook
date:       2021-04-02
author:     CLQ
header-img: img/post-bg-cook.jpg
catalog: true
tags:
    - mathematica
    - vscode
    - 前端
---

# 简介

由于mma原本前端的一些缺陷,如没有vscode这样相对专业的代码管理功能,特殊计算时内核容易崩溃,因此mma已经有许多代替原本notebook前端的方案,如Jupyter Notebook,本文将介绍一种类似于Jupyter Notebook的方案,实现shift+enter功能,图片显示功能,wolfram lauguage server语法插件功能,markdown排版功能,latex显示,三维文件查看(还未正式加入)等功能.此外此方法还能够适应远程开发的需求,解决前端无法难以大规模print的问题,对数据处理较为友好.

# 效果展示

![](https://clq9920.github.io/img/fig/Video_20210402133542.gif)

利用(* \*)作为单元分割符,按下shift+enter后,将两个(* \*)之间的代码输入到终端执行.

# 安装方法

## 安装以下插件,软件包

单元分割插件:Code Block @weihongliang233.github

用于mma代码单元分割

wolfram lauguage server语法插件:,wolfram lauguage server @kenkangxgwe.github

用于mma代码语法注释

markdown显示软件包:mdmma @clq9920.github

用于mma输出显示

shift+enter实现插件:macros @geddski

用于实现shift+enter

## vscode插件的配置

### Code Block

打开设置,在vscode设置的配置文件中输入以下配置信息.

```json
    "code-block.color": "#FFD7000b",
    "code-block.regularexpression": [
        "matlab:^\\s*%+\\*+%+\\s*$",
        "wolfram:(^\\(\\*  \\*\\))|(^\\(\\* $)|(^ \\*\\))"
    ]
```

### wolfram lauguage server

略,参考其说明页.

### macros

打开设置,在vscode设置的配置文件中输入以下配置信息.

```json
    "macros": {
        "block-run": [
            "code-block.selectCurrentBlock",
            "workbench.action.terminal.runSelectedText"
        ]
    }
```

输入ctrl+k,进行快捷键绑定,搜索block-run,将shift+enter绑定到"block-run"

## mma软件包

### mdmma

下载地址:https://github.com/clq9920/mdmma

安装方法:参考其说明页


## 使用说明

打开vscode后,打开一个mma文件,如*.wl,输入alt+D,开启code-block插件,再打开一个终端,即可实现展示效果.

