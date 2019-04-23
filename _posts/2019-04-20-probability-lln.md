---
layout: post
title:  "概率论-大数定律与中心极限定理"
categories: 机器学习
tags: 机器学习 数学基础 概率论
author: naiixeel
---

### 大数定律与中心极限定理

### 切比雪夫不等式

设随机变量 $X$ 具有数学期望 $E(X)=\mu$ 和方差 $D(X)=\sigma^2$，则对任意正数 $\epsilon$，都有

$$
P\{\mid X-\mu\mid \geq \epsilon \}\leq \frac{\sigma^2}{\epsilon^2} \quad 或 \quad P\{\mid X-\mu\mid < \epsilon \}\geq \frac{\sigma^2}{\epsilon^2}
$$

方差越大， $X$ 落在区间外的概率越大，$X$ 的波动也就越大。适用范围是期望、方差都存在的随机变量。

### 大数定律

大数定律(law of large numbers)是一种描述当试验次数很大时所呈现的概率性质的定律。在随机事件的大量重复出现中，往往呈现几乎必然的规律，这个规律就是大数定律。

**切比雪夫大数定律** 设 $X_1,X_2, \cdots​$ 是一列相互独立的随机变量，他们分别存在期望 $E(X_k)​$ 和方差 $D(X_k)​$。若存在常数 $C​$ 使得，则对任意小的正数 $\epsilon​$ 有

$$
\lim_{n\rightarrow \infty}P\left\{\mid \frac{1}{n}\sum_{k=1}^nX_k- \frac{1}{n}\sum_{k=1}^nE(X_k)\mid<\epsilon\right\}=1
$$

切比雪夫大数定律表明，当 $n$ 很大时，随机变量的 $X_1,X_2, \cdots$ 算术平均值将依概率接近于这些随机变量数学期望的算术平均值。

**伯努利大数定律** 设 $\mu$ 是 $n$ 次独立试验中事件 $A$ 发生的次数，且事件 $A$ 在每次试验中发生的概率为 $p$ ，则对任意正数 $\epsilon$ 有

$$
\lim_{n\rightarrow \infty}P(\mid \frac{\mu_n}{n} -p\mid<\epsilon) = 1
$$

伯努利大数定律表明事件发生的频率依概率收敛于事件的概率，表达了频率的稳定性。

**辛钦大数定律** 设随机变量 $X_1,X_2,\cdots$ 相互独立，服从同一分布且具有数学期望 $E(X_k)=\mu$，则对于任意正数 $\epsilon$ 有

$$
\lim_{n\rightarrow \infty}P\left\{\mid\frac{1}{n}\sum_{k=1}^nX_k-\mu \mid <\epsilon \right\} = 1
$$

辛钦大数定律指出随机变量 $X$ 的数学期望的近似值的方法：将随机变量独立重复地观察 $n$ 次，可将 $n​$ 次观测值的算术平均值作为期望的近似。

### 中心极限定理

设随机变量 $X_1,X_2,\cdots$ 相互独立，服从同一分布，且有 $E(X_i)=\mu$，$D(X_i)=\sigma^2 \neq 0$，则对于任意 $x$，有

$$
\lim_{n\rightarrow \infty}P\left\{\frac{\sum_{i=1}^nX_i-n\mu}{\sqrt{n}\sigma} \leq x \right\}=\int_{-\infty}^x\frac{1}{\sqrt{2\pi}}e^{-\frac{t^2}{2}}dt
$$

中心极限定理表明不管总体是什么分布，当样本量 $N$ 逐渐趋于无穷大时， $N$ 个抽样样本的均值的频数逐渐趋于正态分布。

### 参考文献

[ [1](https://static1.squarespace.com/static/54bf3241e4b0f0d81bf7ff36/t/55e9494fe4b011aed10e48e5/1441352015658/probability_cheatsheet.pdf) ] probability cheatsheet