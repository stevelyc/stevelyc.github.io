---
layout: post
title: C++ 运算符重载
category: project
description: 最近在学习C++，写点nlog攒点人品
---
首先咱们说一下为什么会有重载运算符这么个事。因为写的c++不多，暂时没有体会到它有什么好的。只想说真是DT。好，不吐槽了，开始今天的
题。之所以会有重载是因为C++和其他语言为其内置类型提供了一套运算符，然而有些人（原书是我们）希望很方便的（不知道哪来的方便）这些
运算符能很好的支持C++用户自定义运算。于是就有了运算符的重载。

首先跟大家强调一下，有几个运算符是不能重载（wori觉得方便的孩子自行去记吧），而且运算符重载函数要么是类的成员函数，要么是用户定义
类型的参数。这里大家还是好理解的，如果他是全局的，那么可定会影响内置运算符的使用，局部定义定义话会增加维护难度。