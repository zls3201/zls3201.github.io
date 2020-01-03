+++
title= "圆周率PI计算"
date= 2017-07-12T15:52:15+08:00
draft= true
categories = ["dev"]
tags = ["calcute","pi","dev"]
toc = true
author = "zls3201"
author_homepage =  "http://www.zls3201.com/"
+++

闲来无事 写了个圆周率计算

算法推到如下
![图片](/pi_cacl/1.jpg)

代码实现

```csharp
//sin30=0.5
double angle = 30, sin = 0.5;

for (int i = 0; i < 30; i++)
{
	var s1 = 180 / (angle / Math.Pow(2, i)) * sin;
	var s2 = 180 / (angle / Math.Pow(2, i)) * sin / Math.Sqrt(1 - sin * sin);
	Console.WriteLine("角度为 {0}度,正弦值为{1} , {2} < pi <{3}", angle / Math.Pow(2, i), sin, s1, s2);
	sin = sin / Math.Sqrt(2 + 2 * Math.Sqrt(1 - sin * sin));
}

Console.WriteLine(Math.PI);
```

<iframe width="100%" height="475" src="https://dotnetfiddle.net/Widget/qNF6Em" frameborder="0"></iframe>
