---
layout: post
mathjax: true
title:  "线性代数基础回顾"
categories: 机器学习
tags: 机器学习 数学基础 线性代数
author: naiixeel
---

* content
{:toc}

线性代数是关于向量和矩阵的数学。记 $n$ 为正整数，${\Bbb{R}}$ 为实数集合，则 ${\Bbb{R}}^n$ 表示一个 $n$ 维实数元组的集合。向量 $\overrightarrow{v}\in {\Bbb{R}}^n$ 是一个 $n$ 维实数元组。矩阵 $A \in {\Bbb{R}}^{m \times n}$ 表示一个 $m$ 行 $n$ 列的矩形实数阵列。许多科学、商业以及技术上的问题是使用向量和矩阵来描述的，因此需要了解向量和矩阵能够进行的数学运算。

### 基本定义

#### A 向量运算

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

向量的点乘和叉乘也可以用向量间的夹角 $\theta$ 来描述。向量的点乘公式为 $\overrightarrow{u} \cdot \overrightarrow{v}=||\overrightarrow{u} ||\,|| \overrightarrow{v}||\cos\theta$，如果两个向量的夹角为 $90^\circ$则称这两个向量是正交的。正交向量的点乘结果为零：$\overrightarrow{u} \cdot \overrightarrow{v}=||\overrightarrow{u} ||\,|| \overrightarrow{v}||\cos(90^\circ)=0$。叉乘向量的模可以表示为 $||\overrightarrow{u} \times \overrightarrow{v}||=||\overrightarrow{u} ||\,|| \overrightarrow{v}||\sin\theta$。向量的叉乘不满足交换率，即：$\overrightarrow{u} \times \overrightarrow{v} \neq \overrightarrow{v} \times \overrightarrow{u}$，实际上$\overrightarrow{u} \times \overrightarrow{v} = -\overrightarrow{v} \times \overrightarrow{u}$。

#### B 矩阵运算

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

**行列式** 矩阵 $A \in {\Bbb{R}}^{n \times n}$ 的行列式记为 $\det(A)$ 或 $|A|$

#### C 矩阵与向量的乘法

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

#### D 线性变换

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

#### E 基本向量空间

一个向量空间由一组向量以及这些向量的所有线性组合构成。例如向量空间 ${\cal{S}}={\rm{span}}\{\overrightarrow{v}_1,\overrightarrow{v}_2\}​$ 是由所有形式为 $\overrightarrow{v}=\alpha \overrightarrow{v}_1+\beta \overrightarrow{v}_2​$ 的向量组成，其中 $\alpha​$ 和 $\beta​$ 是任意实数。有三个与矩阵 $A​$ 有关的基本向量空间。

矩阵 $A​$ 的**列空间** ${\cal{C}}(A)​$ 是由矩阵 $A​$ 的列向量的线性组合产生的向量构成的向量空间：

$$
{\cal{C}}(A)\equiv \{ \overrightarrow{y}\in{\Bbb{R}}^m|\overrightarrow{y}=A\overrightarrow{x},  \overrightarrow{x}\in{\Bbb{R}}^n\}
$$

列空间表现的是线性变换  $T_A​$ 的结果可能出现的范围。通过遍历所有可能的输入 $\overrightarrow{x}​$，就可以获得矩阵 $A​$ 的列向量所有可能的线性组合。

矩阵 $A​$ 的**零空间** ${\cal{N}}(A)​$ 是由所有使线性变换  $T_A​$ 输出零向量的向量组成的向量空间：

$$
{\cal{N}}(A)\equiv\{ \overrightarrow{x} \in {\Bbb{R}}^n|A\overrightarrow{x}=\overrightarrow{0} \}
$$

零空间中的向量与矩阵的所有行向量都正交。

