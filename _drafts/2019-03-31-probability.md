---
layout: post
title:  "概率论基础回顾"
categories: 机器学习
tags: 机器学习 数学基础 概率论
author: naiixeel
---

* content
{:toc}
### 计数方法

**A. 乘法规则**

有一个复合试验由多个步骤组成，如果第一个步骤有 $n_1$ 个可能的结果，第一个步骤有 $n_2$ 个可能的结果，……，第 $r$ 个步骤有 $n_r$ 个可能的结果，那么整个实验有 $n = \prod_{i=1}^r n_r$ 个可能的结果。

**B. 抽样结果**

在一个大小为 $n​$ 的总体中取一个大小为 $k​$ 的样本，在不同的抽样条件下可能的结果数量如下表所示：

|       | 有序 | 无序 |
| :--:  | :--: | :--: |
| 有放回 | $n^k$ | $C_{n+k-1}^k=\frac{(n+k-1)!}{k!(n-1)!}$ |
| 无放回 | $A_n^k=\frac{n!}{(n-k)!}$ | $C_n^k=\frac{n!}{k!(n-k)!}$ |

**C. 概率的简单定义**

如果试验中所有可能出现的基本事件只有有限个并且每个基本事件的出现都是等可能的，那么事件 A 发生的概率是
$$
P(A)=\frac{A包含的基本事件的个数}{基本事件的总数}
$$

### 条件概率

**A. 独立性**

设 $A,B​$ 为随机事件，如果不论事件 $A​$ 是否发生都不影响事件 $B​$ 的发生概率，那么事件 $A​$ 和 $B​$ 相互独立。当且仅当以下等式成立时，事件 $A​$ 和 $B​$ 相互独立：
$$
\begin{align}
P(AB)&=P(A)P(B)\\
P(A\mid B)&=P(A)\\
P(B\mid A)&=P(B)
\end{align}
$$
给定第三个事件 $C$，如果有 $P(AB \mid C)=P(A\mid C)P(B\mid C)$，则称事件 $A$ 和 $B$ 条件独立。事件 $A$ 和 $B$ 条件独立并不意味着它们相互独立，事件 $A$ 和 $B$ 相互独立也并不意味着它们条件独立。

**B. 联合概率**

联合概率是指在多元的概率分布中多个随机变量分别满足各自条件的概率，也就是多个事件同时发生的概率。随机事件 $A,B$ 的联合概率可记为 $P(AB)$，P(A,B) 或 $P(A\cap B)$。

**C. 边缘概率**

边缘概率是某个事件单独发生的概率，与其它事件无关。在联合概率中，把最终结果中不需要的那些事件合并成其事件的全概率就得到了某个事件的边缘概率。随机事件 $A$ 的边缘概率记为 $P(A)$。

**D. 条件概率**

条件概率是指事件 $A$ 在另外一个事件 $B$ 已经发生的条件下发生概率，记为 $P(A \mid B)$。条件概率也是一种概率，满足所有的概率理论和运算规则。条件概率可由联合概率和边缘概率得到 $P(A \mid B)=P(AB)/P(B)$。

**E. 辛普森悖论**

辛普森悖论是指在分组比较中都占优势的一方，在总评中有时反而是失势的一方。即对于事件 $A,B,C$ 可能存在 $P(A \mid BC) < P(A \mid B\overline{C})$ 且 $P(A \mid B\overline{C})<P(A \mid \overline{B}\overline{C})$ 但是 $P(A\mid B)> P(A\mid \overline{B})$ 的情况。

**F. 全概率公式**

如果事件 $B_1,B_2,\cdots,B_n$ 构成一个完备事件组，即它们两两互不，其和为全集；并且 $P(B_i)>0$，则对于任一事件 $A$ 有
$$
P(A)=P(A\mid B_1)P(B_1)+P(A\mid B_2)P(B_2)+\cdots+P(A\mid B_n)P(B_n)
$$
对于任意两随机事件 $A$ 和 $B$，如果 $B$ 和 $\overline{B}$ 构成完备事件组，则 $P(A)=P(A\mid B)P(B)+P(A|\overline{B})P(\overline{B})​$ 成立。

**G. 贝叶斯公式**

