---
layout: post
title: 指针,数组和函数(1)
category: project
description: 这三个大兄弟,搞的我好头痛,谈谈感悟,有不对的地方,还请指正.
---
今天咱们先说一下指针和数组.首先明确这三者的定义.

指针:其实就是地址.这里我强调一下,指针只是一个地址,所有的指针都只是地址.啰嗦一句,所谓地址就是内存字节的编号
数组:程序中声明的一块用来存储数据的连续区域.
OK, 看一下他们的定义:
指针:
**数据类型 *指针变量名;
数组:
**数据类型 数组名[数组元素的个数];
指针有两个必须要说的运算符:
&:取地址运算符
*:取指针所指向的内存单元的值
举介个例子

	char *pc;
	double *pd = NULL;
	//赋值
	int num = 12;
	int *p = &num;

在这里特别说明一下指针的赋值,指针的类型是"数据类型 *" 指针变量是p,其实赋值操作真正做的是如下两个步骤:

	int *p;
	p = &num;

ok,接下来咱们看一下数组,数组的定义上面我已经说过了.数组的定义式如下所示.首先我们来看数组的定义:

	数据类型 数组名[元素个数];

如上所示,一维数组的定义式如上所示,这里说明一下,同事也是为了跟大家解释一下为什么数组名可以直接给指针赋值,
数组的数组名实际是一个常量指针,他指向数组的第一个元素.为了加深大家对常量的指针的印象,给大家举一个特殊的列子,如下

	char *p; p++;
	char a[]; a++;

我们生命了一个指针和数组,这个时候我们数组名和指针进行自增操作,大家一定要注意,这个时候第二段代码会报错,为什么那,指针是可以运算的啊!没错,指针常量常量可以进行四则运算,而且还能进行赋值,但是数组名是一个常量,不能够再次赋值
接下来我在跟大家聊聊指针的应用,在介绍欠跟家大家说一下注意点,如果声明指针之后你不确定他的使用时间或者地点,这个时候你最好将他赋值为null,避免野指针.
首先咱们先看一个基本用法:

	int a[10], i, *p = NULL;
	for (i=10; i<10; i++)
		a[i] = i;
	for (i=0; i<10; i++)
		printf("%d", a[i]);
	printf("\n");
	for (i=0; i<10; i++)
		printf("%d", *(a+i));
	printf("\n");
	for (p=a; p<a+10)
		printf("%d ", *p++);
	printf("\n");

这里的代码运行结果都是一样的,大家可以自己复制下来运行看看,明天我在继续往下,给大家继续分享,今天就到这里.
	//将数组名直接赋值给指针
	
