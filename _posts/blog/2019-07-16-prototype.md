---
layout: post
title: new 构造函数都做了一些什么？
categories: [JavaScript]
description: 发现，探索 web 优质文章
keywords: JavaScript 
---

# 原型和原型对象
`prototype` 和 `__proto__` 还有 `constructor`，总觉得有些拗口，分不清，记录我的理解

## 对象和函数

在 `JavaScript` 一切皆对象，函数也是对象。但是对于`prototype` 和 `__proto__` 还有 `constructor` 我一直都不太明白，今天要好好理一下。

函数是对象，那函数是怎么指向对象的呢？想了一番，然后在控制台里面打了一下，或许这事最好的理解方式吧

每一个函数都有一个 `prototype` 他指向了函数的原型。

每一个函数的原型都有一个 `constructor` 属性，这个实现指向函数本身。

每一个函数的原型都有一个 `__proto__` 属性，这个实现指向了函数原型的原型（即对象）对应前面的那句话函数也是对象。

![]({{ site.url }}/images/pages/004.png)

如果直接是对象的，他就没有 `prototype` 属性，他的 `__proto__` 属性，指向他的原型（即对象），他的 `constructor` 属性，这个实现指向函数本身

![]({{ site.url }}/images/pages/005.png)

到这里我们理清楚了函数和对象的关系，`prototype` 和 `__proto__` 还有 `constructor` 分别是谁的属性，干什么的应该也差不多了。

## 说一说 `new` 构造函数都发生些什么

理清楚 `prototype` 和 `__proto__` 还有 `constructor` 是为了更好的理解构造函数准备。在一次模拟面试中，朋友问我通过 `new` 关键字调用函数都发生了一些什么？
我每一次都是临时背答案，那一次我背不出来了。然后我就决定自己去理解，而是不背答案，应付。

关于构造函数的概念，简单介绍，函数声明的时候首字母大写（为了区分普通函数和构造函数），调用的时候通过 `new` 关键字，否则和普通函数一样，没有区别。


`prototype` 和 `__proto__` 还有 `constructor`

![]({{ site.url }}/images/pages/006.png)

如果是构造函数调用的话

![]({{ site.url }}/images/pages/007.png)

 通过打印 `this` 发现他指向了函数的原型，推导出 `this.__proto__=Persion.prototype` 
 
 在顺便说一句 构造函数，实例，和原型对象的关系
 
![]({{ site.url }}/images/pages/008.png)