贝叶斯公式是建立在条件概率的基础上寻找事件发生的原因（即大事件 $A​$ 已经发生的条件下，分割中的小事件 $B_i​$ 的概率)，设 $B_1,B_2,\cdots,B_n​$ 是样本空间 $\Omega​$ 的一个划分，则对任一事件 $A​$ ($P(A)>0​$)，有
$$
P(B_i\mid A)=\frac{P(B_i)P(A\mid B_i)}{\sum_{j=1}^nP(B_j)P(A\mid B_j)}=\frac{P(B_i)P(A\mid B_i)}{P(A)}
$$
其中，$B_i$ 是导致试验结果 $A$ 发生的原因，$P(B_i)$ 表示 $B_i$ 发生的可能性大小，称为 $B_i$ 的先验概率(Prior)。$P(B_i \mid A)$ 称为 $B_i$ 的后验概率(Posterior)，即在试验结果 $A$ 发生后，对 $B_i$ 事件概率的重新评估。$P(A \mid B_i)/P(A)$ 称为可能性函数(Likelyhood)，这是一个调整因子，使得预估概率更接近真实概率。贝叶斯公式可以理解为
$$
后验概率　＝　先验概率 \times 调整因子
$$
表示先预估一个先验概率，然后加入实验结果，看这个实验到底是增强还是削弱了先验概率，由此得到更接近事实的后验概率。如果可能性函数 $P(A \mid B_i)/P(A)>1​$，意味着先验概率被增强，事件 $B_i​$ 的发生的可能性变大；如果可能性函数 $P(A \mid B_i)/P(A)=1​$，意味着试验结果 $A​$ 无助于判断事件$B_i​$ 的可能性；如果可能性函数 $P(A \mid B_i)/P(A)<1​$，意味着先验概率被削弱，事件 $B_i​$ 的可能性变小。在运用贝叶斯公式时，一般已知和未知条件为：

> (1) 哪种原因产生试验结果 $A​$ 是未知的，但是每种原因发生的概率已知，即 $P(B_i)​$ ；
>
> (2) 试验结果 $A$ 是已经发生的确定事实，且每种原因导致 $A$ 发生的概率已知，即$P(A \mid B_i)​$；
>
> (3) 试验结果 $A$ 发生的概率 $P(A)​$ 未知，需要使用全概率公式计算得到；
>
> (4) 求解的目标是用事件 $B_i$ 的无条件概率求其在 $A$ 发生的条件下的有条件概率 $P(B_i\mid A)$。

全概率公式可看做是由原因推知结果，而贝叶斯公式则恰好相反，其作用在于由结果推原因，即：
$$
P(B|A)=\frac{P(B)P(A\mid B)}{P(A)} \quad \Rightarrow \quad P(因\mid 果)=\frac{P(因)P(果\mid 因)}{P(果)}
$$

### 随机变量与分布

**A. 随机变量**

随机变量的本质是一种函数，是从样本空间的子集到实数的映射，将事件转换成一个数值。设随机试验为 $E$，其样本空间为 $\Omega=\{\omega\}$，如果对于每个 $\omega \in \Omega$，都有一个实数 $X(\omega)$ 和它对应，于是就得到一个定义在 $\Omega$ 上的实值单值函数 $X(\omega)$ ，称 $X(\omega)$ 为随机变量。随机变量一般用大写拉丁字母或小写希腊字母（例如 $ X,Y,Z,\xi ,\eta $）来表示，随机变量的取值一般用小写拉丁字母表示（例如 $x,y,z$）。

**B. 累积分布函数**

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
**C. 离散随机变量**

如果随机变量 $X​$ 的取值是有限的或者是可数无穷尽的值 $X=\{x_1,x_2,x_3,\cdots\}​$，则称 $X​$ 为离散随机变量。概率质量函数是离散随机变量在各特定取值上的概率，其数学表示如下所示：
$$
p_X(x)=P(X=x)
$$
概率质量函数具有 $p_X(x)\geq 0$ 以及 $\sum\limits_x p_X(x)=1$ 的性质。对于离散随机变量，其累积分布函数为
$$
F_X(x)=P(X\leq x)=\sum_{k\leq x}p_X(k)
$$
**D. 连续随机变量**

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

**E. 随机变量函数的分布**

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

### 二维随机变量及其概率分布

**A. 二维随机变量及其分布函数**

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

**B. 二维离散随机变量**

若二维随机变量 $(X,Y)​$ 所有可能取的值是有限对或可列无限多对时，则称 $(X,Y)​$ 是离散型随机变量。二维随机变量 $(X,Y)​$ 的概率质量函数为
$$
p_{X,Y}(x,y)=P\{X=x,Y=y\}
$$
与一维离散随机变量一样，二维离散随机变量 $(X,Y)​$ 的概率质量函数也具有 $P_{X,Y}(x,y)\geq 0​$ 以及 $\sum\limits_x \sum\limits_y P_{X,Y}(x,y)=1​$ 的性质。二维离散随机变量的边缘分布函数为：
$$
F_X(x) = F(x,+\infty)=\sum_{x_i\leq x}\sum_{j=1}^{+\infty}p_{ij}\\
F_Y(y) = F(+\infty,y)=\sum_{y_j\leq y}\sum_{i=1}^{+\infty}p_{ij}
$$
**C. 二维连续随机变量**

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

**D. 条件分布**

二维离散随机变量的条件分布以及贝叶斯法则为：
$$
P(Y=y\mid X=x)=\frac{P(X=x,Y=y)}{P(X=x)}=\frac{P(X=x\mid Y=y)P(Y=y)}{P(X=x)}
$$
二维连续随机变量的条件分布以及贝叶斯法则为：
$$
f_{X\mid Y}(y\mid x)=\frac{f_{X,Y}(x,y)}{f_X(x)}=\frac{f_{X\mid Y}(x\mid y)f_Y(y)}{f_X(x)}
$$
**E. 随机变量的独立性**

