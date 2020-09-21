---
layout: post
title: " 变分法简介Part 2. "
subtitle: "Intro to Calculus of Variation - Part II"
author: "Yue"
header-mask: 0
header-style: text
catalog: true
mathjax: true
tags:
  - 有限元
  - 应用数学
---

> 这篇文章转载自[我在知乎上的专栏文章](https://zhuanlan.zhihu.com/p/20727402)

### Review of Part I.

接着上次Part 1.的内容。首先回顾下，上节最后我们得到了泛函数的一阶变分：

\begin{align}
\delta I=\int_{x_1}^{x_2}(\frac{\partial F}{\partial y}-\frac{d}{dx}(\frac{\partial F}{\partial y'} ))\delta ydx+\frac{\partial F}{\partial y'}\delta y\Big|_{x_1}^{x_2}
\end{align}

从上式我们又可以得到欧拉-拉格朗日方程(E-L equation):

\begin{align}
\frac{\partial F}{\partial y}-\frac{d}{dx}(\frac{\partial F}{\partial y'})=0, \hspace{.2in} x_1\leq x\leq x_2
\end{align}

以及边界条件：
\begin{align}
\frac{\partial F}{\partial y'}\delta y\Big|_{x_1}^{x_2}=0
\end{align}

上式左边是由两项相乘得到，一项是$\frac{\partial F}{\partial y'}$，另一项是$\delta y$。很明显如果这两项的乘积为零，那么不是第一项为零就是第二项为零（或者都为零）。如果在边界$x_1$或$x_2$处$\frac{\partial F}{\partial y'}$等于零，那么我们称在$x_1$或$x_2$处满足**Natural Boundary Condition**。对应的，如果在边界$x_1$或$x_2$处$\delta y$等于零，我们就称在$x_1$或$x_2$处满足**Essential Boundary condition**。$\delta y=0$是一个比较模糊的概念，不好判断，所以我们把它等价转化一下。如果$y$在某一点处的变分为零，说明它在这点的值是确定不变的。换句话说如果$y$在边界上是确定的值(specified)，那么我们称这个是essential boundary condition。

\underline{Solution of Example 1}
现在我们终于可以解Part 1.中提出的两点之间直线最短的问题啦。
我们回忆下两点之间的路径长度泛函数是：$L=\int_{x1}^{x2}\sqrt{1+(y')^2}dx$。也就是说$F=\sqrt{1+(y')^2}$。带入欧拉-拉格朗日方程(E-L equation)：$\frac{\partial F}{\partial y} =0, \frac{\partial F}{\partial y'}=\frac{y'}{\sqrt{1+(y')^2}}$：

\begin{align}
0-\frac{d}{dx}(\frac{y'}{\sqrt{1+(y')^2}} ) =0, \hspace{.2in} x\in (x_1,x_2)
\end{align}

两个边界条件(BC)：$y(x_1)=y_1\hspace{.1in} \& \hspace{.1in} y(x_2)=y_2$，所以在两个边界点上都是Essential Boundary Condition。

然后解一下E-L方程，可以得出：$\frac{y'}{\sqrt{1+(y')^2}} =\text{constant}=C$。进一步化简可以得出：

\begin{align}
(y')^2=\frac{C^2}{(1-C^2)}
\end{align}

上式表示$y'$是常数，导数是常数的曲线是什么？是直线。加上边界条件，两点之间路径最短的曲线就是直线了。这里我们用变分法科学得解释了一个非常直观的问题。
当然上述问题中，$F$只是$y$和$y'$的函数，但是$F$完全还可能是$y''$甚至更高阶导数的函数。这时候我们用上节所说的设$\tilde{y}(x)=y(x)+\epsilon\eta(x)$的方法就有点麻烦了（但是也可行）。这里我们提供一个更高效的方法，直接对泛函数求变分。

假如泛函数$I=\int_{x_1}^{x_2}F(y,y',y'';x)dx$，那么它的一阶变分为：

\begin{align}
\delta I=\int_{x_1}^{x_2}(\frac{\partial F}{\partial y}\delta y+\frac{\partial F}{\partial y'}\delta y'+\frac{\partial F}{\partial y''}\delta y'')dx 
\end{align}

然后再进行分部积分得到：

\begin{align}
\delta I=\int_{x_1}^{x_2}(\frac{\partial F}{\partial y}-\frac{d}{dx}(\frac{\partial F}{\partial y'})+\frac{d^2}{dx^2}\frac{\partial F}{\partial y''})\delta y dx+\frac{\partial F}{\partial y''}\delta y'\Big|_ {x_1}^{x_2}+[\frac{\partial F}{\partial y'}-\frac{d}{dx}(\frac{\partial F}{\partial y''})]\delta y\Big|_{x_1}^{x_2}=0 
\end{align}

同样我们可以得到欧拉-拉格朗日方程：

\begin{align}
\frac{\partial F}{\partial y}-\frac{d}{dx}(\frac{\partial F}{\partial y'})+\frac{d^2}{dx^2}\frac{\partial F}{\partial y''}=0
\end{align}

以及边界条件：

$@x_1$ and $x_2: \frac{\partial F}{\partial y''}=0$ (Natural) or $\delta y'=0$(Essential) ; $\frac{\partial F}{\partial y'}-\frac{d}{dx}(\frac{\partial F}{\partial y''})=0$(Natural) or $y=0$(Essential)

### 带约束条件的泛函数极值问题（拉格朗日乘数）

现在我们来讨论下如果我们需要求在满足一定条件下求泛函数的极值，应该如何求解。举个简单的例子，如果给定一个区域的边界长度，我们想最大化该边界所围的区域。这类问题我们需要引进拉格朗日乘数($\lambda$)。

假设约束条件为：$J(y)=\int_{x1}^{x_2}G(y,y';x)=\text{constant}$

\begin{align}
I^* =I+\lambda J=\int_{x_1}^{x_2}(F+\lambda G)dx=\int_{x_1}^{x_2}F^*(y,y';x)dx
\end{align}

然后我们就可以转化成之前的问题来解了。还是用刚才提到的最大化面积问题为例来阐述下这个过程吧：

面积：$A=\int_{x_1}^{x_2}ydx$，

边界长度约束：$S=\int_{x_1}^{x_2}\sqrt{1+(y')^2}dx=\text{constant}$

则：$I^*=\int_{x_1}^{x_2}[y+\lambda\sqrt{1+(y')^2}]dx$

令一阶变分为零$(\delta I^*=0)$:
\begin{align}
\int_{x_1}^{x_2}[\delta y+\lambda\frac{y'}{\sqrt{1+(y')^2}}\delta y' ]dx=0
\end{align}

依旧老朋友分部积分：
\begin{align}
\delta I^*=\int_{x_1}^{x_2}[1-\lambda\frac{d}{dx}(\frac{y'}{\sqrt{1+(y')^2}})]\delta y dx+ B.C. term=0
\end{align}

这里图方便我就将边界条件项用B.C.term代替啦。然后欧拉-拉格朗日方程为：
\begin{align}
1-\lambda\frac{d}{dx}(\frac{y'}{\sqrt{1+(y')^2}})=0 \hspace{.2in} x\in (x_1,x_2)
\end{align}

现在我们可以解一下E-L方程：
\begin{align}
\frac{d}{dx}(\frac{y'}{\sqrt{1+(y')^2}})=\frac{1}{\lambda} \\
\Rightarrow \frac{y''}{(1+(y')^2)^{3/2}} =\frac{1}{\lambda} 
\end{align}

也就是说边界是曲率恒为$\frac{1}{\lambda}$ 的曲线，即半径为$\lambda$的圆，这也和我们日常的常识符合一致。
现在引用圆的参数方程：

\begin{align} 
x-x_0&=\lambda \text{cos} t\\ 
y-y_0&=\lambda \text{sin} t\ \ \ \ t \in [0,2\pi] 
\end{align}

带入原约束方程：
\begin{align}
S=\int_{x_1}^{x_2}\sqrt{1+(y')^2}dx=\int_{0}^{2\pi}\sqrt{(dx/dt)^2+(dy/dt)^2}dt=2\pi\lambda
\end{align}

可以解得半径 $\lambda=S/2\pi$。

下节开始准备开始涉及一些力学方面的知识啦，Part 1.和Part 2.还是比较偏纯数学，后面我会慢慢结合力学知识，讲解一些有限元的相关知识。
