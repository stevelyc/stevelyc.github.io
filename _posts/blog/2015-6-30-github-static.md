---
layout: post
title: 漫谈C－关键字 static
description: C系列中一个经典的关键字，也是面试题中经常出现的。
category: blog
---

最近忙着iOS的面试，免不了刷一下网上的题（你懂的），当我第一次刷到static的时候我都惊呆了。md，居然有这么的用法，于是自己翻阅了两本比较经典的C语言著作找比较适合的答案，希望对大家以后的工作有所帮助。

首先咱们先吧网上的贴出来：
<ul>
	<li>函数体内 static 变量的作用范围为该函数体，不同于 auto 变量，该变量的内存只被分配一次， 
因此其值在下次调用时仍维持上次的值；</li>
	<li>在模块内的 static 全局变量可以被模块内所用函数访问，但不能被模块外其它函数访问</li>
	<li>在模块内的 static 函数只可被这一模块内的其它函数调用，这个函数的使用范围被限制在声明 
它的模块内</li>
	<li>在类中的 static 成员变量属于整个类所拥有，对类的所有对象只有一份拷贝（c++）</li>
	<li>在类中的 static 成员函数属于整个类所拥有，这个函数不接收 this 指针，因而只能访问类的static 成员变量（c++）</li>
</ul>

再看了上面的一长串介绍之后，你心中或许会默默说一句，这都是什么鬼，我不记得static有这么复杂的用法啊。没错，static的用法你的确没有这么复杂，但是要看你怎么去理解。

首先咱们来看下c语言之父在《c语言编程设计》中对static的介绍，（书不在身边，回头有时间补上，不过我肯定说的很简单）

而我在《C与指针》上看到说法让我眼前为之一亮。首先他提出一个概念，叫做标示符的链接属性，请注意，这里说的不是变量

标示符的链接属性决定如何处理在不同文件中出现的标示符。标示符的作用域与他的链接属性相关，当然这两个属性并不相同。

static关键字用于修改变量的的存储类型，从自动变量修改为静态变量，但变量的链接和作用域不受影响。至于在同一个文件中，static的作用就是将变量转变一个静态变量，这个就没什么说的了。

static通过改变链接属性，改变了当标示符出现文件中可以采取何种方式进行处理。例如，当你创建test1.c，test2.c两个c文件并且同时创建一个整形变量a，此时你创建一个main.c文件并引用这两个文件，此时在main.c中访问变量a，会发什么？然后你修改其中一个文件中，在定义变量的前面加上一个static又会出现什么情况。亲自动手做一下。（函数的效果是一样的）

扩展：
在《c与指针》中，链接属性决定如何处理在不同文件中出现的标识符。标识符的作用域和它的链接属性有关，但这两者属性并不相同。

链接属性一共三种－－external（外部）， internal（内部）和none（无）。没有链接属性标识符总是被当作单独的个体，也就是说该标识符的多个声明被当作独立不同的实体。属于internal链接属性的标识符在同一个源文件内的所有生命中都指同一个实体，但位于不同源文件的多个声明则分属不同的实体。最后，属于external链接属性的标识符无论声明多少次，位于几个源文件都表示都一个实体。