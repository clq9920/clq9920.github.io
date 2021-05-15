---
layout:     post
title:      mathematica张量计算
subtitle:   一个技术性笔记
date:       2021-02-17
author:     CLQ
header-img: img/nothing-in-here.jpg
catalog: true
tags:
    - mathematica
    - 张量
    - 笔记
    - 物理
---

# 简介

用mathematica计算简单的张量,方便查找.

# 基于mathematica自身的张量计算

## mathematica中的张量基础运算

### 单位四维张量($\delta_i^k$):

$$
\left(
\begin{array}{cccc}
 1 & 0 & 0 & 0 \\
 0 & 1 & 0 & 0 \\
 0 & 0 & 1 & 0 \\
 0 & 0 & 0 & 1 \\
\end{array}
\right)
$$

```mathematica
DiagonalMatrix[{1, 1, 1, 1}]
```

或者:

```mathematica
IdentityMatrix[4]
```

### 度规张量($g^{i,k}$):

$$
\left(
\begin{array}{cccc}
 1 & 0 & 0 & 0 \\
 0 & -1 & 0 & 0 \\
 0 & 0 & -1 & 0 \\
 0 & 0 & 0 & -1 \\
\end{array}
\right)
$$

```mathematica
DiagonalMatrix[{1, -1, -1, -1}]
```

### 全反单位对称张量($e^{i,k,l,m}$):

```mathematica
LeviCivitaTensor[4]
```

### 任意张量$a^{i,j},i,j=0,1,2,3$

$$
\left(
\begin{array}{cccc}
 a(1,1) & a(1,2) & a(1,3) & a(1,4) \\
 a(2,1) & a(2,2) & a(2,3) & a(2,4) \\
 a(3,1) & a(3,2) & a(3,3) & a(3,4) \\
 a(4,1) & a(4,2) & a(4,3) & a(4,4) \\
\end{array}
\right)
$$

```mathematica
Array[a, {4, 4}]
```

### 张量积运算($\otimes$)

$$
\{a(1),a(2),a(3),a(4)\}\otimes\{b(1),b(2),b(3),b(4)\}=\\
\left(
\begin{array}{cccc}
 a(1) b(1) & a(1) b(2) & a(1) b(3) & a(1) b(4) \\
 a(2) b(1) & a(2) b(2) & a(2) b(3) & a(2) b(4) \\
 a(3) b(1) & a(3) b(2) & a(3) b(3) & a(3) b(4) \\
 a(4) b(1) & a(4) b(2) & a(4) b(3) & a(4) b(4) \\
\end{array}
\right)
$$

```mathematica
Array[a,{4}]\[TensorProduct]Array[b,{4}]
```

### 张量缩并

$a^ib^i=a^0b^0+a^1b^1+a^2b^2+a^3b^3$

```mathematica
TensorContract[Array[a,{4}]\[TensorProduct]Array[b,{4}],{{1,2}}]
```


## 简单算例

$a_i a^i={a_0}^2-{a_1}^2-{a_2}^2-{a_3}^2$

```mathematica
dg = DiagonalMatrix[{1, -1, -1, -1}];

TensorContract[
 Array[a, {4}]
 \[TensorProduct]
 dg
 \[TensorProduct]
 Array[b, {4}]
 , { {1, 2}, {3, 4} }
 ]
```

$e^{i,j,l,m}e_{i,j,l,m}=-24$


```mathematica

dg = DiagonalMatrix[{1, -1, -1, -1}];

TensorContract[

 TensorContract[LeviCivitaTensor[4]\[TensorProduct](dg\[TensorProduct]dg\[TensorProduct]dg\[TensorProduct]dg), { {1, 5}, {2, 7}, {3, 9}, {4, 11} }]\[TensorProduct]LeviCivitaTensor[4],

{ {1, 5}, {2, 6}, {3, 7}, {4, 8} }

]
```

## 注意

这种方式计算张量实际上相当于张量全部展开,所以对于高阶张量,计算较慢.

# 基于mathematica张量计算包的计算

待定