矩阵 $A$ 的**行空间** ${\cal{R}}(A)$ 是由矩阵 $A$ 的行向量的线性组合产生的向量构成的向量空间。行空间 ${\cal{R}}(A)$ 是零空间 ${\cal{N}}(A)$ 的正交补充，这意味着任意的向量 $\overrightarrow{v}\in {\cal{R}}(A)$ 与 $\overrightarrow{w}\in {\cal{N}}(A)$ 都有 $\overrightarrow{v}\cdot\overrightarrow{w}=0$。同时零空间和行空间构成了线性变换  $T_A$ 所在的域，${\Bbb{R}}^n={\cal{R}}(A)\bigoplus{\cal{N}}(A)$，其中$\bigoplus$ 称为正交直和。

#### F 矩阵求逆

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

### 线性代数的计算

#### A 求解方程组

如果需要求解以下方程组

$$
\begin{align}
1x_1+2x_2&=5,\\
3x_1+9x_2&=21.
\end{align}
$$

不使用线性代数的知识可以使用替换、消元或相减来求解未知数。高斯－若尔当消元法是基于矩阵行操作的求解方程组的方法，其行操作如下所示

> （1） 将一行乘以一个常数加到另一行
>
> （2）交换两行
>
> （3） 某一行乘以一个非零常数

这些行操作能够简化方程组但不会改变方程组的解。在使用高斯－若尔当消元法求解方程组时，首先需要构建一个增广矩阵：

$$
\left[
    \begin{array}{cc|c}
      1&2&5\\
      3&9&21
    \end{array}
\right]
$$

增广矩阵的第一列对应变量 $x_1​$ 的系数，第二列对应变量 $x_2​$ 的系数，第三列对应方程组等式右边的常量。高斯－若尔当消元法的步骤是从左往右依次处理增广矩阵中表示系数每一列，通过行操作将其中一个元素化为 1 成为主元，通过行变换将主元移动到矩阵主对角线上，有主元的行不能重复选择主元；通过行操作将主元所在的列内除主元外的其他元素化为 0。具体求解过程如下：

(1) 选定第一列中的 1 为主元，第二行减去 3 倍第一列主元所在的行，使第一列第二行所在的元素为 0。

$$
R_2-3R_1 \quad \Rightarrow \quad
\left[
    \begin{array}{cc|c}
      1&2&5\\
      0&3&6
    \end{array}
\right]
$$

(2) 通过在第二行乘以 1/3 将第二列中的 3 转化为主元。

$$
\frac{1}{3}R_2 \quad \Rightarrow \quad
\left[
    \begin{array}{cc|c}
      1&2&5\\
      0&1&2
    \end{array}
\right]
$$

(3) 第一行减去 2 倍第二列主元所在的行，使第二列第一行所在的元素为 0。

$$
R_1 - 2R_2 \quad \Rightarrow \quad
\left[
    \begin{array}{cc|c}
      1&0&1\\
      0&1&2
    \end{array}
\right]
$$

此时的矩阵是最简行阶梯矩阵，是矩阵最简单的形态，方程组的解为 $x_1 =1, x_2 =2​$。

#### B 将方程组转化为矩阵方程

另一个求解方程组的方法是，根据矩阵与向量的乘法的定义，将方程组转化为矩阵方程 $A\overrightarrow{x}=\overrightarrow{b}​$ 的形式，其中，$A​$ 为系数矩阵，$\overrightarrow{x}​$ 是由未知数组成的向量，$\overrightarrow{b}​$ 为常数向量。

$$
\begin{bmatrix}
1&2\\3&9
\end{bmatrix}
\begin{bmatrix}
x_1\\x_2
\end{bmatrix}
=
\begin{bmatrix}
5 \\21
\end{bmatrix}
\quad \Rightarrow \quad
A\overrightarrow{x}=\overrightarrow{b}
$$

通过在矩阵方程的两边乘以逆矩阵 $A^{-1}$ 求解出未知向量 $\overrightarrow{x}=A^{-1}\overrightarrow{b}$。

