---
layout:     post
title:      个人渲染图像展示
subtitle:   小癖好
date:       2022-10-08
author:     CLQ
header-img: img/nothing-in-here.jpg
catalog:    true
tags:
    - blender
    - 渲染
    - mathematica
    - 可视化
    - 稀疏数据结构
---

# 场的渲染

关键词：三维场，三维可视化


![](https://clq9920.github.io/draw/20221008/test_0008.png)

~~似乎有点丑,之后再渲染几张(不得不说，光线追踪的渲染真慢)~~

## 什么是体积云

严格定义我不知道，大概就是云雾的渲染，云雾渲染存在一个问题，就是它是体积渲染，而非像一般物体一眼是表面或近表面渲染，这带来一个问题，就是数据量的增大，从二维到三维是一个跨越。

## blender中的体积云渲染

blender中支持体积云的渲染，但是并不擅长生成体积云，如生成openvdb文件。

### openvdb文件

openvdb是一种稀疏数据结构，稀疏数据结构有很多种，如一般的稀疏数组，而openvdb是一种优化的结构，适用于流体等的计算，进行了特殊的优化（文件体积与计算速度）。

openvdb是开源的数据格式，并且有开源的实现。

openvdb格式应该是渲染器中比较通用的稀疏数据结构。

## mma与openvdb

在尝试利用librarylink编写mma的openvdb库过程中，遇到了不少问题，最后依然有一些没解决，但是能用。

即可以实现mma的数据导出成openvdb格式，再将此openvdb在blender中渲染

<!-- (有需求的可以联系一下我) -->

最后放一个视频\(还是很丑...\)：

<iframe 
src="https://clq9920.github.io/draw/20221008/movie.mp4" 
scrolling="no" 
border="0" 
frameborder="no" 
framespacing="0" 
allowfullscreen="true" 
height=600 
width=800> 
</iframe>

# 一个烟花动画

![](https://clq9920.github.io/draw/20221008/yanhua.gif)

