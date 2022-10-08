---
layout:     post
title:      blender+mathematica联合渲染
subtitle:   blender与mma的通信
date:       2021-08-17
author:     CLQ
header-img: img/nothing-in-here.jpg
catalog: true
tags:
    - blender
    - 渲染
    - mathematica
    - 3D模型
    - 计算机
    - python
    - 可视化
---


# 效果图

![](https://clq9920.github.io/draw/20210909/bblender-mmma.png)


# 起因

主要是mathematica自己的三维渲染器有点卡,而且和blender这些相比,还有提升空间.

# 简单记录

mathematica本身的模型导出有点问题,比如颜色很难导出,基本上是不可用的,因此我用wxf作为数据交换格式,在blender与mathematica之间传递模型,并自己简单写了个python脚本解析wxf数据.
