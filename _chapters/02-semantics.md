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

所以，*为什么* 其他人应该使用语义化的类名呢？

## 因为更容易理解

若使用语义化类名，不论你是在修改 HTML 或者 CSS，你都清楚你将造成的影响。而使用视觉化类名(visual class names)的方式，你不得不在每一个元素上写很多类名，最终你可能只是对这些类名有一个模糊的理解，而不清楚它真正的意图是什么。而且，视觉化类名非常难以维护。

## Because we are building responsive websites.

Styles often need changing based on viewport size. For example, you might float elements on big screens and not on small screens. So if you have a class called `clearfix` but you don't clear on small screens, then you now have misleading code.

If you use semantic class names, then you can style them differently based on media queries making it easier to maintain.

## Because semantic class names are easier to find.

If an element has classes based on how it looks such as `.red`, `clearfix` and `.pull-left`, then these classes will be scattered all over the codebase&mdash;so if you’re trying to hunt for a particular piece of HTML, the class name is not going to help you.

On the other hand, if your class names are semantic, a search will find the HTML in question. Or more typically, if you're beginning your search via the HTML (think: inspecting an element) then finding unique CSS selectors based on the class name will be far easier.

## Because you don't want unexpected regression.

If you have utility non-semantic classes that describe the look then when you edit one of these classes, they will propagate to every single element with that class. Knowing CSS as you do, do you feel comfortable that the propagation didn't cause unexpected problems elsewhere?

Semantic class names are unique, so when editing one, you *can* feel comfortable that your change only applies to the module in question as you intended, making maintainance easier.

## Because you don't want to be afraid to update code.

Directly linked with the previous point about regression, when you don't feel comfortable touching code, you end up causing problems or being afraid to touch it at all. Therefore you end up with redundant code, increasing maintainance issues.

## Because it helps automated functional testing.

Automated functional tests work by searching for particular elements, interacting with them (typing in text, clicking buttons and links etc) and verifying based on that.

If you have visual class names all over the HTML, then there is no reliable way to target particular elements and act upon them.

## Because it provides meaningful hooks for Javascript to enhance.

Just like these hooks help automated testing, they are also useful to enhance behaviour with Javascript. Visual class names can't be used as a reliable way to target modules or components.

## Because of general maintainance concerns.

If you name something based on what it is, you won't have to touch the HTML again i.e. a heading is always a heading, no matter what it *looks* like.

The styling might change but you only have to update the CSS. This is otherwise known as Loose Coupling and this improves maintainability.

## Because utility classes increase noise when debugging.

When debugging an element, there will be several applicable CSS selectors making it noisey to debug.

## Because the standards recommend it.

On using the class attribute, HTML5 specs say in 3.2.3.7:

> "[...] authors are encouraged to use values that describe the nature of the content, rather than values that describe the desired presentation of the content."

## Because you get a performance bump.

This is a *very* small benefit but when you have one class name per element, you end up with smaller HTML. With visual classes you end up with multiple class names per element and that can add up.

## Because it adheres to the reuse rule.

If you don't use semantic class names, then you will likely be breaking the rules of reuse. Read the next chapter to find out more.

<!--## Why? Because visual class names might declare the same property!

It's likely that several different utility classes could refer to the same property meaning order matters and performance degrades.

Think of an example of this.
-->

## Final thoughts about semantics

Semantic class names are a corner stone of *MaintainableCSS*. Without this, everything else makes little sense. So name something based on what it is and everything else follows.