$$
A^{-1}A\overrightarrow{x}=\overrightarrow{x}=
\begin{bmatrix}
x_1 \\ x_2
\end{bmatrix}
=A^{-1}\overrightarrow{b}=
\begin{bmatrix}
3 & -\frac{2}{3}\\
-1 & \frac{1}{3}
\end{bmatrix}
\begin{bmatrix}
5 \\ 21
\end{bmatrix}
=
\begin{bmatrix}
1 \\ 2
\end{bmatrix}
$$

### 计算矩阵的逆

#### A 使用行操作

矩阵求逆的方法之一是使用高斯－若尔当消元法的方程组求解过程。在计算开始时，创建一个左边是矩阵 $A​$ 右边是单位矩阵的阵列：

$$
\left[
    \begin{array}{cc|cc}
      1&2&1&0\\
      3&9&0&1
    \end{array}
\right]
$$

然后就可以对这个阵列使用高斯－若尔当消元法：

(1) 第一个行操作是第二行减去 3 倍的第一行，$R_2 \leftarrow R_2-3R_1$ 

$$
\left[
    \begin{array}{cc|cc}
      1&2&1&0\\
      0&3&-3&1
    \end{array}
\right]
$$

(2) 第二个行操作是第二行乘以 1/3 ，$R_2 \leftarrow \frac{1}{3}R_2 ​$

$$
\left[
    \begin{array}{cc|cc}
      1&2&1&0\\
      0&1&-1&\frac{1}{3}
    \end{array}
\right]
$$

(3) 第三个行操作是第一行减去 2 倍第二行，$R_1 \leftarrow R_1 - 2R_2 $

$$
\left[
    \begin{array}{cc|cc}
      1&0&3&-\frac{2}{3}\\
      0&1&-1&\frac{1}{3}
    \end{array}
\right]
$$

经过处理后，这个阵列已经转化为最简行阶梯矩阵，阵列的右边就是矩阵 $A$ 的逆矩阵。这与求解方程组 $A\overrightarrow{x}=\overrightarrow{b}$ 执行的行操作过程是一致的。阵列的右边是一个比较方便的方式记录执行的行操作并获取逆矩阵 $A^{-1}$。

#### B 使用初等矩阵

每对矩阵执行一次行操作就等价于矩阵左乘一个初等矩阵。有三种初等矩阵对应于三种行操作：

$$
\begin{align}
{\cal{R}_\alpha}:R_1\leftarrow R_1+mR_2 \quad &\Leftrightarrow \quad E_\alpha= 
\begin{bmatrix} 1&m \\ 0&1 \end{bmatrix}\\
{\cal{R}_\beta}:R_1 \leftrightarrow R_2 \quad &\Leftrightarrow \quad E_\beta= 
\begin{bmatrix} 0&1 \\ 1&0 \end{bmatrix}\\
{\cal{R}_\gamma}:R_1\leftarrow mR_1 \quad &\Leftrightarrow \quad E_\gamma= 
\begin{bmatrix} m&0 \\ 0&1 \end{bmatrix}
\end{align}
$$

在矩阵求逆的过程中每一个行操作都对应于一个初等矩阵相乘：

(1) 第一个行操作 $R_2 \leftarrow R_2-3R_1​$ 对应于乘以初等矩阵 $E_1​$:

$$
E_1A=
\begin{bmatrix}
1 & 0\\
-3& 1
\end{bmatrix}
\begin{bmatrix}
1 & 2\\
3 & 9
\end{bmatrix}
=
\begin{bmatrix}
1 & 2\\
0 & 3
\end{bmatrix}
$$

(2) 第二个行操作 $R_2 \leftarrow \frac{1}{3}R_2 ​$ 对应于乘以初等矩阵 $E_2​$:

$$
E_2(E_1A)=
\begin{bmatrix}
1 & 0\\
0 & \frac{1}{3}
\end{bmatrix}
\begin{bmatrix}
1 & 2\\
0 & 3
\end{bmatrix}
=
\begin{bmatrix}
1 & 2\\
0 & 1
\end{bmatrix}
$$

(3) 第三个行操作 $R_1 \leftarrow R_1 - 2R_2 ​$ 对应于乘以初等矩阵 $E_3​$:

