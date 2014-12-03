---
layout: post
title: Awk split with specail character
categories:
- Programming
tags:
- shell awk split
---

 
##awk split使用特殊字符串做分割符##
awk的`aplit`内置函数用于将字符串分割为字符数组，函数原型如下：

    num split(s, a [, r])

将s用FS（默认）或正则表达式r（如果指定了的话）分割放到数组a中，返回字段总数。

用普通的字符/字符串分割比较简单，在这里不再演示。如果分隔符是含有特殊字符的字符串，用起来需要注意一下，否则可能得到不符合预期的分割效果。下面是一个实例：
待分割的字符串如下：

	abc*_*def*_*hij*_*klm*_*nop*_*qrs*_*tuv*_*wxyz

- 直接使用“`*_*`”分割，代码如下
<!-- lang:awk -->
	{
		split($0,field,"*_*");
		for(x in field) {
			print x, field[x];
		}
	}

执行结果如下：

> 	1 abc
> 	2
> 	3 def
> 	4
> 	5 hij
> 	6
> 	7 klm
> 	8
> 	9 nop
> 	10
> 	11 qrs
> 	12
> 	13 tuv
> 	14
> 	15 wxyz

可以看到结果中有很多空的项目，这并不是我们期望的结果。

- 将“`*_*`”改为“`\*_\*`”后再次运行，仍然得到以上结果。
- 将“`*_*`”改为“`\\*_\\*`”后再次运行，得到结果如下：

>     1 abc
>     2 def
>     3 hij
>     4 klm
>     5 nop
>     6 qrs
>     7 tuv
>     8 wxyz

这次是我们期望的结果。



----
