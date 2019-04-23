---
layout: post
mathjax: true
title:  "线性代数-基本定义"
categories: 机器学习
tags: 机器学习 数学基础 线性代数
author: naiixeel
---

* content
{:toc}

### 向量运算

可以在向量 $\overrightarrow{u}=(u_1, u_2, u_3)$ 和 $\overrightarrow{v}=(v_1,v_2,v_3)$ 上进行的运算有：加、减、数乘向量、求模、点乘和叉乘。

$$
\begin{align}
\overrightarrow{u}+\overrightarrow{v}&=(u_1+v_1, u_2+v_2, u_3+v_3)\\
\overrightarrow{u}-\overrightarrow{v}&=(u_1-v_1, u_2-v_2, u_3-v_3)\\
\alpha \overrightarrow{u}&=(\alpha u_1, \alpha u_2, \alpha u_3)\\
||\overrightarrow{u}||&=\sqrt{u_1^2+u_2^2+u_3^2}\\
\overrightarrow{u} \cdot \overrightarrow{v} &= u_1v_1 + u_2v_2+u_3v_3 \\
\overrightarrow{u} \times \overrightarrow{v} &=(u_2v_3-u_3v_2,u_3v_1-u_1v_3, u_1v_2-u_2v_1)
\end{align}
$$

向量的点乘和叉乘也可以用向量间的夹角 $\theta$ 来描述。向量的点乘公式为 $\overrightarrow{u} \cdot \overrightarrow{v}=\begin{Vmatrix} \overrightarrow{u} \end{Vmatrix}\begin{Vmatrix}\overrightarrow{v}\end{Vmatrix}\cos\theta$ ，如果两个向量的夹角为 $90^\circ$ 则称这两个向量是正交的。正交向量的点乘结果为零：$\overrightarrow{u} \cdot \overrightarrow{v}=\begin{Vmatrix}\overrightarrow{u} \end{Vmatrix}\begin{Vmatrix}\overrightarrow{v}\end{Vmatrix}\cos(90^\circ)=0$。叉乘向量的模可以表示为 $\begin{Vmatrix}\overrightarrow{u} \times \overrightarrow{v}\end{Vmatrix}=\begin{Vmatrix}\overrightarrow{u}\end{Vmatrix}\begin{Vmatrix}\overrightarrow{v}\end{Vmatrix}\sin\theta$。向量的叉乘不满足交换率，即：$\overrightarrow{u} \times \overrightarrow{v} \neq \overrightarrow{v} \times \overrightarrow{u}$，实际上$\overrightarrow{u} \times \overrightarrow{v} = -\overrightarrow{v} \times \overrightarrow{u}$。

### 矩阵运算

记 $A$ 为一个矩阵，$a_{ij}$ 为 $A$ 中的元素，则矩阵的运算可以定义如下：

**矩阵加法**

$$
C=A+B \qquad \Leftrightarrow \qquad c_{ij} = a_{ij} + b_{ij}
$$

**矩阵减法**

$$
C=A-B \qquad \Leftrightarrow \qquad c_{ij} = a_{ij} - b_{ij}
$$

**矩阵乘法** 矩阵 $A \in {\Bbb{R}}^{m \times n}$ 和 矩阵 $B \in {\Bbb{R}}^{n \times l}$ 相乘的结果为 $C \in {\Bbb{R}}^{m \times l}$，矩阵乘法不满足交换率，即 $AB\neq BA$

$$
C=AB \qquad \Leftrightarrow \qquad c_{ij} = \sum_{k=1}^n a_{ik}b{kj}
$$

**矩阵求逆** 矩阵 $A \in {\Bbb{R}}^{m \times n}​$ 的逆记为  $A^{-1} \in {\Bbb{R}}^{m \times n}​$ 

**矩阵转置** 矩阵 $A \in {\Bbb{R}}^{m \times n}$ 的转置记为  $A^T \in {\Bbb{R}}^{n \times m}$ 

$$
\begin{bmatrix}
\alpha_1&\alpha_2&\alpha_3\\
\beta_1&\beta_2&\beta_3
\end{bmatrix}^T
=
\begin{bmatrix}
\alpha_1&\beta_1\\
\alpha_2&\beta_2\\
\alpha_3&\beta_3
\end{bmatrix}
$$

