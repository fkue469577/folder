# 简介

从本章开始，我将陆续（翻译、转载、整理）http://dmitrysoshnikov.com/网站关于ECMAScript标标准理解的好文。

本章我们要讲解的是ECMAScript标准里的执行上下文和相关可执行代码的各种类型。

```
原始作者：Dmitry A. Soshnikov
原始发布: 2009-06-26
俄文原文：http://dmitrysoshnikov.com/ecmascript/ru-chapter-1-execution-contexts/

英文翻译：Dmitry A. Soshnikov.
发布时间：2010-03-11
英文翻译：http://dmitrysoshnikov.com/ecmascript/chapter-1-execution-contexts/

本文参考了博客园justinw的中文翻译，做了一些错误修正，感谢译者。
```

# 定义

每次当控制器转到ECMAScript可执行代码的时候，即会进入到一个执行上下文。执行上下文(简称-EC)是ECMA-262标准里的一个抽象概念，用于同可执行代码(executable code)概念进行区分。

标准规范没有从技术实现的角度定义EC的准确类型和结构，这应该是具体实现ECMAScript引擎时要考虑的问题。

活动的执行上下文组在逻辑上组成一个堆栈。堆栈底部永远都是全局上下文(global context)，而顶部就是当前(活动的)执行上下文。堆栈在EC类型进入和退出上下文的时候被修改（推入或弹出）。

