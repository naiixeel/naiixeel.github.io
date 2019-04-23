---
layout: post
title:  "概率论-随机变量与分布"
categories: 机器学习
tags: 机器学习 数学基础 概率论
author: naiixeel
---

* content
{:toc}


### 随机变量

随机变量的本质是一种函数，是从样本空间的子集到实数的映射，将事件转换成一个数值。设随机试验为 $E$，其样本空间为 $\Omega=\{\omega\}$，如果对于每个 $\omega \in \Omega$，都有一个实数 $X(\omega)$ 和它对应，于是就得到一个定义在 $\Omega$ 上的实值单值函数 $X(\omega)$ ，称 $X(\omega)$ 为随机变量。随机变量一般用大写拉丁字母或小写希腊字母（例如 $ X,Y,Z,\xi ,\eta $）来表示，随机变量的取值一般用小写拉丁字母表示（例如 $x,y,z$）。

### 累积分布函数

累积分布函数是用来计算给定 $x$ 值的累积概率，能完整描述一个实随机变量X的概率分布。对于所有实数 $x$，累积分布函数定义如下：

$$
F_X(x)=P(X\leq x),-\infty<x<+\infty
$$

累积分布函数是一个右连续的单调递增函数，并且是它一个有界函数:

$$
\begin{align}
&有界性 \quad\lim_{x\rightarrow -\infty}F(x)=0,\;\lim_{x\rightarrow +\infty}F(x)=1 \\
&单调性 \quad F_X(x_1)\leq F_X(x_2),\;x_1<x_2\\
&右连续 \quad \lim_{x\rightarrow x_0^+}F_X(x)=F_X(x_0)
\end{align}
$$

### 离散随机变量

如果随机变量 $X​$ 的取值是有限的或者是可数无穷尽的值 $X=\{x_1,x_2,x_3,\cdots\}​$，则称 $X​$ 为离散随机变量。概率质量函数是离散随机变量在各特定取值上的概率，其数学表示如下所示：

$$
p_X(x)=P(X=x)
$$

概率质量函数具有 $p_X(x)\geq 0$ 以及 $\sum\limits_x p_X(x)=1$ 的性质。对于离散随机变量，其累积分布函数为

$$
F_X(x)=P(X\leq x)=\sum_{k\leq x}p_X(k)
$$

### 连续随机变量

如果随机变量 $X$ 由全部实数或者由一部分区间组成 $X=\{x\mid a \leq x \leq b \},\;-\infty<a<b<+\infty$，则称 $X$ 为连续随机变量，连续随机变量的取值是不可数及无穷尽的。对于连续随机变量  $X$，其累积分布函数为

$$
F(x)=\int_{-\infty}^xf(t)dt
$$

其中，$f(x)​$ 称为 $X​$ 的概率密度函数，概率密度函数非负 $f(x)\geq0​$ 且 $\int_{-\infty}^{+\infty}f(x)dx=1​$。由定义可知，连续随机变量的累积分布函数是连续函数。若 $f(x)​$ 在点 $x​$ 连续，则有 $F^\prime(x) = f(x)​$。对于任意两个实数 $x_1,x_2​$ 若有 $x_1 < x_2​$，则

$$
P\{x_1<X\leq x_2\}=F(x_2)-F(x_1)=\int_{x_1}^{x_2}f(x)dx$X$
$$

由此可得，$X$ 取任一指定实数值 $a$ 的概率为

$$
P\{X=a\}=\int_a^af(x)dx = 0
$$

因此，在计算连续性随机变量落在某一区间的概率时，可以不必区分该区间是开区间还是闭区间，有

$$
P\{a<X<b\}=P\{a\leq X\leq b\}=P\{a\leq X<b\}=P\{a<X\leq b\}
$$

由于 $P\{X=x_0\}=0​$ 但是 $\{X=x_0\}\neq \emptyset​$，所以一个事件的概率为 0，只是表示这个事件发生的可能性很小，但该事件并不一定是不可能事件。同样，一个事件的概率为1，并不意味这个事件一定是必然事件。

### 随机变量函数的分布

设随机变量 $X$ 的分布已知，若 $Y=g(X)$ 为随机变量 $X$ 的函数，则随机变量函数 $Y$ 的概率分布为

$$
P\{Y\in B\}=P\{g(X)\in B\} = P\{ X \in g^{-1}(B) \}
$$

离散随机变量的函数也为离散随机变量，设随机向量 $X$ 的概率质量函数为 $P(X = x)$，则 $X$ 的函数 $Y = g(X)$ 的概率质量函数为：

$$
P(Y=y)=P(g(X)=y)=\sum_{x:g(x)=y}P(X=x)
$$

对于连续随机变量，设随机变量 $X$ 有概率密度函数 $f(x),x\in (a,b)$，而 $y=g(x)$ 在 $x \in (a,b)$ 上是严格单调的连续函数，存在唯一的反函数 $x=h(y), y\in (\alpha,\beta)$ 并且 $h^{\prime}(y)$ 存在且连续，那么 $Y=g(X)$ 也是连续型随机变量且有概率密度函数：

$$
p(y)=f(h(y))\mid h^{\prime}(y)\mid,\quad y\in(\alpha,\beta)
$$

### 参考文献

[ [1](https://static1.squarespace.com/static/54bf3241e4b0f0d81bf7ff36/t/55e9494fe4b011aed10e48e5/1441352015658/probability_cheatsheet.pdf) ] probability cheatsheet

[ [2](https://baike.baidu.com/item/%E8%BF%9E%E7%BB%AD%E5%9E%8B%E9%9A%8F%E6%9C%BA%E5%8F%98%E9%87%8F/3318213?fr=aladdin) ] 连续型随机变量