**矩阵的迹** 

$$
Tr[A]\equiv \sum_{i=1}^n a_{ii}
$$

**行列式** 矩阵 $A \in {\Bbb{R}}^{n \times n}$ 的行列式记为 $\det(A)$ 或 $\begin{vmatrix} AS \end{vmatrix}$

### 矩阵与向量的乘法

矩阵与向量的乘法是矩阵与矩阵乘法的一个很重要的特例。一个 $3\times2​$ 的矩阵 $A​$ 和一个 $2\times1​$ 的列向量 $\overrightarrow{x}​$ 相乘会得到一个  $3\times1​$ 的列向量  $\overrightarrow{y}​$:

$$
\overrightarrow{y} = A\overrightarrow{x}\qquad \Leftrightarrow \qquad 
 \begin{align}
 \begin{bmatrix}
 y_1\\y_2\\y_3
 \end{bmatrix}
 &=
 \begin{bmatrix}
 a_{11}&a_{12}\\a_{21}&a_{22}\\a_{31}&a_{32}
 \end{bmatrix}
 \begin{bmatrix}
 x_1\\x_2
 \end{bmatrix}
 = 
 \begin{bmatrix}
  a_{11}x_1+a_{12}x_2\\
  a_{21}x_1+a_{22}x_2\\
  a_{31}x_1+a_{32}x_2
 \end{bmatrix}\\
 &=x_1 
 \begin{bmatrix}
 a_{11}\\a_{21}\\a_{31}
 \end{bmatrix}
 +x_2
 \begin{bmatrix}
 a_{12}\\a_{22}\\a_{32}
 \end{bmatrix} \qquad  (C)\\
 &=
 \begin{bmatrix}
 (a_{11},a_{12})\cdot\overrightarrow{x}\\
 (a_{21},a_{22})\cdot\overrightarrow{x}\\
 (a_{31},a_{32})\cdot\overrightarrow{x}
 \end{bmatrix} \qquad  \qquad \,(R)
 \end{align}
$$

有两种本质上不同但是等价的方式来解释矩阵与向量的乘法。按照列来看，矩阵 $A​$ 和向量 $\overrightarrow{x}​$ 相乘得到了矩阵列的一个线性组合，如 (C) 所示：$\overrightarrow{y} = A\overrightarrow{x}=x_1A_{[:,1]}+x_2A_{[:,2]}​$，其中 $A_{[:,1]}​$ 和 $A_{[:,2]}​$ 是矩阵 $A​$ 的第一列和第二列。按照行来看，矩阵 $A​$ 和向量 $\overrightarrow{x}​$ 相乘得到了一个由矩阵 $A​$ 的每一行点乘向量 $\overrightarrow{x}​$ 的结果组成的列向量。

### 线性变换

矩阵与向量的乘法可以用来定义线性变换的概念，这是线性代数中的关键概念之一。乘以一个矩阵 $A \in {\Bbb{R}}^{m \times n}​$ 可认为是计算了一个线性变换 $T_A​$，$T_A​$ 以 $n​$ 维向量作为输入，输出一个 $m​$ 维向量：

$$
T_A:{\Bbb{R}}^{n} \rightarrow {\Bbb{R}}^{m}
$$

对向量 $\overrightarrow{x}​$ 施加一个线性变换  $T_A​$ 等价于矩阵 $A​$ 与向量 $\overrightarrow{x}​$ 相乘：$\overrightarrow{y} = A\overrightarrow{x}​$。可以把线性变换看作是向量函数，其性质可与正则函数进行类比：

$$
\begin{align}
正则函数\; f:{\Bbb{R}} \rightarrow {\Bbb{R}}\quad &\Leftrightarrow \quad 线性变换 \; T_A:{\Bbb{R}}^{n} \rightarrow {\Bbb{R}}^{m} \\
输入\; x\in {\Bbb{R}} \quad &\Leftrightarrow \quad 输入 \; \overrightarrow{x} \in {\Bbb{R}}^n \\
输出\; f(x) \quad &\Leftrightarrow \quad 输出\; T_a(\overrightarrow{x}) = A\overrightarrow{x} \in \Bbb{R}^m\\
g\circ f = g(f(x)) \quad &\Leftrightarrow  \quad T_b(T_a(\overrightarrow{x}))=BA\overrightarrow{x}\\
反函数\; f^{-1} \quad &\Leftrightarrow \quad 矩阵的逆 A^{-1}\\
函数的零点\; f(x)=0 \quad &\Leftrightarrow \quad 矩阵的零空间 \; A\overrightarrow{x}=\overrightarrow{0} \\
函数的值域\;f(x) \quad &\Leftrightarrow \quad 矩阵的列空间 \;T_a(\overrightarrow{x})
\end{align}
$$

