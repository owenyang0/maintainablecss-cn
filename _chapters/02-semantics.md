---
layout: chapter
title: 语义化(Semantics)
section: Background
permalink: /chapters/semantics/
description: Why naming something based on what it is, instead of how it looks or behaves is a cornerstone of writing well architected and maintainable CSS code.
---

**概述:** 基于这 *是* 什么命名，而不是基于它 *像* 什么或 *能做* 什么命名。

## 长版本解释

语义化(semantic)的 HTML 不仅仅关乎我们所使用的元素&mdash;&mdash;你当然知道一个链接应该使用 `<a>` 标签，表格数据应该使用 `<table>` 标签，段落使用 `<p>` 等等。

更重要的是，它和我们所添加的类名(class names)和IDs有关。而类名和IDs为 CSS 和 JavaScript提供额外的机制，让我们更容易去操作和增强 HTML 元素。

很容易出现不经过思考而随意添加类名的场景，但现实中命名却又特别重要。


> &ldquo;在计算机科学领域，有两大难题，如何让缓存失效(cache invalidation)和如何给各种东西命名。&rdquo;
<br>&mdash; <cite>Phil Karlton, 网景架构师</cite>

这是由于人只是擅长和人沟通，却不太能理解简短的，不具有语义化的抽象概念。

## 类名好坏对比

试着找出非语义化和语义化类名的区别...

	<!-- 不好 -->
	<div class="red pull-left">
	<div class="grid row">
	<div class="col-xs-4">

这里完全看不出这段 HTML 代码要表达 *什么*。你 *可能* 会说它 *看起来* 怎样（比如应该在小屏幕还是大屏幕上），但也就仅此而已。

	<!-- 好 -->
	<div class="header">
	<div class="basket">
	<div class="product">
	<div class="searchResults">

这段代码就正是我所推崇的。我很清楚地知道这段 HTML 代表着什么。虽然我不知道它看起来应该是怎样的，但我并不在乎，这是 CSS 存在的价值。而语义化的类名对 HTML 和 CSS 甚至 JS 都很有意义。

所以，*为什么* 我们应该使用语义化的类名呢？

## 因为更容易理解

若使用语义化类名，不论你是在修改 HTML 或者 CSS，你都清楚你将造成的影响。而使用视觉化类名(visual class names)的方式，你不得不在每一个元素上写很多类名，最终你可能只是对这些类名有一个模糊的理解，而不清楚它真正的意图是什么。而且，视觉化类名非常难以维护。


## 因为要构建响应式站点

一般说来，不同的视图(viewport)会有不同的样式。比如，你可能需要在大屏上浮动(float)一个元素，在小屏不浮动。如果你有一个叫 `.clearfix` 的类名来清理浮动，但在小屏上的效果却和类名不一样，这看起来会不会让人困惑呢？

使用语义化的类名，你就会基于 mediea queries 去编写样式，这会让 CSS 更易维护。


## 因为更容易查找

如果一个元素是基于其外在表像命名，比如 `.red`, `.clearfix`, 和 `.pull-left` 等，那么这些类名就会像垃圾一样散落在代码库的任何地方&mdash;&mdash;当你搜索一段特定的 HTML 代码的时候，类名不会起任何作用。

换句话说，如果你的类名足够语义化，搜索特定代码片段是很简单的事。更常见的是，当你从头搜索你的 HTML(想像一下浏览器上的审查元素)去找类名的时候，查找唯一的 CSS 选择器肯定会快很多。


## 因为不想做无故的回归测试

如果你使用描述性的，非语义化的类名，那么当你修改其中一个类名的时候，样式的改变会影响每一个使用这个类名的元素。基于你使用 CSS 的经验，你能保证你的修改不会在其他地方产生不可预知的问题吗？

语义化的类名是唯一的，所以当你编辑其中一个的时候，你 *能* 自信地说，你的修改只会影响你想要改变的那个模块，维护起来更简单。


## 因为不用再恐惧更新代码

和前一个有关回归测试的那一点有关，当你对修改的代码不够自信的时候，你很有可能会造成 BUG 接着便会由于害怕出错而不再碰那些代码。更可怕的是会造成恶性循环，写很多冗余代码，最后变得越来越不具有可维护性。


## 因为有助于自动化测试

自动化功能测试需要定位特定的元素，与其进化交互（输入文本，点击按钮、链接等等），基于这些操作进行相关校验。

若你的 HTML 通篇都使用描述性的类名，那么你将不会有一个可靠方式去定位一个特定的元素，更惶论与其交互了。


## 因为为JavaScript提供了有意义的接口

就像和自动化测试一样，语义化的类名对JavaScript来说同样有意义。描述性的类名不具有可靠性，不可用于定位相应的模块或组件。


## 因为常规维护的担心

若你是基于该元素是什么而命名，你就不必再次修改 HTML 的类名。如，heading 始终是 heading, 你不用管它变成什么样子。

样式可能会改变，但你只需要改变你的 CSS。这在另一个方面来说，实际是上松耦合从而提高了可维护性。


## 因为非语义类名调试困难

当你调试(debug)一个元素的时候，会出现很多类似的 CSS 选择器，增加了调试的难度。


## 因为标准推荐使用

HTML5 的规范在 [3.2.5.7](https://www.w3.org/TR/html5/dom.html#classes) 里有说，使用类名属性。

> "[...] 更鼓励使用能描述内容本质的类名，而不是那些只是描述其外在表像的值。"


## 因为能带来性能的提升

这是一个 *非常* 小的优势，因为当你一个元素只有一个类名的时候，你的整个 HTML 代码体积都会更小。而使用描述性的类名，每个元素有无数个类名，结果自然与前者不一样。


## 因为和重用规则有关

如果你没有使用语义化类名，你有可能会是误解了重用(reuse)的概念，而误用重用。阅读下章，获得更多。

<!--## Why? Because visual class names might declare the same property!

It's likely that several different utility classes could refer to the same property meaning order matters and performance degrades.

Think of an example of this.
-->

## 最后想想语义化

语义化的类名是 *MaintainableCSS* 的基石，没有它，一切都没意义。所以，基于是什么命名，其他所有都将受益。