$$
E_3(E_2E_1A)=
\begin{bmatrix}
1 & -2\\
0 & 1
\end{bmatrix}
\begin{bmatrix}
1 & 2\\
0 & 1
\end{bmatrix}
=
\begin{bmatrix}
1 & 0\\
0 & 1
\end{bmatrix}
$$

因为有 $E_3E_2E_1A=E$，所以初等矩阵的乘积 $E_3E_2E_1$ 就与矩阵 $A$ 的逆矩阵 $A^{-1}$ 相等：

$$
A^{-1}=E_3E_2E_1=
\begin{bmatrix}
1 & -2\\
0 & 1
\end{bmatrix}
\begin{bmatrix}
1 & 0\\
0 & \frac{1}{3}
\end{bmatrix}
\begin{bmatrix}
1 & 0\\
-3& 1
\end{bmatrix}
=
\begin{bmatrix}
3 & -\frac{2}{3}\\
-1& \frac{1}{3}
\end{bmatrix}
$$

初等矩阵求逆的方法也证明了每一个可逆矩阵者可以分解为若干个初等矩阵相乘的形式。因为有 $A^{-1}=E_3E_2E_1$，那么 $A=(A^{-1})^{-1}=(E_3E_2E_1)^{-1}=E_1^{-1}E_2^{-1}E_3^{-1}​$。

### 其它主题

#### A 基

从直觉上来说，基是能够用来表示向量空间坐标系的一组向量。$xy​$ 平面的标准基就是由两个正交的坐标轴组成：$x​$ 轴和 $y​$ 轴。一个向量 $\overrightarrow{v}​$ 可以表示为关于这两个向量的坐标对 $(v_x, v_y)​$，或者是 $\overrightarrow{v}=v_x\hat{i}+v_y \hat{j} ​$ ，其中 $\hat{i} \equiv (1,0)​$，$\hat{j} \equiv (0,1)​$ 是$x​$ 轴和 $y​$ 轴的单位向量。也可以用其它坐标系表示向量 $\overrightarrow{v}​$。

> **定义** 一个 $n​$ 维向量空间 $\cal{S}​$ 的基是在 $\cal{S}​$ 中的任意 $n​$ 个线性无关向量的集合。

任意两个线性无关的向量 $\{\hat{e}_1,\hat{e_2}\}​$ 都可以作为向量空间 $\Bbb{R}^2​$ 的基。任意一个向量 $\overrightarrow{v} \in {\Bbb{R}}^2​$ 都可以使用这些基向量的线性组合表示：$\overrightarrow{v} =v_1 \hat{e}_1+v_2\hat{e}_2​$。同一向量  $\overrightarrow{v} ​$ 可能对应于不同的坐标对，这都取决于基的选取。在标准基 $B_s \equiv \{\hat{i}, \hat{j}\}​$ 中，坐标对为 $\overrightarrow{v} =(v_x, v_y)​$，而在其基  $B_e=\{\hat{e}_1,\hat{e}_2\}​$ 中，坐标对为 $\overrightarrow{v} =(v_1, v_2)​$，因此需要注意不同的基对应的坐标系。将一个坐标对从基 $B_e​$ 表示的坐标系转换到基 $B_s​$ 表示的坐标系就是乘以一个基变换矩阵：

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

#### B 线性变换的矩阵表示

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

#### C 向量空间的维度和基

向量空间的维度定义为表示向量空间的基中向量的个数。考虑以下向量空间 ${\cal S} = {\rm{span}} \{(1, 0, 0), (0, 1, 0), (1,1,0)\}​$，看起来它包含三个向量，所以它的维度应该是 3。但实际上这三个向量并不线性相关，它们不能构成向量空间 $\cal{S}​$ 的基。两个向量已经足够用来表示向量空间 $\cal{S}​$ 中的任何向量，所以 ${\cal S} = {\rm{span}} \{(1, 0, 0), (0, 1, 0)\}​$，这两个向量线性无关所以能构成向量空间 $\cal{S}​$ 的基。因此向量空间 $\cal{S}​$ 的维度为 $\dim({\cal S})=2​$。

