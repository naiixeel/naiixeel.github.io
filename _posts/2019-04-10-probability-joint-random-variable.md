---
layout: post
title:  "概率论-二维随机变量与分布"
categories: 机器学习
tags: 机器学习 数学基础 概率论
author: naiixeel
---

* content
{:toc}

### 二维随机变量及其分布函数

设 $E$ 是一个随机试验，$\Omega$ 是它的基本空间，在 $\Omega$ 上定义两个随机变量 $X$ 和 $Y$，由它们构成的一个向量 $(X,Y)$，称为二维随机变量或二维随机向量，$X$ 和 $Y$ 称为二维随机变量的分量。对于任意实数 $x,y$，二元函数 

$$
F(x,y)=P\{X\leq x,Y\leq y\}
$$

称为二维随机变量 $(X,Y)​$ 的分布函数，或者称为随机变量 $X​$ 和 $Y​$ 的联合分布函数。分布函数 $F(x,y)​$ 具有以下性质：

> (1) $0\leq F(x,y)\leq1​$，并且 $F(-\infty,-\infty)=0​$，$F(\infty,\infty)=1​$。
>
> (2) 对任意固定的 $x$ 与 $y$，有 $F(-\infty,y)=F(x,-\infty)=0$。
>
> (3) $F(x,y)$ 是 $x$ 和 $y$ 的非减函数。当 $x_2 > x_1$ 时 $F(x_2,y) \geq F(x_1,y)$，当 $y_2 > y_1$ 时 $F(x,y_2) \geq F(x,y_1)$。
>
> (4) $F(x,y)$ 关于 $x$ 右连续，关于 $y$ 也右连续，$\lim\limits_{x\rightarrow x_0^+}F(x,y)=F(x_0,y)$，$\lim\limits_{y\rightarrow y_0^+}F(x,y)=F(x,y_0)​$。

当任一个随机变量的值趋于 $+\infty$ 时，便得到另一个随机变量的分布函数:

$$
F(x,+\infty)=P\{X\leq x,Y<+\infty\}=P\{X\leq x\}=F_X(x)\\
F(+\infty,y)=P\{X<+\infty,Y\leq y\}=P\{Y\leq y\}=F_Y(y)
$$

$F_X(x)$ 和 $F_Y(y)$ 分别叫做随机变量 $(X,Y)$ 关于 $X$ 和 $Y$ 的边缘分布函数。

### 二维离散随机变量

若二维随机变量 $(X,Y)​$ 所有可能取的值是有限对或可列无限多对时，则称 $(X,Y)​$ 是离散型随机变量。二维随机变量 $(X,Y)​$ 的概率质量函数为

$$
p_{X,Y}(x,y)=P\{X=x,Y=y\}
$$

与一维离散随机变量一样，二维离散随机变量 $(X,Y)​$ 的概率质量函数也具有 $P_{X,Y}(x,y)\geq 0​$ 以及 $\sum\limits_x \sum\limits_y P_{X,Y}(x,y)=1​$ 的性质。二维离散随机变量的边缘分布函数为：

$$
F_X(x) = F(x,+\infty)=\sum_{x_i\leq x}\sum_{j=1}^{+\infty}p_{ij}\\
F_Y(y) = F(+\infty,y)=\sum_{y_j\leq y}\sum_{i=1}^{+\infty}p_{ij}
$$

### 二维连续随机变量

对于二维随机变量 $(X,Y)​$ 的分布函数 $F(x,y)​$，如果存在非负的函数 $f(x,y)​$ 对于任意的 $x,y​$  有

$$
F(x,y)=\int_{-\infty}^y\int_{-\infty}^xf(u,v)dudv
$$

则称 $(X,Y)$ 是二维连续随机变量，函数 $f(x,y)$ 称为二维连续随机变量 $(X,Y)$ 的概率密度函数。概率密度函数 $f(x,y)$ 具有 $f(x,y) \geq 0$  以及 $\int_{-\infty}^{+\infty}\int_{-\infty}^{+\infty}f(x,y)dxdy=1$ 的性质。分布函数 $F(x,y)$ 整个二维平面上连续且有：

$$
\frac{\partial^2F(x,y)}{\partial x \partial y} = f(x,y)
$$

二维连续随机变量的边缘分布函数为：

$$
F_X(x) = F(x,+\infty)=\int_{-\infty}^x\left[\int_{-\infty}^{+\infty} f(x,y)dy\right]dx=\int_{-\infty}^xf_X(x)dx\\
F_Y(y) = F(+\infty,y)=\int_{-\infty}^y\left[\int_{-\infty}^{+\infty} f(x,y)dx\right]dy=\int_{-\infty}^xf_Y(y)dy
$$

其中，$f_X(x)$ 和 $f_Y(y)$ 随机变量 $(X,Y)$  关于 $X$ 和 $Y$ 的边缘概率密度。

### 条件分布

二维离散随机变量的条件分布以及贝叶斯法则为：

$$
P(Y=y\mid X=x)=\frac{P(X=x,Y=y)}{P(X=x)}=\frac{P(X=x\mid Y=y)P(Y=y)}{P(X=x)}
$$

二维连续随机变量的条件分布以及贝叶斯法则为：

$$
f_{X\mid Y}(y\mid x)=\frac{f_{X,Y}(x,y)}{f_X(x)}=\frac{f_{X\mid Y}(x\mid y)f_Y(y)}{f_X(x)}
$$

### 随机变量的独立性

设 $X,Y$ 是两个随机变量，若对任意的 $x,y$ 有 $P(X\leq x, Y\leq Y)=P(X\leq x)P(Y\leq y)$ 或 $F(x,y)=F_X(x)F_Y(y)$ 则称 $X$ 和 $Y$ 相互独立。若 $X$ 和 $Y$ 相互独立，则 $f(X)$ 和 $g(Y)$ 也相互独立。

### 参考文献

[ [1](https://static1.squarespace.com/static/54bf3241e4b0f0d81bf7ff36/t/55e9494fe4b011aed10e48e5/1441352015658/probability_cheatsheet.pdf) ] probability cheatsheet