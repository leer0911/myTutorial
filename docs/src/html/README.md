# HTML 介绍

:::tip

- 什么是 HTML？
- HTML 元素有哪些类别？
- 什么是块级元素、内联元素，它们分别有哪些？
- 什么是 HTML 标签？
- 如何给 `<a>` 添加超链接？
- 如何禁用 `<input>`?
- 如何在 HTML 页面中显示 <, >,",' 和 & 等特殊字符？
- 什么是 HTML 注释？

:::

## 什么是 HTML

HTML (HyperText Markup Language) 不是一门编程语言，而是一种用来告知浏览器如何组织页面的标记语言。

下面来分析一下这段代码

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <title>我的测试站点</title>
  </head>
  <body>
    <p>这是我的页面</p>
  </body>
</html>
```

- `<!DOCTYPE html>` 用于声明文档类型
- [`<html>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/html) 这个元素包裹了整个完整的页面，是一个根元素。
- [`<head>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/head) 这个元素是一个容器，它包含了所有你想包含在 HTML 页面中但不想在 HTML 页面中显示的内容。这些内容包括你想在搜索结果中出现的关键字和页面描述，CSS 样式，字符集声明等等
- [`<meta charset="utf-8">`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meta) 这个元素设置文档使用 utf-8 字符集编码，utf-8 字符集包含了人类大部分的文字。
- [`<title>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/title) 设置页面标题，出现在浏览器标签上，当你标记/收藏页面时它可用来描述页面。
- [`<body>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/body) 包含了你访问页面时所有显示在页面上的内容，文本，图片，音频，游戏等等

## HTML 元素

一个典型的元素包括一个具有一些属性的开始标签，中间的文本内容和一个结束标签。

```html
<p>我的猫咪脾气爆:)</p>
```

如上，开始标签、结束标签与内容相结合，便是一个完整的元素。

### HTML 元素类别

在 HTML 中有两种你需要知道的重要元素类别，块级元素和内联元素。

- 块级元素在页面中以块的形式展现 —— 相对于其前面的内容它会出现在新的一行，其后的内容也会被挤到下一行展现。块级元素通常用于展示页面上结构化的内容，例如段落、列表、导航菜单、页脚等等。一个以 block 形式展现的块级元素不会被嵌套进内联元素中，但可以嵌套在其它块级元素中。

- 内联元素通常出现在块级元素中并环绕文档内容的一小部分，而不是一整个段落或者一组内容。内联元素不会导致文本换行：它通常出现在一堆文字之间例如超链接元素 `<a>` 或者强调元素 `<em>` 和 `<strong>`。

> 元素和标签不是同一种概念。源代码中的标签用来标识元素的开始或结束，而元素是文档对象模型（[DOM](https://developer.mozilla.org/zh-CN/docs/Glossary/DOM)）中的一部分，文档对象模型会被浏览器渲染、展示为页面。(该部分内容会放在后续章节讲解)
> HTML5 重新定义了元素的类别：见 [元素内容分类](https://developer.mozilla.org/zh-CN/docs/Web/Guide/HTML/Content_categories)

## HTML 标签

在 HTML 中，tag 用来创建一个 element。HTML 元素的名称是在尖括号中使用的名称，例如 `<p>` 用于段落（ paragraph ）。注意，结束标记的名称前面有一个斜杠字符"`</p>`"。在空元素中，结束标记既不需要也不允许。在任何情况下，如果没有提及 [attributes](https://developer.mozilla.org/zh-CN/docs/Glossary/Attribute) ，那么将使用默认值。

## HTML 注释

如同大部分的编程语言一样，在 HTML 中有一种可用的机制来在代码中书写注释 —— 注释是被浏览器忽略的，而且是对用户不可见的，它们的目的是允许你描述你的代码是如何工作的和不同部分的代码做了什么等等

为了将一段 HTML 中的内容置为注释，你需要将其用特殊的记号 `<!--和-->` 包括起来， 比如：

```html
<p>我在注释外！</p>

<!-- <p>我在注释内！</p> -->
```

## 编码注意事项

- HTML 标签**不区分大小写**，不过，从一致性、可读性等各方面来说，最好仅使用小写字母。
- 在 HTML 中，字符 <, >,",' 和 & 是特殊字符. 它们是 HTML 语法自身的一部分。必须使用时，可以使用字符引用，如 `<` 用 `&lt;` 表示
- 无论你在 HTML 元素的内容中使用多少空格(包括空白字符，包括换行)，当渲染这些代码的时候，HTML 解释器会将连续出现的空白字符减少为一个单独的空格符
- 在我们的 HTML 代码中，我们让每一个嵌套的元素以两个空格缩进。 你使用什么风格来格式化你的代码取决于你 (比如所对于每层缩进使用多少个空格)，但是你应该坚持使用某种风格

## 其他

- [HTML 元素参考](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element)
- [自定义元素](https://wiki.developer.mozilla.org/zh-CN/docs/Web/Web_Components/Using_custom_elements)
