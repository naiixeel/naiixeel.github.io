---
layout: post
mathjax: true
title:  "线性代数-其他主题"
categories: 机器学习
tags: 机器学习 数学基础 线性代数
author: naiixeel
---

* content
{:toc}


### 基

从直觉上来说，基是能够用来表示向量空间坐标系的一组向量。$xy​$ 平面的标准基就是由两个正交的坐标轴组成：$x​$ 轴和 $y​$ 轴。一个向量 $\overrightarrow{v}​$ 可以表示为关于这两个向量的坐标对 $(v_x, v_y)​$，或者是 $\overrightarrow{v}=v_x\hat{i}+v_y \hat{j} ​$ ，其中 $\hat{i} \equiv (1,0)​$，$\hat{j} \equiv (0,1)​$ 是$x​$ 轴和 $y​$ 轴的单位向量。也可以用其它坐标系表示向量 $\overrightarrow{v}​$。

> **定义** 一个 $n​$ 维向量空间 $\cal{S}​$ 的基是在 $\cal{S}​$ 中的任意 $n​$ 个线性无关向量的集合。

任意两个线性无关的向量 $\begin{Bmatrix}\hat{e}_1,\hat{e}_2\end{Bmatrix}​$ 都可以作为向量空间 $\Bbb{R}^2​$ 的基。任意一个向量 $\overrightarrow{v} \in {\Bbb{R}}^2​$ 都可以使用这些基向量的线性组合表示：$\overrightarrow{v} =v_1 \hat{e}_1+v_2\hat{e}_2​$。同一向量  $\overrightarrow{v}​$ 可能对应于不同的坐标对，这都取决于基的选取。在标准基 $B_s \equiv \begin{Bmatrix}\hat{i}, \hat{j}\end{Bmatrix}​$ 中，坐标对为 $\overrightarrow{v} =(v_x, v_y)​$，而在其基  $B_e=\begin{Bmatrix}\hat{e}_1,\hat{e}_2\end{Bmatrix}​$ 中，坐标对为 $\overrightarrow{v} =(v_1, v_2)​$，因此需要注意不同的基对应的坐标系。将一个坐标对从基 $B_e​$ 表示的坐标系转换到基 $B_s​$ 表示的坐标系就是乘以一个基变换矩阵：

$$
\begin{bmatrix}
\overrightarrow{v}
\end{bmatrix}_{B_s}
=
\begin{bmatrix}
M_{e\rightarrow s}
\end{bmatrix}
\begin{bmatrix}
\overrightarrow{v}
\end{bmatrix}_{B_e}
\quad \Leftrightarrow \quad
\begin{bmatrix}
v_x\\v_y
\end{bmatrix}
=
\begin{bmatrix}
\hat{i}\cdot\hat{e}_1 & \hat{i}\cdot\hat{e}_2\\
\hat{j}\cdot\hat{e}_1 & \hat{j}\cdot\hat{e}_2\\
\end{bmatrix}
\begin{bmatrix}
v_1\\v_2
\end{bmatrix}
$$

基变换矩阵是一个恒等变换，向量 $\overrightarrow{v} $ 并没有发生变化，只是表达方式转换到了一个新的坐标系下。从基 $B_s$ 表示的坐标系转换到基 $B_e$ 表示的坐标系可以使用逆矩阵 $\begin{bmatrix} M_{s\rightarrow e} \end{bmatrix} = (\begin{bmatrix} M_{e\rightarrow s} \end{bmatrix})^{-1}$。

### 线性变换的矩阵表示

在表示线性变换  $T:{\Bbb{R}}^n \rightarrow {\Bbb{R}}^m​$ 时，基有着重要的作用。为了全面的描述某些线性变换 $T​$ 对应的矩阵，需要充分的理解 $T​$ 对输入空间的 $n​$ 维基向量的影响。对于线性变换  $T:{\Bbb{R}}^2 \rightarrow {\Bbb{R}}^2​$ ，其对应的矩阵为：

$$
M_T=
\begin{bmatrix}
|&|\\
T(\hat{i})&T(\hat{j})\\
|&|
\end{bmatrix}
\; \in \; {\Bbb{R}}^{2 \times 2}
$$

第一个例子，考虑将向量投影到 $x$ 轴的线性变换 $\prod_x$。对于任何一个向量 $\overrightarrow{v}=(v_x, v_y)$，都有  $\prod_x(\overrightarrow{v})=(v_x, 0)$。线性变换 $\prod_x$ 对应的矩阵为：

