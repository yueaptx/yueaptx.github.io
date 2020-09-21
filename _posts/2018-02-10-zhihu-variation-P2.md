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
