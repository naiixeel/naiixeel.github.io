---
layout: post
mathjax: true
title:  "线性代数-线性代数的计算"
categories: 机器学习
tags: 机器学习 数学基础 线性代数
author: naiixeel
---

* content
{:toc}

### 求解方程组

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

### 将方程组转化为矩阵方程

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

### 参考文献

[ [1](https://minireference.com/static/tutorials/linear_algebra_in_4_pages.pdf) ] linear algebra in 4 pages