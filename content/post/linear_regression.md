+++
title= "线性回归"
date= 2018-07-12T08:00:35+08:00
draft= false
categories = ["ml","DL","AI"]
tags = ["study","calcute"]
toc = true
author = "zls3201"
author_homepage =  "http://www.zls3201.com/"
+++

### 线性回归

## 1.线性回归数学

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


<p>
$$X\text{是一个矩阵，m行（m为样本数量），n+1列。 } x^{(i)}  \text{ 是一个向量  }   [x_0,x_1,x_2,...,x_n] \text{ 其中}x_0\text{为1}$$
</p>


<p>
$$
Y\text{是一个列向量，m行， }Y_i \text{ 是一个数值， }
$$
</p>


<p>
$$\theta\text{是一个列向量，行数为n+1。}
\theta_i \text{ 是一个数值 }$$
</p>


<p>
$$\text{Hypothesis is :} \ h_{\theta}\left( x \right) =  \theta^T X$$
</p>


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


<p>
为了获取$J(\theta)$的最小值，利用高斯下降算法
$$
\boxed{\begin{aligned}
\theta_j&:=\theta_{j}-\alpha\frac{\partial}{\partial\theta_j}J(\theta) \\
&:=\theta_j- \alpha\cdot\frac{1}{2}\frac{\partial}{\partial\theta_j}(h_{\theta}(x)-y)^2 \\
&:=\theta_j- \alpha\cdot2\cdot\frac{1}{2}(h_{\theta}(x)-y)(\frac{\partial}{\partial\theta_j}(h_{\theta}(x)-y)) \\
&:=\theta_j- \alpha\cdot(h(\theta)-y)\cdot\frac{\partial}{\partial\theta_j}(\sum^{m}_{i=0}\theta_ix_i-y_i) \\
&:=\theta_j- \alpha\cdot(h_{\theta}(x)-y)x_j
\end{aligned}}
$$
</p>

```python
# -*- coding: utf-8 -*-
"""
Created on Sat Jun  9 08:18:10 2018

@author: zls3201@gmail.com
"""
import numpy as np
from matplotlib import pyplot as plt
from mpl_toolkits.mplot3d import Axes3D
from matplotlib import animation as amat

def loadDataSet(fileName):
    """从文本文件加载数据.

    文件内容格式.

    Args:
        path: 传入文件名称.

    Returns:
        返回一个参数矩阵x和一个结论列向量y. For
        example:

        {'Serak': ('Rigel VII', 'Preparer'),
         'Zim': ('Irk', 'Invader'),
         'Lrrr': ('Omicron Persei 8', 'Emperor')}

        If a key from the keys argument is missing from the dictionary,
        then that row was not found in the table.

    Raises:
        IOError: An error occurred accessing the bigtable.Table object.
    
    """
    dataX=[];dataY=[]
    fr=open(fileName)
    for line in fr.readlines():
        dataArr= []
        for item in  line.strip().split('\t'):
            dataArr.append(float(item))
       
        dataX.append( dataArr[0:-1])
        dataY.append( dataArr[-1])
    
    print(dataX)
    print(dataY)
    return np.array( dataX),np.array(dataY)

def dataNomalize(dataX,dataY):
    """对数据进行归一化处理.

    文件内容格式.

    Args:
        matriX: 参数组成的矩阵x，每行为一组样本个例参数.
        vertY: 结论值组成的向量y.

    Returns:
        返回归一化后的一个参数矩阵x和一个结论列向量y. For
        example:

        {'Serak': ('Rigel VII', 'Preparer'),
         'Zim': ('Irk', 'Invader'),
         'Lrrr': ('Omicron Persei 8', 'Emperor')}

        If a key from the keys argument is missing from the dictionary,
        then that row was not found in the table.

    Raises:
        IOError: An error occurred accessing the bigtable.Table object.
    
    """
    m,n=np.shape(dataX)
    colMaxMin=[dataX.max(axis=0),dataX.min(axis=0)]

    for i in range(m):
        for j in range(n):
            #print (i,j,dataX[i][j])
            dataX[i][j]= (dataX[i][j]-colMaxMin[1][j])/colMaxMin[0][j]

    minY=dataY.min();maxY=dataY.max()

    for i in range(len(dataY)):
        dataY[i]=(dataY[i]-minY)/maxY

    print(dataX)
    print(dataY)
    return dataX,dataY

def computeCost(x,y,theta):
    m = y.shape[0]
#     J = (np.sum((X.dot(theta) - y)**2)) / (2*m)
    C = x.dot(theta) - y
    J2 = (C.T.dot(C))/ (2*m)
    return J2

def batchGradientDescent(dataX,dataY):
    matX=np.mat(dataX)
    matY=np.mat(dataY).transpose()
    m,n=np.shape(matX)
    alpha=0.001
    theta=np.ones((n,1))
    maxTimes=500
    for k in range(maxTimes):
        theta=theta-(alpha/m)*(np.dot(matX.T,np.dot(matX,theta)-matY))
        cost=computeCost(matX,matY,theta)
        print(theta,cost)
    return theta

def stochastieGradientDeccent():
    return 3

def miniBatchGradientDescent():
    return 4

if __name__ == '__main__':
    dataX,dataY=loadDataSet('house_prize.txt')
    dataX,dataY=dataNomalize(dataX,dataY)
    batchGradientDescent(dataX,dataY)


```
