# CSS 布局

:::tip 问题列表

- 什么是盒模型？

:::

## 盒模型

当对一个文档进行布局（lay out）的时候，浏览器的渲染引擎会根据标准之一的 CSS 基础框盒模型（CSS basic box model），将所有元素表示为一个个矩形的盒子（box）。CSS 决定这些盒子的大小、位置以及属性（例如颜色、背景、边框尺寸…）。

### 什么是 CSS 盒模型

完整的 CSS 盒模型应用于块级盒子，内联盒子只使用盒模型中定义的部分内容。模型定义了盒的每个部分 —— margin, border, padding, and content —— 合在一起就可以创建我们在页面上看到的内容。为了增加一些额外的复杂性，有一个标准的和替代（IE）的盒模型。

CSS 中组成一个块级盒子需要:

- Content box: 这个区域是用来显示内容，大小可以通过设置 [width](https://developer.mozilla.org/zh-CN/docs/Web/CSS/width) 和 [height]()
- Padding box: 包围在内容区域外部的空白区域； 大小通过 padding 相关属性设置
- Border box: 边框盒包裹内容和内边距。大小通过 border 相关属性设置
- Margin box: 这是最外面的区域，是盒子和其他元素之间的空白区域。大小通过 margin 相关属性设置

### 块级盒子（Block box） 和 内联盒子（Inline box）

在 CSS 中我们广泛地使用两种“盒子” —— 块级盒子 (block box) 和 内联盒子 (inline box)。这两种盒子会在页面流（page flow）和元素之间的关系方面表现出不同的行为:

一个被定义成块级的（block）盒子会表现出以下行为:

- 盒子会在内联的方向上扩展并占据父容器在该方向上的所有可用空间，在绝大数情况下意味着盒子会和父容器一样宽
- 每个盒子都会换行
- `width` 和 `height` 属性可以发挥作用
- 内边距（padding）, 外边距（margin） 和 边框（border） 会将其他元素从当前盒子周围“推开”

除非特殊指定，诸如标题(`<h1>`等)和段落(`<p>`)默认情况下都是块级的盒子

如果一个盒子对外显示为 inline，那么他的行为如下:

- 盒子不会产生换行
- `width` 和 `height` 属性将不起作用
- 垂直方向的内边距、外边距以及边框会被应用但是不会把其他处于 `inline` 状态的盒子推开
- 水平方向的内边距、外边距以及边框会被应用而且也会把其他处于 `inline` 状态的盒子推开

用做链接的 `<a>` 元素、 `<span>`、 `<em>` 以及 `<strong>` 都是默认处于 `inline` 状态的。

### 内部和外部显示类型

我们通过对盒子 [display](https://developer.mozilla.org/zh-CN/docs/Web/CSS/display) 属性的设置，比如 inline 或者 block ，来控制盒子的外部显示类型。

盒模型还有内部显示类型，它决定了盒子内部元素是如何布局的。默认情况下是按照 [正常文档流](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Normal_Flow) 布局，也意味着它们和其他块元素以及内联元素一样(如上所述)

我们可以通过使用类似 `flex` 的 `display` 属性值来更改内部显示类型。如果设置 `display: flex`，在一个元素上，外部显示类型是 `block`，但是内部显示类型修改为 `flex`。 该盒子的所有直接子元素都会成为 `flex` 元素，会根据 [弹性盒子（Flexbox ）](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Flexbox) 规则进行布局，稍后您将了解这些规则。

现在需要记住的是， `display` 属性可以改变盒子的外部显示类型是块级还是内联，这将会改变它与布局中其他元素的显示方式

## 包含块

一个元素的尺寸和位置经常受其包含块(containing block)的影响。大多数情况下，包含块就是这个元素最近的祖先块元素的内容区，但也不是总是这样。在本文中，我们来过一遍确定包含块的所有因素。

元素的尺寸及位置，常常会受它的包含块所影响。对于一些属性，例如 width, height, padding, margin，绝对定位元素的偏移值 （比如 position 被设置为 absolute 或 fixed），当我们对其赋予百分比值时，这些值的计算值，就是通过元素的包含块计算得来。

[更多](https://developer.mozilla.org/zh-CN/docs/Web/CSS/All_About_The_Containing_Block)

## CSS 布局模式

布局是一种基于盒子与其兄弟和祖辈盒子的交互方式来确定盒子的位置和大小的算法。有以下几种形式：

- 块布局：用来布置文件。块布局包含以文档为中心的功能，例如[浮动](https://developer.mozilla.org/en-US/docs/Web/CSS/float)元素或将其放置在[多列](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Columns/Using_multi-column_layouts)上的功能。
- 行内布局：用来布置文本。
- 表格布局：用来布置表格。
- 定位布局：用来对那些与其他元素无交互的定位元素进行布置 。
- [弹性盒子布局](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Flexible_Box_Layout/Using_CSS_flexible_boxes)：用来布置那些可以顺利调整大小的复杂页面。
- [网格布局](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Grid_Layout)：用来布置那些与一个固定网格相关的元素。

## 推荐阅读

- [CSS 布局](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/CSS_layout)
