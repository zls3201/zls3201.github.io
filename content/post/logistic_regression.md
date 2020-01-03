+++
title= "逻辑回归"
date= 2018-07-15T08:00:35+08:00
draft= false
categories = ["ml","DL","AI"]
tags = ["study","calcute"]
toc = true
author = "zls3201"
author_homepage =  "http://www.zls3201.com/"
+++

### 逻辑回归

## 1.逻辑回归数学

<p>
输入{x,y},参数$\theta$,假设函数为$H(\theta)$,损失函数为$J(\theta)$
目标:根于样本输入，确定$\theta$,是损失函数$J(\theta)$尽可能小
</p>

<p>
$$Input : X ,Y \
X\text{ is }
\begin{bmatrix}
   x^{(1)} \\
   x^{(2)} \\
   ... \\
   x^{(m-1)} \\
   x^{(m)}
\end{bmatrix}   \ Y  \text{ is }
\begin{bmatrix}
   y_1 \\
   y_2 \\
   ... \\
   y_{m-1} \\
   y_m
\end{bmatrix}  \
Parameter : \theta \text{ is }
\begin{bmatrix}
   \theta_0 \\
   \theta_1 \\
   \theta_2 \\
   ... \\
   \theta_{n-1} \\
   \theta_n
\end{bmatrix} $$
</p>


<p>$$X\text{是一个矩阵，m行（m为样本数量），n+1列。 } x^{(i)}  \text{ 是一个向量  }   [x_0,x_1,x_2,...,x_n] \text{ 其中}x_0\text{为1}$$</p>


<p>$$Y\text{是一个列向量，m行， }Y_i \in \{0,1\}$$</p>


<p>$$\theta\text{是一个列向量，行数为n+1。}\theta_i \text{ 是一个数值 }$$</p>


<p>
$$\text{Hypothesis is :} \ h_{\theta}\left( x \right) =g(  \theta^T X)$$
</p>


<p>$$\text{    where   } g(z)=\frac{1}{1+e^{-z}} $$</p>


<p>
$$
\begin{aligned}
    \text{ Lost Function: }
\end{aligned}
\begin{aligned}
J(\theta)=\frac 1 m  \sum^{m}_{i=1} \frac 1 2 (h_{\theta}(x^{(i)})-y^{(i)})^2
\end{aligned}
$$
</p>

<p>$$\text{概率密度函数  :}  \begin{cases} 
P(y=1|x;\theta)=h_\theta(x) \\

p(y=0|x;\theta)=1-h_\theta(x)  
\end{cases} $$</p>

<p>
简写为
$$
P(y|x;\theta)=(h_\theta(x))^y(1-h_\theta(x))^{1-y}
$$</p>


<p>
样本（X，Y）出现的概率为
$$
\boxed{\begin{aligned}
L(\theta)&=p(Y|X;\theta)                         \\
&= \displaystyle\prod_{i=1}^mP(y^{(i)}|x^{(i)};\theta)   \\
&= \displaystyle\prod_{i=1}^m (h_\theta(x^{(i)}))^{y^{(i)}}(1-h_{\theta}(x^{(i)}))^{1-y^{(i)}}
\end{aligned}}
$$
</p>

<p>
似然估计
$$
\boxed{\begin{aligned}
\ell(\theta)&=\log{L(\theta)}                         \\
&= \displaystyle\sum_{i=1}^m y^{(i)} \log{h(x^{(i)})}  + (1- y^{(i)} ) \log{(1-h(x^{(i)}))} 
\end{aligned}}
$$
</p>
<p>
对思然估计求导
$$  
\boxed{\begin{aligned}
\frac{\partial}{\partial\theta_j}\ell(\theta)&=\log{L(\theta)}                         \\
&= (y^{(i)}\frac{1}{g(\theta^{T}X)} + (1-y)\frac{1}{1-g(\theta^{T}X)}*{-1})\frac{\partial}{\partial\theta_{j}}g(\theta^{T}X) \\
&= (y^{(i)}\frac{1}{g(\theta^{T}X)} - (1-y)\frac{1}{1-g(\theta^{T}X)}) g(\theta^{T}X)(1-g(\theta^{T}X))\frac{\partial}{\partial\theta_{j}}\theta^{T}X  \\
&= (y(1-g(\theta^{T}X)) -(1-y)g(\theta^{T}X)  )x_{j}   \\
&= (y-h_{\theta}(x))x_{j}


\end{aligned}}
$$
</p>

<p>
为了获取$\ell(\theta)$的最大值，利用梯度上升算法
$$
\boxed{\begin{aligned}
\theta_j&:=\theta_{j}+\alpha\frac{\partial}{\partial\theta_j}\ell(\theta) \\
&:=\theta_j + \alpha(y-h_{\theta}(x))x_{j}
\end{aligned}}
$$
</p>