可以看到在对向量 $\overrightarrow{x}​$ 施加一个线性变换  $T_A​$ 后再施加一个线性变换  $T_B​$ 等价于 $BA\overrightarrow{x}​$。

### 基本向量空间

一个向量空间由一组向量以及这些向量的所有线性组合构成。例如向量空间 ${\cal{S}}={\rm{span}}\begin{Bmatrix}\overrightarrow{v}_1,\overrightarrow{v}_2\end{Bmatrix}​$ 是由所有形式为 $\overrightarrow{v}=\alpha \overrightarrow{v}_1+\beta \overrightarrow{v}_2​$ 的向量组成，其中 $\alpha​$ 和 $\beta​$ 是任意实数。有三个与矩阵 $A​$ 有关的基本向量空间。

矩阵 $A​$ 的**列空间** ${\cal{C}}(A)​$ 是由矩阵 $A​$ 的列向量的线性组合产生的向量构成的向量空间：

$$
{\cal{C}}(A)\equiv \begin{Bmatrix} \overrightarrow{y}\in{\Bbb{R}}^m|\overrightarrow{y}=A\overrightarrow{x},  \overrightarrow{x}\in{\Bbb{R}}^n\end{Bmatrix}
$$

列空间表现的是线性变换  $T_A​$ 的结果可能出现的范围。通过遍历所有可能的输入 $\overrightarrow{x}​$，就可以获得矩阵 $A​$ 的列向量所有可能的线性组合。

矩阵 $A​$ 的**零空间** ${\cal{N}}(A)​$ 是由所有使线性变换  $T_A​$ 输出零向量的向量组成的向量空间：

$$
{\cal{N}}(A)\equiv\begin{Bmatrix} \overrightarrow{x} \in {\Bbb{R}}^n|A\overrightarrow{x}=\overrightarrow{0} \end{Bmatrix}
$$

零空间中的向量与矩阵的所有行向量都正交。

矩阵 $A$ 的**行空间** ${\cal{R}}(A)$ 是由矩阵 $A$ 的行向量的线性组合产生的向量构成的向量空间。行空间 ${\cal{R}}(A)$ 是零空间 ${\cal{N}}(A)$ 的正交补充，这意味着任意的向量 $\overrightarrow{v}\in {\cal{R}}(A)$ 与 $\overrightarrow{w}\in {\cal{N}}(A)$ 都有 $\overrightarrow{v}\cdot\overrightarrow{w}=0$。同时零空间和行空间构成了线性变换  $T_A$ 所在的域，${\Bbb{R}}^n={\cal{R}}(A)\bigoplus{\cal{N}}(A)$，其中$\bigoplus$ 称为正交直和。

### 矩阵求逆

按照定义，逆矩阵 $A^{-1}​$ 能够抵消矩阵 $A​$  的影响。逆矩阵 $A^{-1}​$ 和矩阵 $A​$ 相乘得到的是单位矩阵 $E​$，单位矩阵对角线上的元素为 1，其它全都为 0，它对应的线性变换为 $T_E(\overrightarrow{x}) = E\overrightarrow{x} = \overrightarrow{x}​$。

$$
A^{-1}A=E\equiv
\begin{bmatrix}
1&&0\\
&\ddots&\\
0&&1
\end{bmatrix}
$$

矩阵求逆用于求解矩阵方程，当我们在某些矩阵方程中想要去消除矩阵 $A​$，就可以乘以逆矩阵 $A^{-1}​$。例如求解矩阵方程 $AX=B​$ 中的矩阵 $X​$，可以同时在两边乘以逆矩阵 $A^{-1}​$ 得到  $X=A^{-1}B​$。

### 参考文献

[ [1](https://minireference.com/static/tutorials/linear_algebra_in_4_pages.pdf) ] linear algebra in 4 pages