有一个通用的方法用来寻找一个向量空间的基。假设有一个由 $m​$ 个向量构成的向量空间 ${\cal V} = {\rm span}\{\overrightarrow{v}_1,\overrightarrow{v}_2,\cdots,\overrightarrow{v}_m\}​$ 需要求解维度和基。为了得到向量空间 ${\cal V}​$ 的基，就必须要找到一组能够表示向量空间 ${\cal V}​$ 的线性无关的向量。我们可以使用高斯－若尔当消元法来完成这个任务。首先将向量 $\overrightarrow{v}_i​$ 写为矩阵 $M​$ 的一行，向量空间 $\cal V​$ 就对应于矩阵的行空间。接下来就使用行操作将矩阵 $M​$ 转化为最简行阶梯矩阵。因为行操作不会改变矩阵的行空间，矩阵 $M​$ 的行空间就等价于其最简行阶梯矩阵的行空间。最简行阶梯矩阵的非零行就构成了向量空间 $\cal V​$ 的基，非零行的数量就是向量空间 $\cal V​$ 的维度。

#### D 行空间，列空间和矩阵的秩

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

矩阵 $A$ 的最简行阶梯矩阵包含三个主元。主元的位置对寻找列空间 ${\cal C}(A)$ 和零空间 ${\cal N}(A)$ 的基有着十分重要的作用。向量 $\{ (1,3,0,0), (0,0,1,0), (0,0,0,1) \}$ 构成了行空间 ${\cal R}(A)$ 的基。求列空间 ${\cal C}(A)$ 的基，需要找到矩阵线性无关的列，具体做法是在最简行阶梯矩阵 ${\rm rref}(A)$ 中找到从上往下第一个非零元素为 1 的列，原始矩阵中对应的列就构成了列空间的基。在最简行阶梯矩阵 ${\rm rref}(A)$ 中，第一列、第三列和第四列是线性无关的，所以向量 $\{ (1,2,3)^T,(3,7,9)^T,(3,6,10)^T\}$  构成了列空间 ${\cal C}(A)$ 的基。

零空间 ${\cal N}(A)\equiv \{\overrightarrow{x} \in {\Bbb R}^4 | A\overrightarrow{x}=\overrightarrow{0}\}$ 基也可以通过最简行阶梯矩阵求解。最简行阶梯矩阵的第二列不包含主元，因此它对应了一个自由变量，将其记为 $s$。要求解的向量包含三个未知量和一个自由变量 $(x_1,s,x_3,x_4)$ 并且它满足以下条件：

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

未知量 $x_1$，$x_2$ 和 $x_3$ 可以用自由变量 $s$ 来表示，其中 $x_1 = -3s$，$x_3=0$，$x_4=0$。因此对于任何形式为 $(-3s,s,0,0)$ 且 $s\in {\Bbb R}$ 的向量都属于矩阵 $A$ 的零空间，矩阵 $A$ 的零空间可写为 ${\cal N}(A)={\rm {span}}\{ (-3,1,0,0)^T\}$。通过观察可知 ${\rm dim}({\cal C}(A))={\rm dim}({\cal R}(A)) = 3$，这就是矩阵 $A$ 的秩。同时，${\rm dim}({\cal R}(A))+{\rm dim}({\cal N}(A))=3+1=4$，这就是线性变换 $T_A​$ 所在空间的维度。

