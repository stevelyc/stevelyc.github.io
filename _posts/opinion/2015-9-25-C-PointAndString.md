---
layout: post
title: Pointer and String
category: opinion
description: 字符串和指针，这个也算是C语言中的一个难点。今天我就跟大家谈谈我的理解
---

首先，当我们实现字符串，也就是我们定义一个字符串时，我们有两种方法，1.数组实现，2.指针实现
<code>
	char *strp = "Hello world";
	char str[] = "Hello word";
</code>
数组定义的没什么要说的。大家应该都知道，一篇连续的存储空间，然后...（自行脑补吧）。那么咱们着重来看一下指针实现。指针的是实现也
时开辟一片连续区域，依次存储字符串的每一个字符，末尾加上空字符。但是一定要注意，此时的指针指向的是字符串的第一个字符。

今天主要想跟大家说的是一种我们常见的指针与数组之间的复制错误,情形如下：
<code>
	
</code>

z