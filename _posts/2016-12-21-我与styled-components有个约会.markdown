---
layout:     post
title:      "我与styled-components有个约会"
date:       2016-12-21 12:00:00
author:     "zhongjie-chen"
header-img: "img/post-bg-05.jpg"
---

# 我与styled-components

> 转载请说明出处 [原文]()

> 本文章为翻译加个人评价 [译文](https://medium.com/@jamiedixon/styled-components-production-patterns-c22e24b1d896#.9q4p5gejo)

[styled-components](https://styled-components.com/)是一个能够让你在React或React-native组件里面编写css的库，它的写法可以让css混合在js里面。

如果你不熟悉[styled-components](https://styled-components.com/)可以去我们的官网去查看。

以下是styled-component基本写法的组件：

![](../img/sc_1.png)

最近一段时间我们使用styled-components应用到我们的项目中，我想写一些我们的使用心得。

# 更少的Styles

因为styled-components允许我们以函数的形式表现css的值,我们可以切换不同样式基于传入组件的props值，而不是像经典的写法添加新的类到HTML中。

这可以减少很大的代码量。当我们一开始将CSS转换成styled-components的形式,我们看到了戏剧性的改变。

![](../img/sc_2.png)

![](../img/sc_3.png)

# 更简洁的JSX

如果你像我一样,你会发现你的JSX散落着< div >和< span >,你将会很高兴的知道styled-components会让你的默认样式标签更加具有语意化。

![](../img/sc_4.png)

![](../img/sc_5.png)

我肯定你的JSX已经看起来像第二个例子:P,但如果还没有,styled-components可以帮助你成功到达该境界。

# 合成Styles

这是我最喜欢的功能之一。一旦你创建了一个styled component可以很轻松地组合成一个新的styled component。

这是因为styled-components是通过组件的形式,而不是DOM元素。

![](../img/sc_6.png)

# Prop过滤

自从React15.2.0,未知的DOM元素上的属性会报一个unknown-prop警告。这意味着,如果我们做< div foo = " foo " >我们会得到一个警告,“foo”不是一个已知的属性。

有时我们有需要接受props包含DOM的props并将其传递到DOM元素内。很难做到通过手动档指定每一个DOM属性，所以我们最终以spreading props的方式在这些类型的组件:< div {…props} >。

为了避免上述unknown-prop警告我们开始过滤props不是有效的DOM props。因垂死听的是styled-components已经在内部很好得解决了这个问题,我们避免去做有效属性的白名单。

![](../img/sc_7.png)

![](../img/sc_8.png)

以上是我们自从开始使用styled-components得出来的好处，随着使用时间的推移我相信将会有更多好处。

非常感谢Max Stoiber和Glen Maddern开发的styled-components。