$$
M_{\prod_x}=
\begin{bmatrix}
\prod_x\left(\begin{bmatrix}1\\0 \end{bmatrix}\right) &
\prod_x\left(\begin{bmatrix}0\\1 \end{bmatrix}\right)
\end{bmatrix}
=
\begin{bmatrix} 
1&0\\
0&0
\end{bmatrix}
$$

第二个例子，将向量逆时针旋转 $\theta$ 角的线性变换 $R_{\theta}$ 对应的矩阵为：

$$
M_{R_\theta}=
\begin{bmatrix}
R_\theta\left(\begin{bmatrix}1\\0 \end{bmatrix}\right) &
R_\theta\left(\begin{bmatrix}0\\1 \end{bmatrix}\right)
\end{bmatrix}
=
\begin{bmatrix} 
\cos\theta&-\sin \theta\\
\sin\theta& \cos \theta
\end{bmatrix}
$$

$M_{R_\theta}$ 的第一列表明了 $R_{\theta}$ 将向量 $\hat{i}  \equiv 1\angle 0$ 映射到向量 $1\angle \theta=(\cos \theta, \sin \theta)^T$。第二列表明了 $R_{\theta}$ 将向量 $\hat{j}  \equiv 1\angle \frac{\pi}{2}$ 映射到向量 $1\angle (\frac{\pi}{2}  + \theta)=(-\sin \theta, \cos\theta)^T$。

### 向量空间的维度和基

向量空间的维度定义为表示向量空间的基中向量的个数。考虑以下向量空间 ${\cal S} = {\rm{span}} \begin{Bmatrix}(1, 0, 0), (0, 1, 0), (1,1,0)\end{Bmatrix}​$，看起来它包含三个向量，所以它的维度应该是 3。但实际上这三个向量并不线性相关，它们不能构成向量空间 $\cal{S}​$ 的基。两个向量已经足够用来表示向量空间 $\cal{S}​$ 中的任何向量，所以 ${\cal S} = {\rm{span}} \begin{Bmatrix}(1, 0, 0), (0, 1, 0)\end{Bmatrix}​$，这两个向量线性无关所以能构成向量空间 $\cal{S}​$ 的基。因此向量空间 $\cal{S}​$ 的维度为 $\dim({\cal S})=2​$。

有一个通用的方法用来寻找一个向量空间的基。假设有一个由 $m​$ 个向量构成的向量空间 ${\cal V} = {\rm span}\begin{Bmatrix}\overrightarrow{v}_1,\overrightarrow{v}_2,\cdots,\overrightarrow{v}_m\end{Bmatrix}​$ 需要求解维度和基。为了得到向量空间 ${\cal V}​$ 的基，就必须要找到一组能够表示向量空间 ${\cal V}​$ 的线性无关的向量。我们可以使用高斯－若尔当消元法来完成这个任务。首先将向量 $\overrightarrow{v}_i​$ 写为矩阵 $M​$ 的一行，向量空间 $\cal V​$ 就对应于矩阵的行空间。接下来就使用行操作将矩阵 $M​$ 转化为最简行阶梯矩阵。因为行操作不会改变矩阵的行空间，矩阵 $M​$ 的行空间就等价于其最简行阶梯矩阵的行空间。最简行阶梯矩阵的非零行就构成了向量空间 $\cal V​$ 的基，非零行的数量就是向量空间 $\cal V​$ 的维度。

### 行空间，列空间和矩阵的秩

高斯－若尔当消元法可以提取出一组线性无关的向量作为矩阵 $A​$ 行空间 ${\cal R}(A)​$ 的基。通过最简行阶梯矩阵也可以得到矩阵 $A​$ 列空间 ${\cal C}(A)​$ 和零空间 ${\cal N}(A)​$ 的基。考虑以下的矩阵和它的最简行阶梯矩阵：

$$
A=
\begin{bmatrix}
1&3&3&3\\
2&6&7&6\\
3&9&9&10
\end{bmatrix}
\quad\quad
{\rm rref}(A) =
\begin{bmatrix}
1&3&0&0\\
0&0&1&0\\
0&0&0&1
\end{bmatrix}
$$

矩阵 $A$ 的最简行阶梯矩阵包含三个主元。主元的位置对寻找列空间 ${\cal C}(A)$ 和零空间 ${\cal N}(A)$ 的基有着十分重要的作用。向量 $\begin{Bmatrix}(1,3,0,0), (0,0,1,0), (0,0,0,1)\end{Bmatrix}$ 构成了行空间 ${\cal R}(A)$ 的基。求列空间 ${\cal C}(A)$ 的基，需要找到矩阵线性无关的列，具体做法是在最简行阶梯矩阵 ${\rm rref}(A)$ 中找到从上往下第一个非零元素为 1 的列，原始矩阵中对应的列就构成了列空间的基。在最简行阶梯矩阵 ${\rm rref}(A)$ 中，第一列、第三列和第四列是线性无关的，所以向量 $\begin{Bmatrix}(1,2,3)^T,(3,7,9)^T,(3,6,10)^T\end{Bmatrix}$  构成了列空间 ${\cal C}(A)$ 的基。

