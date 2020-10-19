# CSS 入门

:::tip 问题列表

- 什么是 CSS？
- HTML 文档添加 CSS 有哪些方式？
- 谈谈你对 CSS 中层叠、优先级和继承的理解？
- 什么是 CSS 选择器，其优先级如何分？
- 优先级是如何计算的？
- `!important` 有什么作用？
- CSS 简写属性有哪些，需要注意什么？
- 什么是层叠上下文？
- CSS 中哪些属性会影响文档中元素的层叠上下文？
- 什么是块格式化上下文？
- 什么是外边距重叠？

:::

## 什么是 CSS

CSS （Cascading Style Sheets，层叠样式表）是用来控制网页在浏览器中的显示外观的声明式语言。浏览器会根据 CSS 的样式定义将其选定的元素显示为恰当的形式。一条 CSS 的样式定义包括属性和属性值，它们共同决定网页的外观。

一般用它来定义 [HTML 元素](https://developer.mozilla.org/zh-CN/docs/Glossary/%E5%85%83%E7%B4%A0) 的样式，但它也能用于其他标记语言，如 [SVG](https://developer.mozilla.org/zh-CN/docs/Glossary/SVG) 和 [XML](https://developer.mozilla.org/zh-CN/docs/Glossary/XML)

CSS 中的 “C” 表示 “层叠的”，意为多个选择符之间具有特定的优先级。这一点非常重要，因为复杂网站可能会有非常多的 CSS 规则，因此必须规定好这些规则的优先级，以免乱套。

CSS 的语法反映了这个目标，由下面两个部分构建：

- 属性（ property）是一个标识符，用可读的名称来表示其特性。
- 值（value）则描述了浏览器引擎如何处理该特性。每个属性都包含一个有效值的集合，它有正式的语法和语义定义，被浏览器引擎实现。

来分析一下如下代码：

```css
/* p 选择符用来选择页面中的所有 <p> 标签 */
p {
  /* color 属性用来定义文本颜色，这里为黄色 */
  color: yellow;

  /* background-color 属性用来定义元素的背景色，这里为黑色 */
  background-color: black;
}
```

一条 CSS 规则包含一个 [选择符](https://developer.mozilla.org/zh-CN/docs/Glossary/CSS_Selector) 和一组 [属性](https://developer.mozilla.org/en-US/docs/Glossary/property/CSS) 定义。冒号之前是属性，冒号之后是值。不同的 CSS 属性(properties) 对应不同的合法值。

属性可以接受的值远不止这些，不论你是忘记了某个属性，还是想要知道一个属性还能接受什么其它的值。参阅 [CSS 参考](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Reference)

## [如何构建 CSS](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/First_steps/How_CSS_is_structured)

- 外部样式表，是指将 CSS 编写在扩展名为.css 的单独文件中，并从 HTML `<link>` 元素引用它
- 内部样式表，内部样式表是指不使用外部 CSS 文件，而是将 CSS 放在 HTML 文件 `<head>` 标签里的 `<style>` 标签之中
- 内联样式，内联样式表存在于 HTML 元素的 `style` 属性之中。其特点是每个 CSS 表只影响一个元素 (除特除场景，建议少用。如仅允许您编辑 HTML 正文，常被应用在 HTML 电子邮件中)

## [层叠、优先级和继承](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Building_blocks/Cascade_and_inheritance)

- 层叠（cascade）：简单的说，css 规则的顺序很重要；当应用两条同级别的规则到一个元素的时候，写在后面的就是实际使用的规则
- 优先级（specificity）：浏览器是根据优先级来决定当多个规则有不同选择器对应相同的元素的时候需要使用哪个规则
- 继承：在默认情况下，一些 CSS 属性继承当前元素的父元素上设置的值，有些则不继承。这也可能导致一些和期望不同的结果

这三个概念一起来控制 CSS 规则应用于哪个元素

> 在 MDN CSS 属性引用页面你会发现一个技术信息框，通常在规范区域的底部，列举了属性的很多数据信息，包括能否被继承

### `!important`

有一个特殊的 CSS 可以用来覆盖所有上面所有优先级计算，不过需要很小心的使用 — `!important`。用于修改特定属性的值， 能够覆盖普通规则的层叠。

> 覆盖 !important 唯一的办法就是另一个 !important 具有 相同优先级 而且顺序靠后，或者更高优先级。

## [CSS 选择器](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Building_blocks/Selectors)

CSS 中，选择器用来指定网页上我们想要样式化的 HTML 元素

### 选择器列表

如果你有多个使用相同样式的 CSS 选择器，那么这些单独的选择器可以被混编为一个“选择器列表”，这样，规则就可以应用到所有的单个选择器上了。如：

```css
h1 {
  color: blue;
}

.special {
  color: blue;
}

/* 我也可以将它们组合起来，在它们之间加上一个逗号，变为选择器列表。 */

h1,
.special {
  color: blue;
}
```

### CSS 选择器种类

<table class="standard-table"> <thead> <tr> <th scope="col">选择器</th> <th scope="col">示例</th> <th scope="col">学习CSS的教程</th> </tr> </thead> <tbody> <tr> <td><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/Type_selectors">类型选择器</a></td> <td><code>h1 {&nbsp; }</code></td> <td> <a href="https://developer.mozilla.org/zh-CN/docs/user:chrisdavidmills/CSS_Learn/CSS_Selectors/Type_Class_and_ID_Selectors#Type_selectors" >类型选择器</a > </td> </tr> <tr> <td><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/Universal_selectors">通配选择器</a></td> <td><code>* {&nbsp; }</code></td> <td> <a href="https://developer.mozilla.org/zh-CN/docs/user:chrisdavidmills/CSS_Learn/CSS_Selectors/Type_Class_and_ID_Selectors#The_universal_selector" >通配选择器</a > </td> </tr> <tr> <td><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/Class_selectors">类选择器</a></td> <td><code>.box {&nbsp; }</code></td> <td> <a href="https://developer.mozilla.org/zh-CN/docs/user:chrisdavidmills/CSS_Learn/CSS_Selectors/Type_Class_and_ID_Selectors#Class_selectors" >类选择器</a > </td> </tr> <tr> <td><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/ID_selectors">ID选择器</a></td> <td><code>#unique { }</code></td> <td> <a href="https://developer.mozilla.org/zh-CN/docs/user:chrisdavidmills/CSS_Learn/CSS_Selectors/Type_Class_and_ID_Selectors#ID_Selectors" >ID选择器</a > </td> </tr> <tr> <td> <a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/Attribute_selectors">标签属性选择器</a> </td> <td><code>a[title] {&nbsp; }</code></td> <td> <a href="https://developer.mozilla.org/zh-CN/docs/User:chrisdavidmills/CSS_Learn/CSS_Selectors/Attribute_selectors" >标签属性选择器</a > </td> </tr> <tr> <td><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/Pseudo-classes">伪类选择器</a></td> <td><code>p:first-child { }</code></td> <td> <a href="https://developer.mozilla.org/zh-CN/docs/User:chrisdavidmills/CSS_Learn/CSS_Selectors/Pseuso-classes_and_Pseudo-elements#What_is_a_pseudo-class" >伪类</a > </td> </tr> <tr> <td><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/Pseudo-elements">伪元素选择器</a></td> <td><code>p::first-line { }</code></td> <td> <a href="https://developer.mozilla.org/zh-CN/docs/User:chrisdavidmills/CSS_Learn/CSS_Selectors/Pseuso-classes_and_Pseudo-elements#What_is_a_pseudo-element" >伪元素</a > </td> </tr> <tr> <td> <a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/Descendant_combinator">后代选择器</a> </td> <td><code>article p</code></td> <td> <a href="https://developer.mozilla.org/zh-CN/docs/User:chrisdavidmills/CSS_Learn/CSS_Selectors/Combinators#Descendant_Selector" >后代运算符</a > </td> </tr> <tr> <td><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/Child_combinator">子代选择器</a></td> <td><code>article &gt; p</code></td> <td> <a href="https://developer.mozilla.org/zh-CN/docs/User:chrisdavidmills/CSS_Learn/CSS_Selectors/Combinators#Child_combinator" >子代选择器</a > </td> </tr> <tr> <td> <a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/Adjacent_sibling_combinator" >相邻兄弟选择器</a > </td> <td><code>h1 + p</code></td> <td> <a href="https://developer.mozilla.org/zh-CN/docs/User:chrisdavidmills/CSS_Learn/CSS_Selectors/Combinators#Adjacent_sibling" >相邻兄弟</a > </td> </tr> <tr> <td> <a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/General_sibling_combinator" >通用兄弟选择器</a > </td> <td><code>h1 ~ p</code></td> <td> <a href="https://developer.mozilla.org/zh-CN/docs/User:chrisdavidmills/CSS_Learn/CSS_Selectors/Combinators#General_sibling" >通用兄弟</a > </td> </tr> </tbody> </table>

### [优先级是如何计算的](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Specificity)

优先级就是分配给指定的 CSS 声明的一个权重，它由 匹配的选择器中的 每一种选择器类型的 数值 决定。

当同一个元素有多个声明的时候，优先级才会有意义。因为每一个直接作用于元素的 CSS 规则总是会接管/覆盖（take over）该元素从祖先元素继承而来的规则。

> 注意: 文档树中元素的接近度（[Proximity of elements](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Specificity#%E6%97%A0%E8%A7%86DOM%E6%A0%91%E4%B8%AD%E7%9A%84%E8%B7%9D%E7%A6%BB)）对优先级没有影响。

优先级是基于选择器的形式进行计算的，一个选择器的优先级可以说是由四个部分相加 (分量)，可以认为是个十百千 — 四位数的四个位数：

- 千位： 如果声明在 style 的属性（内联样式）则该位得一分。这样的声明没有选择器，所以它得分总是 1000。
- 百位： 选择器中包含 ID 选择器则该位得一分。
- 十位： 选择器中包含类选择器、属性选择器或者伪类则该位得一分。
- 个位：选择器中包含元素、伪元素选择器则该位得一分。

> 注: 通用选择器 (\*)，组合符 (+, >, ~, ' ')，和否定伪类 (:not) 不会影响优先级。

## [简写属性](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Shorthand_properties)

简写属性是可以让你同时设置好几个 CSS 属性值的 CSS 属性。使用简写属性，Web 开发人员可以编写更简洁、更具可读性的样式表，节省时间和精力

CSS 规范定义简写属性的目的在于将那些关于同一主题的常见属性的定义集中在一起。比如 CSS 的 background 属性就是一个简写属性，它可以定义 background-color、background-image、background-repeat 和 background-position 的值。类似地，最常见的字体相关的属性可以使用 font 的简写，盒子（box）各方向的外边距（margin） 可以使用 margin 这个简写。

> 注意，这部分细节比较多，初学者记不住也没关系，随时可以参考文档来查看细节

## [层叠上下文](https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Understanding_z_index/The_stacking_context)

我们假定用户正面向（浏览器）视窗或网页，而 HTML 元素沿着其相对于用户的一条虚构的 z 轴排开，层叠上下文就是对这些 HTML 元素的一个三维构想。众 HTML 元素基于其元素属性按照优先级顺序占据这个空间。

- 层叠上下文可以包含在其他层叠上下文中，并且一起创建一个层叠上下文的层级

- 每个层叠上下文都完全独立于它的兄弟元素：当处理层叠时只考虑子元素

- 每个层叠上下文都是自包含的：当一个元素的内容发生层叠后，该元素将被作为整体在父级层叠上下文中按顺序进行层叠

文档中的层叠上下文由满足以下任意一个条件的元素形成：

- 文档根元素（`<html>`）；

- position 值为 absolute（绝对定位）或 relative（相对定位）且 z-index 值不为 auto 的元素；

- position 值为 fixed（固定定位）或 sticky（粘滞定位）的元素（沾滞定位适配所有移动设备上的浏览器，但老的桌面浏览器不支持）；

- flex (flexbox) 容器的子元素，且 z-index 值不为 auto；

- grid (grid) 容器的子元素，且 z-index 值不为 auto；

- opacity 属性值小于 1 的元素（参见 the specification for opacity）；

- 以下任意属性值不为 none 的元素：

  - transform
  - filter
  - perspective
  - clip-path
  - mask / mask-image / mask-border

- will-change 值设定了任一属性而该属性在 non-initial 值时会创建层叠上下文的元素（参考这篇文章）；

- contain 属性值为 layout、paint 或包含它们其中之一的合成值（比如 contain: strict、contain: content）的元素。

## [块格式化上下文](https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Block_formatting_context)

块格式化上下文（Block Formatting Context，BFC） 是 Web 页面的可视 CSS 渲染的一部分，是块盒子的布局过程发生的区域，也是浮动元素与其他元素交互的区域

下列方式会创建块格式化上下文：

- 根元素（`<html>`）

- 浮动元素（元素的 float 不是 none）

- 绝对定位元素（元素的 position 为 absolute 或 fixed）

- 行内块元素（元素的 display 为 inline-block）

- 表格单元格（元素的 display 为 table-cell，HTML 表格单元格默认为该值）

- 表格标题（元素的 display 为 table-caption，HTML 表格标题默认为该值）匿名表格单元格元素（元素的 display 为 table、table-row、table-row-group、table-header-group、table-footer-group（分别是 HTML table、row、tbody、thead、tfoot 的默认属性）或 inline-table）

- overflow 值不为 visible 的块元素

- display 值为 flow-root 的元素

- contain 值为 layout、content 或 paint 的元素

- 弹性元素（display 为 flex 或 inline-flex 元素的直接子元素）

- 网格元素（display 为 grid 或 inline-grid 元素的直接子元素）

- 多列容器（元素的 column-count 或 column-width 不为 auto，包括 column-count 为 1）

- column-span 为 all 的元素始终会创建一个新的 BFC，即使该元素没有包裹在一个多列容器中（标准变更，Chrome bug）。

## [外边距重叠](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Box_Model/Mastering_margin_collapsing)

块的上外边距(margin-top)和下外边距(margin-bottom)有时合并(折叠)为单个边距，其大小为单个边距的最大值(或如果它们相等，则仅为其中一个)，这种行为称为边距折叠。

有三种情况会形成外边距重叠：

- 相邻的两个元素之间的外边距重叠，除非后一个元素加上 [clear-fix 清除浮动](https://developer.mozilla.org/zh-CN/docs/Web/CSS/clear)
- 没有内容将父元素和后代元素分开
- 空的块级元素

## [图像、媒体和表单元素](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Building_blocks/Images_media_form_elements)

在 CSS 中，某些特殊元素是怎样处理的。图像、其他媒体和表格元素的表现和普通的盒子有些不同，这取决于你使用 CSS 格式化它们的能力。理解什么可能做到，什么不可能做到能够省些力气。

图像和视频被描述为[替换元素](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Replaced_element)，这意味着 CSS 不能影响这些元素的内部布局-仅影响它们在页面上于其他元素中的位置。另外，替换元素在成为网格或者弹性布局的一部分时，有不同的默认行为。

对于表单的样式，推荐阅读[样式化 HTML 表单](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Styling_HTML_forms)

## 推荐阅读

- [组织 CSS](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Building_blocks/Organizing)
- [CSS 构建](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Building_blocks/Organizing)
- [CSS 参考](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Reference)
- [CSS 如何运行](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/First_steps/CSS%E5%A6%82%E4%BD%95%E8%BF%90%E8%A1%8C)
- [@规则](https://developer.mozilla.org/zh-CN/docs/Web/CSS/At-rule)
- [颜色](https://developer.mozilla.org/zh-CN/docs/Web/CSS/color_value)
- [字体大小](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-size)
- [动画](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Animations)
- [CSS 属性值定义语法](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Value_definition_syntax)
- [CSS 单位与取值类型](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Value_definition_syntax)
- [CSS 的值与单位](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Building_blocks/Values_and_units)
- [CSS 常见问题](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Howto)
