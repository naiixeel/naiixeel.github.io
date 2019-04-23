---
layout: post
mathjax: true
title:  "线性代数-计算矩阵的逆"
categories: 机器学习
tags: 机器学习 数学基础 线性代数
author: naiixeel
---

* content
{:toc}

### 使用行操作

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

### 使用初等矩阵

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

### 参考文献

[ [1](https://minireference.com/static/tutorials/linear_algebra_in_4_pages.pdf) ] linear algebra in 4 pages