零空间 ${\cal N}(A)\equiv\begin{Bmatrix}\overrightarrow{x}\in{\Bbb R}^4 \mid A\overrightarrow{x}=\overrightarrow{0}\end{Bmatrix}$ 基也可以通过最简行阶梯矩阵求解。最简行阶梯矩阵的第二列不包含主元，因此它对应了一个自由变量，将其记为 $s$。要求解的向量包含三个未知量和一个自由变量 $(x_1,s,x_3,x_4)$ 并且它满足以下条件：

$$
\begin{bmatrix}
1&3&0&0\\
0&0&1&0\\
0&0&0&1
\end{bmatrix}
\begin{bmatrix}
x_1\\s\\x_3\\x_4
\end{bmatrix}
=
\begin{bmatrix}
0\\0\\0
\end{bmatrix}
\quad \Rightarrow \quad
\begin{align}
1x_1+3s & = 0\\
1x_3 &= 0\\
1x_4 &= 0
\end{align}
$$

未知量 $x_1$，$x_2$ 和 $x_3$ 可以用自由变量 $s$ 来表示，其中 $x_1 = -3s$，$x_3=0$，$x_4=0$。因此对于任何形式为 $(-3s,s,0,0)$ 且 $s\in {\Bbb R}$ 的向量都属于矩阵 $A$ 的零空间，矩阵 $A$ 的零空间可写为 ${\cal N}(A)={\rm {span}}\begin{Bmatrix} (-3,1,0,0)^T\end{Bmatrix}$。通过观察可知 ${\rm dim}({\cal C}(A))={\rm dim}({\cal R}(A)) = 3$，这就是矩阵 $A$ 的秩。同时，${\rm dim}({\cal R}(A))+{\rm dim}({\cal N}(A))=3+1=4$，这就是线性变换 $T_A​$ 所在空间的维度。

### 可逆矩阵定理

可逆矩阵与非可逆矩阵有很重要的区别，矩阵是否可逆需要看其是否满足以下定理：

> **定理:** 对于一个 $n\times n$ 的矩阵 $A$，以下的声明是等价的：
>
> (1) $A$ 是可逆矩阵
>
> (2) $A$ 的最简行阶梯矩阵是 $n\times n$ 的单位矩阵
>
> (3) 矩阵的秩为 $n$
>
> (4) $A$ 的行空间为 ${\Bbb R}^n$
>
> (4) $A$ 的列空间为 ${\Bbb R}^n$
>
> (6) A 不存在零空间 (只有零向量 ${\cal N}(A)=\begin{Bmatrix}\overrightarrow{0} \end{Bmatrix}$)
>
> (7) $A$ 的行列式不为零 ${\rm det}(A) \neq 0​$

  对于给定的矩阵 $A$，上面的声明要么都成立要么都不成立。一个可逆矩阵对应于 $n$ 维的线性变换 $T_A$，它将一个 $n$ 维向量空间 ${\Bbb R}^n$ 转换到另一个 $n$ 维向量空间 ${\Bbb R}^n$，并且存在一个可逆矩阵 $T_A^{-1}$ 可以抵消 $T_A$ 的影响。从另一方面来说，一个 $n\times n$ 的不可逆矩阵 $B$ 对应相当于将一个 $n$ 维向量空间  ${\Bbb R}^n$ 映射到一个子空间 ${\cal C}(B) \subsetneq {\Bbb R}^n$ 并且它有一个非空零空间。一旦矩阵 $B$ 将一个向量 $\overrightarrow{w} \in {\cal N}(B)$ 映射零向量，不存在一个可逆矩阵 $T_B^{-1}$ 能够将零向量逆变换到 $\overrightarrow{w}$。

### 行列式

矩阵的行列式可记为 ${\rm det}(A)​$ 或 $\begin{vmatrix}A\end{vmatrix}$，它是一个验证矩阵是否可逆的特殊方法。$2\times 2​$ 和 $3\times 3​$ 的矩阵的行列式计算公式为:

