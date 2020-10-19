# CSS 布局

:::tip 问题列表

- 什么是盒模型？
- CSS 有哪些定位规则？
- 什么是溢出，以及如何控制它？
- 使用 CSS 为页面中元素设定尺寸的方法？
- 什么是元素尺寸、固有尺寸？
- CSS 有哪些布局模式？
- 什么是弹性盒布局及其优势？

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

## CSS 定位规则

一旦生成了盒子以后，CSS 引擎就需要定位它们以完成布局。下面是定位盒子时所使用的规则：

- 普通流：按照次序依次定位每个盒子

  - 当 CSS 的 position 属性为 static 或 relative，并且 float 为 none 时，其布局方式为普通流。

- 浮动：将盒子从普通流中单独拎出来，将其放到外层盒子的某一边

  - 一个盒子的 float 值不为 none，并且其 position 为 static 或 relative 时，该盒子为浮动定位

- 绝对定位：按照绝对位置来定位盒子，其位置根据盒子的包含元素所建立的绝对坐标系来计算，因此绝对定位元素有可能会覆盖其他元素

  - 如果元素的 position 为 absolute 或 fixed，该元素为绝对定位

## [溢出](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Building_blocks/Overflowing_content)

CSS 中万物皆盒，因此我们可以通过给 width 和 height（或者 inline-size 和 block-size）赋值的方式来约束盒子的尺寸。溢出是在你往盒子里面塞太多东西的时候发生的，所以盒子里面的东西也不会老老实实待着。

[overflow](https://developer.mozilla.org/zh-CN/docs/Web/CSS/overflow) 属性是你控制一个元素溢出的方式，它告诉浏览器你想怎样处理溢出。overflow 的默认值为 visible，这就是我们的内容溢出的时候，我们在默认情况下看到它们的原因。

## 在 CSS 中调整大小

在受 CSS 设置影响之前，HTML 元素有其原始的尺寸。一个直观的例子就是图像。一副图像的长和宽由这个图像文件自身确定。这个尺寸就是固有尺寸。

我们可以给元素一个具体的 width 和 height 值, 然后不论我们放什么内容进去它都是该尺寸。 （当给元素指定尺寸（然后其内容需要适合该尺寸）时，我们将其称为外部尺寸）

除了让万物都有一个确定的大小以外，我们可以让 CSS 给定一个元素的最大或最小尺寸。如果你有一个包含了变化容量的内容的盒子，而且你总是想让它至少有个确定的高度，你应该给它设置一个 min-height 属性。max-width 的常见用法为，在没有足够空间以原有宽度展示图像时，让图像缩小，同时确保它们不会比这一宽度大。

## CSS 布局模式

布局是一种基于盒子与其兄弟和祖辈盒子的交互方式来确定盒子的位置和大小的算法。有以下几种形式：

- 块布局：用来布置文件。块布局包含以文档为中心的功能，例如[浮动](https://developer.mozilla.org/en-US/docs/Web/CSS/float)元素或将其放置在[多列](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Columns/Using_multi-column_layouts)上的功能。
- 行内布局：用来布置文本。
- 表格布局：用来布置表格。
- 定位布局：用来对那些与其他元素无交互的定位元素进行布置 。
- [弹性盒子布局](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Flexible_Box_Layout/Using_CSS_flexible_boxes)：用来布置那些可以顺利调整大小的复杂页面。
- [网格布局](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Grid_Layout)：用来布置那些与一个固定网格相关的元素。

## [弹性盒布局](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Flexible_Box_Layout/Using_CSS_flexible_boxes)

CSS3 弹性盒子(Flexible Box 或 Flexbox)，是一种用于在页面上布置元素的布局模式。对于许多应用程序，弹性盒子模型提供了对块模型的改进，因为它不使用浮动，flex 容器的边缘也不会与其内容的边缘折叠。

![](../assets/img/flexbox.png)

- 弹性容器(Flex container)
  包含着弹性项目的父元素。通过设置 display 属性的值为 flex 或 inline-flex 来定义弹性容器。

- 弹性项目(Flex item)
  弹性容器的每个子元素都称为弹性项目。弹性容器直接包含的文本将被包覆成匿名弹性单元。

- 轴(Axis)
  每个弹性框布局包含两个轴。弹性项目沿其依次排列的那根轴称为主轴(main axis)。垂直于主轴的那根轴称为侧轴(cross axis)。

  - flex-direction 确立主轴。
  - justify-content 定义了在当前行上，弹性项目沿主轴如何排布。
  - align-items 定义了在当前行上，弹性项目沿侧轴默认如何排布。
  - align-self 定义了单个弹性项目在侧轴上应当如何对齐，这个定义会覆盖由 align-items 所确立的默认值。

- 方向(Direction)
  弹性容器的主轴起点(main start)/主轴终点(main end)和侧轴起点(cross start)/侧轴终点(cross end)描述了弹性项目排布的起点与终点。它们具体取决于弹性容器的主轴与侧轴中，由 writing-mode 确立的方向（从左到右、从右到左，等等）。

  - order 属性将元素与序号关联起来，以此决定哪些元素先出现。
  - flex-flow 属性是 flex-direction 和 flex-wrap 属性的简写，决定弹性项目如何排布。

- 行(Line)
  根据 flex-wrap 属性，弹性项目可以排布在单个行或者多个行中。此属性控制侧轴的方向和新行排列的方向。

- 尺寸(Dimension)
  根据弹性容器的主轴与侧轴，弹性项目的宽和高中，对应主轴的称为主轴尺寸(main size) ，对应侧轴的称为 侧轴尺寸(cross size)。

  - min-height 与 min-width 属性初始值将为 0。
  - flex 属性是 flex-grow、flex-shrink 和 flex-basis 属性的简写，描述弹性项目的整体的伸缩性。

## 推荐阅读

- [CSS 基础框盒模型](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Box_Model)
- [CSS 布局](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/CSS_layout)
- [视觉格式化模型](https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Visual_formatting_model)
- [使用 CSS 弹性盒子](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Flexible_Box_Layout/Using_CSS_flexible_boxes)
- [CSS 布局手册](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Layout_cookbook)