#### E 可逆矩阵定理

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
> (6) A 不存在零空间 (只有零向量 ${\cal N}(A)=\{\overrightarrow{0} \}$)
>
> (7) $A$ 的行列式不为零 ${\rm det}(A) \neq 0​$

  对于给定的矩阵 $A$，上面的声明要么都成立要么都不成立。一个可逆矩阵对应于 $n$ 维的线性变换 $T_A$，它将一个 $n$ 维向量空间 ${\Bbb R}^n$ 转换到另一个 $n$ 维向量空间 ${\Bbb R}^n$，并且存在一个可逆矩阵 $T_A^{-1}$ 可以抵消 $T_A$ 的影响。从另一方面来说，一个 $n\times n$ 的不可逆矩阵 $B$ 对应相当于将一个 $n$ 维向量空间  ${\Bbb R}^n$ 映射到一个子空间 ${\cal C}(B) \subsetneq {\Bbb R}^n$ 并且它有一个非空零空间。一旦矩阵 $B$ 将一个向量 $\overrightarrow{w} \in {\cal N}(B)$ 映射零向量，不存在一个可逆矩阵 $T_B^{-1}$ 能够将零向量逆变换到 $\overrightarrow{w}$。

#### F 行列式

矩阵的行列式可记为 ${\rm det}(A)​$ 或 $|A|​$，它是一个验证矩阵是否可逆的特殊方法。$2\times 2​$ 和 $3\times 3​$ 的矩阵的行列式计算公式为:

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

如果 $|A|=0$，那么 $A$ 是不可逆的，相反如果 $|A| \neq 0$，那么 $A$ 是可逆的。

#### G 特征值和特征向量

矩阵的特征向量是一组特殊的输入向量，特征向量与矩阵的乘积描述为特征向量的尺度变化。矩阵与它的一个特征向量的相乘就等价于一个常数乘以该特征向量 $A \overrightarrow{e}_\lambda=\lambda \overrightarrow{e}_\lambda$，其中常数 $\lambda$ 称为矩阵 $A$ 的特征值。求解矩阵 $A$ 的特征值可以从特征值方程 $A \overrightarrow{e}_\lambda=\lambda \overrightarrow{e}_\lambda$ 开始，可将其改写为一个零空间问题：

$$
A \overrightarrow{e}_\lambda=\lambda \overrightarrow{e}_\lambda 
\quad \Rightarrow \quad
(A-\lambda E)\overrightarrow{e}_\lambda =\overrightarrow{0}
$$

当 $|A-\lambda E|=0​$ 时，方程有解。矩阵 $A \in {\Bbb R}^{n\times n}​$ 的特征值 $\{\lambda_1,\lambda_2,\cdots,\lambda_n \}​$ 是特征多项式 $p(\lambda) = |A-\lambda E|​$ 的基础。与特征值对应的特征向量属于矩阵 $(A-\lambda E)​$ 的零空间。一些矩阵可以用它的特征值和特征向量来表示。设矩阵 $\Lambda​$ 的对角线是由矩阵 $A​$ 的特征值组成，矩阵 $Q​$ 的列由矩阵 $A​$ 的特征向量组成：

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

#### H 矩阵的 SVD 分解

将矩阵分解为特征值和特征向量只对 $n \times n$ 的方阵才有效，如果矩阵不是方阵就无法进行分解。奇异值分解 (SVD) 能适用于任意的矩阵分解和特征提取。设矩阵 $A\in {\Bbb R}^{m \times n}$，其 SVD 分解可定义为

$$
A=U\Sigma V^T
$$

其中，矩阵 $\Sigma \in {\Bbb R}^{m \times n}$ 其主对角线上的元素以外全为 0，主对角线上的每个元素都称为奇异值。矩阵 $U \in {\Bbb R}^{m \times m}$，矩阵 $V \in {\Bbb R}^{n \times n}$，矩阵 $U$ 和 $V$ 满足 $U^TU=E$，$V^TV=E$。 SVD 分解相当于将矩阵分解为 $A=旋转 \cdot 拉伸 \cdot 投影$ 的变换组合。

### 参考文献

[ [1](https://minireference.com/static/tutorials/linear_algebra_in_4_pages.pdf) ] linear algebra in 4 pages

[ [2](https://www.matongxue.com/madocs/228/) ] 如何理解矩阵特征值和特征向量？

[ [3](https://www.matongxue.com/madocs/306/) ] 如何通俗地理解奇异值？