$$
\begin{align}
\begin{vmatrix}
a_{11} & a_{12}\\
a_{21} & a_{22}
\end{vmatrix}
&= a_{11}a_{22} - a_{12}a_{21}
\\
\begin{vmatrix}
a_{11} & a_{12} & a_{13}\\
a_{21} & a_{22} & a_{23}\\
a_{31} & a_{32} & a_{33}
\end{vmatrix}
&=
a_{11}
\begin{vmatrix}
a_{22} & a_{23}\\
a_{32} & a_{33}
\end{vmatrix}
-a_{12}
\begin{vmatrix}
a_{21} & a_{23}\\
a_{31} & a_{33}
\end{vmatrix}
+a_{13}
\begin{vmatrix}
a_{21} & a_{22}\\
a_{31} & a_{32}
\end{vmatrix}
\end{align}
$$

如果 $\begin{vmatrix}A\end{vmatrix}=0$，那么 $A$ 是不可逆的，相反如果 $\begin{vmatrix}A\end{vmatrix} \neq 0$，那么 $A$ 是可逆的。

### 特征值和特征向量

矩阵的特征向量是一组特殊的输入向量，特征向量与矩阵的乘积描述为特征向量的尺度变化。矩阵与它的一个特征向量的相乘就等价于一个常数乘以该特征向量: 

$$
A\overrightarrow{e}_\lambda=\lambda \overrightarrow{e}_\lambda
$$

其中常数 $\lambda$ 称为矩阵 $A$ 的特征值。求解矩阵 $A$ 的特征值可以从特征值方程开始，可将其改写为一个零空间问题：

$$
A\overrightarrow{e}_\lambda=\lambda \overrightarrow{e}_\lambda 
\quad \Rightarrow \quad
(A-\lambda E)\overrightarrow{e}_\lambda =\overrightarrow{0}
$$

当 $\begin{vmatrix}A-\lambda E\end{vmatrix}=0$ 时，方程有解。矩阵 $A \in {\Bbb R}^{n\times n}$ 的特征值 $\begin{Bmatrix}\lambda_1,\lambda_2,\cdots,\lambda_n \end{Bmatrix}$ 是特征多项式 $p(\lambda) = \begin{vmatrix}A-\lambda E\end{vmatrix}$ 的基础。与特征值对应的特征向量属于矩阵 $(A-\lambda E)$ 的零空间。一些矩阵可以用它的特征值和特征向量来表示。设矩阵 $\Lambda$ 的对角线是由矩阵 $A$ 的特征值组成，矩阵 $Q$ 的列由矩阵 $A$ 的特征向量组成：

$$
\Lambda=
\begin{bmatrix}
\lambda_1& \cdots & 0\\
\vdots   & \ddots & 0\\
0        &    0   & \lambda_n
\end{bmatrix},
Q=
\begin{bmatrix}
|&&|\\
\overrightarrow{e}_{\lambda 1}&\cdots&\overrightarrow{e}_{\lambda n}\\
|&&|
\end{bmatrix}
\quad \Rightarrow \quad
A=Q\Lambda Q^{-1}
$$

能用这种方式表示的矩阵称为可对角化。如果把矩阵看作是运动，特征值就是运动的速度，特征向量就是运动的方向。矩阵的特征值分解相当于将矩阵分解为 $A=旋转 \cdot 拉伸 \cdot 旋转$ 的变换组合。

### 矩阵的 SVD 分解

将矩阵分解为特征值和特征向量只对 $n \times n$ 的方阵才有效，如果矩阵不是方阵就无法进行分解。奇异值分解 (SVD) 能适用于任意的矩阵分解和特征提取。设矩阵 $A\in {\Bbb R}^{m \times n}$，其 SVD 分解可定义为

$$
A=U\Sigma V^T
$$

其中，矩阵 $\Sigma \in {\Bbb R}^{m \times n}$ 其主对角线上的元素以外全为 0，主对角线上的每个元素都称为奇异值。矩阵 $U \in {\Bbb R}^{m \times m}$，矩阵 $V \in {\Bbb R}^{n \times n}$，矩阵 $U$ 和 $V$ 满足 $U^TU=E$，$V^TV=E$。 SVD 分解相当于将矩阵分解为 $A=旋转 \cdot 拉伸 \cdot 投影$ 的变换组合。

### 参考文献

[ [1](https://minireference.com/static/tutorials/linear_algebra_in_4_pages.pdf) ] linear algebra in 4 pages

[ [2](https://www.matongxue.com/madocs/228/) ] 如何理解矩阵特征值和特征向量？

[ [3](https://www.matongxue.com/madocs/306/) ] 如何通俗地理解奇异值？