设 $X,Y$ 是两个随机变量，若对任意的 $x,y$ 有 $P(X\leq x, Y\leq Y)=P(X\leq x)P(Y\leq y)$ 或 $F(x,y)=F_X(x)F_Y(y)$ 则称 $X$ 和 $Y$ 相互独立。若 $X$ 和 $Y$ 相互独立，则 $f(X)$ 和 $g(Y)$ 也相互独立。

### 随机变量的数字特征

**A. 期望**

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

**B. 方差**

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

**C. 标准化随机变量**

设随机变量 $X$ 的期望 $E(X)$ 和方差 $D(X)$ 都存在, 且 $D(X) \neq 0$, 则称
$$
X^\ast = \frac{X-E(X)}{\sqrt{D(X)}}
$$
为 $X$ 的标准化随机变量。显然有 $E(X^\ast) = 0$， $D(X^\ast) = 1​$。

**D. 协方差**

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

**E. 相关系数​**

相关关系是一种非确定性的关系，研究的是变量之间线性相关程度的量。对于二维随机变量 $(X,Y)$ ，若 $D(X)>0$，$D(Y)>0$，则称
$$
E\left(\frac{(X-E(X))(Y-E(Y))}{\sqrt{D(X)}\sqrt{D(Y)}} \right) = \frac{ {\rm cov}(X,Y)}{\sqrt{D(X)}\sqrt{D(Y)}}
$$
为二维随机变量 $(X,Y)$ 的相关系数，记为 $\rho_{XY}$。同时 $\rho_{XY} ={\rm cov}(X^\ast,Y^\ast)$。如果 $X,Y$ 不相关，则$\rho_{XY} = 0$ 。

**E 矩**

矩描述了分布的形状，随机变量 $X​$ 的 $k​$ 阶矩定义为 $\mu_k=E(X^k)​$，$k​$ 阶标准矩定义为 $m_k = E((X^\ast)^k )​$。期望(mean)，方差(variance)，偏度(skewness )以及峰度(kurtosis )是分布形状几个比较重要的度量

> - 期望 $E(X) = \mu_1 \quad \Rightarrow \quad$表示随机变量平均取值的大小
> - 方差 $D(X) = \mu_2-\mu_1^2 \quad \Rightarrow \quad$表示随机变量围绕中心值的散布程度
> - 偏度 $${\rm Skew}(X)=m_3  \quad \Rightarrow \quad$$表示随机变量分布非对称的程度，向右倾斜值为正，向左值为负
> - 峰度 ${\rm Kurt}(X)=m_4 - 3  \quad \Rightarrow \quad$表示随机变量分布在平均值处峰值的高低，峰度高意味着方差增大是由低频度的大于或小于平均值的极端差值引起的

### 大数定律与中心极限定理

**A. 切比雪夫不等式**

设随机变量 $X$ 具有数学期望 $E(X)=\mu$ 和方差 $D(X)=\sigma^2$，则对任意正数 $\epsilon$，都有
$$
P\{\mid X-\mu\mid \geq \epsilon \}\leq \frac{\sigma^2}{\epsilon^2} \quad 或 \quad P\{\mid X-\mu\mid < \epsilon \}\geq \frac{\sigma^2}{\epsilon^2}
$$
方差越大， $X$ 落在区间外的概率越大，$X$ 的波动也就越大。适用范围是期望、方差都存在的随机变量。

**B. 大数定律**

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

**C. 中心极限定理**

设随机变量 $X_1,X_2,\cdots$ 相互独立，服从同一分布，且有 $E(X_i)=\mu$，$D(X_i)=\sigma^2 \neq 0$，则对于任意 $x$，有
$$
\lim_{n\rightarrow \infty}P\left\{\frac{\sum_{i=1}^nX_i-n\mu}{\sqrt{n}\sigma} \leq x \right\}=\int_{-\infty}^x\frac{1}{\sqrt{2\pi}}e^{-\frac{t^2}{2}}dt
$$
中心极限定理表明不管总体是什么分布，当样本量 $N$ 逐渐趋于无穷大时， $N$ 个抽样样本的均值的频数逐渐趋于正态分布。

### 参考文献

[ [1](https://static1.squarespace.com/static/54bf3241e4b0f0d81bf7ff36/t/55e9494fe4b011aed10e48e5/1441352015658/probability_cheatsheet.pdf) ] probability cheatsheet
[ [2](https://www.zhoulujun.cn/html/theory/math/2017_0913_8050.html) ] 贝叶斯公式由浅入深大讲解—AI基础算法入门
[ [3](https://www.cnblogs.com/Belter/p/5923828.html) ] 【概率论与数理统计】全概率公式和贝叶斯公式
[ [4](https://baike.baidu.com/item/%E8%BF%9E%E7%BB%AD%E5%9E%8B%E9%9A%8F%E6%9C%BA%E5%8F%98%E9%87%8F/3318213?fr=aladdin) ] 连续型随机变量