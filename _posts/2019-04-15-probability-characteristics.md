---
layout: post
title:  "概率论-随机变量的数字特征"
categories: 机器学习
tags: 机器学习 数学基础 概率论
author: naiixeel
---

* content
{:toc}

### 期望

随机变量的数学期望的本质是加权平均，它是一个数不再是随机变量，反映了随机变量平均取值的大小。随机变量 $X$ 的数学期望定义为

$$
\begin{align}
离散随机变量 \quad &E(X)=\sum_{x}xP(X=x) \\
连续随机变量 \quad &E(X)=\int_{-\infty}^{+\infty} xf(x)dx
\end{align}
$$

若随机变量 $Y​$ 符合函数 $Y=g(X)​$，则随机变量 $Y​$ 的数学期望定义为

$$
\begin{align}
离散随机变量 \quad &E(Y)=E(g(X))=\sum_{x}g(x)P(X=x) \\
连续随机变量 \quad &E(Y)=E(g(X))=\int_{-\infty}^{+\infty} g(x)f(x)dx
\end{align}
$$

设 $(X,Y)$ 为二维离散型随机变量，则 $(X,Y)$ 的函数 $Z=g(X,Y)$ 的数学期望定义为

$$
\begin{align}
离散随机变量 \quad &E(Z)=E(g(X,Y))=\sum_{x}\sum_{y}g(x,y)P(X=x,Y=y) \\
连续随机变量 \quad &E(Z)=E(g(X,Y))=\int_{-\infty}^{+\infty}\int_{-\infty}^{+\infty} g(x,y)f_{X,Y}(x,y)dxdy
\end{align}
$$

数学期望具有以下性质：

> - $E(C) = C$，$C$ 为常数
> - $E(aX) = aE(X)$，$a$ 为任意常数
> - $E(X+Y) = E(X) +E(Y)$
> - 当 $X​$ 和 $Y​$ 相互独立时， $E(XY) = E(X)E(Y)​$ 

### 方差

若 $E ((X - E(X))^2)​$ 存在，则称其为随机变量 $X​$ 的方差,  记为 $D(X)​$，称 $\sqrt{D(X)}​$ 为随机变量 $X​$ 的标准差。常用的计算方差的公式为

$$
D(X)=E(X^2)-E^2(X)
$$

方差具有以下性质:

> - $D(C) = 0$
> - $D(aX)=a^2D(X)​$
> - $D(X \pm Y) = D(X)+D(Y) \pm 2E((X-E(X))E(Y-E(Y)))​$
> - 若 $X$ 和 $Y$ 相互独立，则 $D(X \pm Y) = D(X)+D(Y)$
> - 对任意常数 $C$, $D(X)= E(X – C)^2$ , 当且仅当 $C = E(X)$ 时等号成立
> - $D(X)=0 \Leftrightarrow P(X=E(X))=1$

### 标准化随机变量

设随机变量 $X$ 的期望 $E(X)$ 和方差 $D(X)$ 都存在, 且 $D(X) \neq 0$, 则称

$$
X^\ast = \frac{X-E(X)}{\sqrt{D(X)}}
$$

为 $X$ 的标准化随机变量。显然有 $E(X^\ast) = 0$， $D(X^\ast) = 1​$。

### 协方差

协方差表示的是两个变量的总体的误差，二维随机变量 $(X,Y)$ 的协方差记为 ${\rm cov}(X,Y)$，协方差的计算式为

$$
{\rm cov}(X,Y) = E((X-E(X))E(Y-E(Y)))=E(XY)-E(X)E(Y)
$$

矩阵

$$
\begin{bmatrix}
D(X)&{\rm cov}(X,Y)\\
{\rm cov}(X,Y)&D(Y)
\end{bmatrix}
$$

为二维随机变量 $(X,Y)​$ 的协方差矩阵，协方差矩阵为半正定矩阵。协方差具有以下性质:

> - ${\rm cov}(X,Y)={\rm cov}(Y,X)=E(XY)-E(X)E(Y)​$ 
> - ${\rm cov}(aX,bY)=ab\,{\rm cov}(X,Y)​$
> - ${\rm cov}(X+Y,Z) = {\rm cov}(X,Z) + {\rm cov}(Y,Z)​$
> - ${\rm cov}(X,X)=D(X)​$
> - $\mid {\rm cov}(X,Y) \mid^2 \leq D(X)D(Y)​$
> - 当 $X$ 和 $Y$ 相互独立时，${\rm cov}(X,Y) = 0$

### 相关系数​

相关关系是一种非确定性的关系，研究的是变量之间线性相关程度的量。对于二维随机变量 $(X,Y)$ ，若 $D(X)>0$，$D(Y)>0$，则称

$$
E\left(\frac{(X-E(X))(Y-E(Y))}{\sqrt{D(X)}\sqrt{D(Y)}} \right) = \frac{ {\rm cov}(X,Y)}{\sqrt{D(X)}\sqrt{D(Y)}}
$$

为二维随机变量 $(X,Y)$ 的相关系数，记为 $\rho_{XY}$。同时 $\rho_{XY} ={\rm cov}(X^\ast,Y^\ast)$。如果 $X,Y$ 不相关则$\rho_{XY} = 0$ 。

### 矩

矩描述了分布的形状，随机变量 $X​$ 的 $k​$ 阶矩定义为 $\mu_k=E(X^k)​$，$k​$ 阶标准矩定义为 $m_k = E((X^\ast)^k )​$。期望(mean)，方差(variance)，偏度(skewness )以及峰度(kurtosis )是分布形状几个比较重要的度量

> - 期望 $E(X) = \mu_1 \quad \Rightarrow \quad$表示随机变量平均取值的大小
> - 方差 $D(X) = \mu_2-\mu_1^2 \quad \Rightarrow \quad$表示随机变量围绕中心值的散布程度
> - 偏度 $${\rm Skew}(X)=m_3  \quad \Rightarrow \quad$$表示随机变量分布非对称的程度，向右倾斜值为正，向左值为负
> - 峰度 ${\rm Kurt}(X)=m_4 - 3  \quad \Rightarrow \quad$表示随机变量分布在平均值处峰值的高低，峰度高意味着方差增大是由低频度的大于或小于平均值的极端差值引起的

### 参考文献

[ [1](https://static1.squarespace.com/static/54bf3241e4b0f0d81bf7ff36/t/55e9494fe4b011aed10e48e5/1441352015658/probability_cheatsheet.pdf) ] probability cheatsheet