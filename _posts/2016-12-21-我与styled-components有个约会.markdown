---
layout:     post
title:      "我与styled-components有个约会"
date:       2016-12-21 12:00:00
author:     "zhongjie-chen"
header-img: "img/post-bg-05.jpg"
---

> 转载请说明出处 [原文](http://zhongjie-chen.github.io/blog/2016/12/21/%E6%88%91%E4%B8%8Estyled-components%E6%9C%89%E4%B8%AA%E7%BA%A6%E4%BC%9A/)，本文章为翻译加个人评价 [译文](https://medium.com/@jamiedixon/styled-components-production-patterns-c22e24b1d896#.9q4p5gejo)

[styled-components](https://styled-components.com/)是一个能够让你在React或React-native组件里面编写css的库，它的写法可以让css混合在js里面。

如果你不熟悉[styled-components](https://styled-components.com/)可以去我们的官网去查看。

***

以下是styled-component基本写法的组件：

![](/blog/img/sc_1.png)
*图片来自[ https://styled-components.com/]( https://styled-components.com/)*

最近一段时间我们使用styled-components应用到我们的项目中，我想写一些我们的使用心得。

# 更少的Styles

因为`styled-components`允许我们以函数的形式表现css的值,我们可以切换不同样式基于传入组件的`props`值，而不是像经典的写法添加新的类到`HTML`中。

这可以减少很大的代码量。当我们一开始将`CSS`转换成`styled-components`的形式,我们看到了戏剧性的改变。

![](/blog/img/sc_2.png)
*A portion of our original CSS*

![](/blog/img/sc_3.png)
*The same styles converted to a styled-components component.*

# 更简洁的JSX

如果你像我一样,你会发现你的`JSX`散落着`< div >和< span >`,你将会很高兴的知道styled-components会让你的默认样式标签更加具有`语意化`。

![](/blog/img/sc_4.png)
*Original JSX with class hooks for styling*

![](/blog/img/sc_5.png)
*After converting to styled-components No more className! and look at those semantic tags.*

我肯定你的`JSX`已经看起来像第二个例子:P,但如果还没有,`styled-components`可以帮助你成功到达该境界。

# 合成Styles

这是我最喜欢的功能之一。一旦你创建了一个`styled component`可以很轻松地组合成一个新的`styled component`。

这是因为`styled-components`是通过组件的形式,而不是`DOM`元素。

![](/blog/img/sc_6.png)
*Here we compose Message into two new components, Success and Danger.*

# Prop过滤

自从`React15.2.0`,未知的`DOM`元素上的属性会报一个`unknown-prop`警告。这意味着,如果我们做``< div foo = " foo " >``我们会得到一个警告,``“foo”``不是一个已知的属性。

有时我们有需要接受`props`包含`DOM`的`props`并将其传递到`DOM`元素内。很难做到通过手动档指定每一个`DOM`属性，所以我们最终以`spreading props`的方式在这些类型的组件:``< div {…props} >``。

为了避免上述`unknown-prop`警告我们开始过滤`props`不是有效的`DOM props`。因垂死听的是`styled-components`已经在内部很好得解决了这个问题,我们避免去做有效属性的白名单。

![](/blog/img/sc_7.png)
*We had a function to filter DOM props that we could use to ensure only valid DOM props were passed to things like  &gt;span&lt;*

![](/blog/img/sc_8.png)
*Using styled-components we get this whitelist for free, even if we don’t need any styles!*

以上是我们自从开始使用`styled-components`得出来的好处，随着使用时间的推移我相信将会有更多好处。

非常感谢[Max Stoiber](https://twitter.com/mxstbr)和[Glen Maddern](https://twitter.com/glenmaddern)开发的`styled-components`。

***

# 个人看法
