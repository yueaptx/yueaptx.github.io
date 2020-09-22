---
layout: post
title: "番外——关于张量计算（Index notation）"
subtitle: "Intro to Index Notation"
author: "Yue"
header-mask: 0
header-style: text
catalog: true
mathjax: true
tags:
  - 计算力学
  - 应用数学
  - 有限元
---

> 这篇文章转载自[我在知乎上的专栏文章](https://zhuanlan.zhihu.com/p/20783300)

由于之后的几篇文章会用到大量的index notation形式的张量计算，所以在这里做个简要的介绍。Index notation初次接触会很不习惯，但是熟悉了之后会发现确实能大大简化张量计算书写和计算过程。
首先从简单的一阶张量—向量说起。在一个以$\{\hat{e_1},\hat{e_2},\hat{e_3}\}$为底的三维空间坐标系中,我们可以将向量表示为：

$\underline{v}=v_1\hat{e_1}+v_2\hat{e_2}+v_3\hat{e_3}$，或者用求和公式表示为：$\underline{v}=\sum_{i=1}^{3}{v_i\hat{e_i}}$

通过求和公式，已经能把之前很长的方程大大简化了。但是爱因斯坦在大概100年前提出来写求和符号也好烦啊，就不能把它也省了吗。于是他想出了一个简化的方法，后来也被称为爱因斯坦求和约定(Summation Convention)。其主要内容是：**当一个下标在单独某项中出现了两次，那么我们可以省略求和符号，但依然对这单独某项关于重复下标的所有可能值求和**。我语文不好，这句话可能解释的有点拗口，还是结合上面的向量例子来说明。首先单独某项可以是任意多项的乘积，只要不出现加减之类的，我们都姑且把它当成是单独项。在向量的例子中，$v_i\hat{e_i}$就是一个单独项，而且下标i出现了两次，因此我们可以省去求和符号，但仍然进行求和运算。即可以将向量表示为$\underline{v}=v_i\hat{e_i}$。

现在我们可以继续讨论二阶张量，一般用双下划线表示，如$\underline{\underline{I}}$。在三维坐标系中，二阶张量有9个分量。比如应力张量:

$\underline{\underline{\sigma}}=\sigma_{11}\hat{e_1}\hat{e_1}+\sigma_{12}\hat{e_1}\hat{e_2}+\sigma_{13}\hat{e_1}\hat{e_3}+\sigma_{21}\hat{e_2}\hat{e_1}+\sigma_{22}\hat{e_2}\hat{e_2}+\sigma_{23}\hat{e_2}\hat{e_3}+\sigma_{31}\hat{e_3}\hat{e_1}+\sigma_{32}\hat{e_3}\hat{e_2}+\sigma_{33}\hat{e_3}\hat{e_3}$

如果向量方程的长度还能接受的话，那二阶张量的长度就是灾难了（我打了好久啊）。但是我们现在有了Summation Convention可以用。这样就可以将其简写为：

$\underline{\underline{\sigma}}=\sigma_{ij}\hat{e_i}\hat{e_j}$

这里乘积项中i和j各出现了两次，所以都要进行求和，对于某一个i，j有三项要求和，而i本身又有三项求和，所以一共有3*3=9项。如果对这个过程不熟悉的，可以先写出带有求和符号的式子：$\underline{\underline{\sigma}}=\sum_{i=1}^{3}{\sum_{j=1}^{3}{\sigma_{ij}\hat{e_i}\hat{e_j}} }$，然后把求和符号去掉就行了。

运用Index notation时有一些重要的规则需要遵守。如果不注意会造成混乱。

**规则1. 同一个下标不能在单独某项中出现两次以上。** 举个例子，$a_{ii}b_{ij}$就是没有意义的，因为$i$出现了三次。

**规则2. 方程的每一项所含的自由下标(free index)必须一致。** Free index就是指没有重复，不用求和的下标。举个例子：$a_{iik}+b_{m}c_{mk}=d_nd_nd_k$。这个式子中，只有$k$是free index，因为它在单项中没有重复。而每一项都有$k$，是一致的，所以成立，反之如果某一项缺少$k$，那么就不成立。

接下来我们引入一个很有用的量: Kronecker delta($\delta_{ij}$)，它的定义为：

$\delta_{ij}=1, \hspace{.2in} if\hspace{.1in} i=j;$

上述定义和单位向量的乘积是一致的。比如$\hat{e_i}\cdot\hat{e_j}$在$i=j$的情况下等于1，在$i\ne j$的情况下等于0，所以我们有：$\delta_{ij}=\hat{e_i}\cdot\hat{e_j}$。$\delta_{ij}$同样是有9项，我们可以把它当成是一个二阶张量的9个分量，写成矩阵的形式就是单位矩阵I。这个不难理解，因为单位矩阵是对角线上的项等于1，其他分量等于0。而对角线上的分量就是两个下标相等的情况。趁热问个tricky的问题: 那$\delta_{kk}$是多少呢？等于3，因为k出现了两次，根据summation convention,需要进行求和，即等于$\delta_{11}+\delta_{22}+\delta_{33}=3$。

Kronecker delta有个令人兴奋的性质，举个例子说：$a_i\delta_{ij}=a_j$。语言叙述就是当某一项和Kronecker delta相乘时，如果它有和Kronecker delta相同的下标，那么可以将这个下标改成delta的另一个下标然后去掉delta。在例子中，$a_i$和$\delta_{ij}$有相同的下标i，所以可以把这个$i$改成$\delta_{ij}$的另一个下标j，然后去掉$\delta_{ij}$，就变成了$a_j$。这个性质很好证明，只要按照求和展开就一目了然了，之后就可以无脑使用了。

现在终于可以用上述知识解决问题啦。首先从向量点乘开始。

$\underline{\underline{\sigma}}\cdot \underline{n}=\sigma_{ij}\hat{e_i}\hat{e_j}\cdot n_k\hat{e_k}=\sigma_{ij}n_k\hat{e_i}\delta_{jk}=\sigma_{ij}n_j\hat{e_i}$

上式是traction的计算公式，应力张量和表面法向量的乘积，得到的是向量，通常我们把这个结果记做$\underline{t}=t_i\hat{e_i}$，带入上式得到$\sigma_{ij}n_j=t_i$。

下面就是我觉得index notation最有用的地方了，计算梯度和散度，偏微分。

首先我们引入梯度(gradient)$\nabla=\frac{\partial}{\partial x_i}\hat{e_i}=\partial_i\hat{e_i}$，注意这里也用到了summation convention，其实是三项的和。比如对于标量的梯度：$\nabla u=\partial_k\hat{e_k}u=u_{,k}\hat{e_k}=\frac{\partial u}{\partial x_1}\hat{e_1} +\frac{\partial u}{\partial x_2}\hat{e_2} +\frac{\partial u}{\partial x_3}\hat{e_3}$，得到的是向量。这里说明下一般会将$\frac{\partial u}{\partial x_i}$ 简写成$u_{,i}$这种逗号的形式，同样遵循上述所说的index notation的所有性质。对于向量的梯度：$\nabla\underline{u}=\partial_k\hat{e_k}u_i\hat{e_i}=u_{i,k}\hat{e_i}\hat{e_k}$。可以看到得到的是二阶张量。所以梯度永远是将该项的阶数升高1阶。

再来看散度(divergence)$\nabla\cdot$，多了个点乘。标量没有散度。向量的散度为：$\nabla\cdot\underline{u}=\partial_k\hat{e_k}\cdot u_i\hat{e_i}=u_{i,k}\delta_{ik}=u_{i,i}$，可以看到得到的是个标量。对于二阶张量的散度：$\nabla\cdot\underline{\underline{u}}=\partial_k\hat{e_k}\cdot u_{ij}\hat{e_i}\hat{e_j}=u_{ij,k}\delta_{ik}\hat{e_j}=u_{ij,i}\hat{e_j}$，结果是一个向量。所以散度是将该项的阶数降1阶。
作为练习可以尝试计算Laplace operator:$\nabla^2f=\nabla\cdot(\nabla f)=$?
