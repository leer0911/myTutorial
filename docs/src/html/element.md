# HTML 元素

:::tip 问题列表

- 什么是 元数据？
- 如何设置网页标题与描述？
- 如何引入外部样式与脚本？
- 如何引入 favicon？
- meta 元素有哪些作用？
- 如何提高 img 元素的可访问性？

:::

## 元素分类

HTML 包含了非常多的元素，按照功能分组如下：

- 主根元素
- 文档元数据
- 分区根元素
- 内容分区
- 文本内容
- 内联文本语义
- 图片和多媒体
- 内嵌内容
- 脚本
- 编辑标识
- 表格内容
- 表单
- 交互元素
- Web 组件

由于元素过多，建议新手在想进一步了解某元素时通过 [HTML 元素参考](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element) 了解具体细节。

**受限于篇幅，本章仅介绍比较特别的元素**

## [`<base>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/base)

需要了解的知识点：

- HTML `<base>` 元素用于一个 HTML 文档中包含的所有相对 URL 的根 URL。一份中只能有一个 `<base>` 元素
 
- `<base>` 元素必须在其他任何属性是URL的元素之前 `<base>` 元素的 href 属性才有效，比如 `<link>`
 
- 如果指定了多个 `<base>` 元素，只会使用第一个 href 和 target 值, 其余都会被忽略
 
- [Open Graph](https://ogp.me/)（一些社交 meta 标签） 不接受 `<base>`，并且应该始终具有完整的绝对URL。例如：

    `<meta property="og:image" content="https://example.com/thumbnail.jpg">`

## [`<link>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/link)

需要了解的知识点：

- `<link>` 元素可以出现在 `<head>` 元素或者 `<body>` 元素中，具体取决于它是否有一个 body-ok 的[链接类型](https://html.spec.whatwg.org/multipage/links.html#body-ok)，例如，stylesheet链接类型是body-ok的，因此 `<link rel="stylesheet">` 允许出现在body中。然而，这不是一种好的可遵循的实践方式；更合理的方式是，将你的 `<link>` 元素从你的body内容中分离出来，将其放在 `<head>` 中。 

- 可以设置媒体类型，或者在 media 属性内部进行查询；这种资源将只在满足媒体条件的情况下才被加载进来。例如：

    ```html
    <link href="print.css" rel="stylesheet" media="print">
    <link href="mobile.css" rel="stylesheet" media="screen and (max-width: 600px)">
    ```

- 网站图标的链接

    `<link rel="icon" href="favicon.ico">`

- 引入一个css文件

    `<link href="style.css" rel="stylesheet">`

推荐阅读

- [链接类型及其在 HTML 中的意义](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Link_types)
- [通过rel="preload"进行内容预加载](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Preloading_content)
- [可替换的外部样式表](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Alternative_style_sheets)

## [`<meta>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meta)

需要了解的知识点：

- HTML 元相关（meta-related）元素：`<base>`、`<link>`, `<script>`、`<style>` 或 `<title>`
- 如果设置了 name 属性，meta 元素提供的是文档级别（document-level）的元数据，应用于整个页面
- 如果设置了 `http-equiv` 属性，meta 元素则是编译指令，提供的信息与类似命名的HTTP头部相同
- 如果设置了 `charset` 属性，meta 元素是一个字符集声明，告诉文档使用哪种字符编码
- 如果设置了 `itemprop` 属性，meta 元素提供用户定义的元数据
- 在同一个 `<meta>` 标签中，name, http-equiv 或者 charset 三者中任何一个属性存在时，itemprop 属性不能被使用

推荐阅读

- [标准元数据名称](https://wiki.developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meta/name)

## [`<title>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/title)

需要了解的知识点：

- 它只应该包含文本，若是包含有标签，则它包含的任何标签都将被忽略
- 这个元素只拥有[全局属性](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes)
- `<title>` 元素始终在页面的 `<head>` 块内使用
- 页面标题的内容可能对搜索引擎优化（[SEO](https://developer.mozilla.org/zh-CN/docs/Glossary/SEO)）具有重要意义

## [`<img>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/title)

需要了解的知识点

- Referrer/CORS 控制，保证安全与隐私：详见 [crossorigin](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img#attr-crossorigin) 属性和 [referrerpolicy](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img#attr-referrerpolicy) 属性

- 如果在加载或渲染图像时发生错误，且设置了至少一个 onerror 事件处理器来处理 error 事件，那么设置的事件处理器就会被调用。这样的错误可能发生在各种不同的情况下，包括：
  - src 属性的属性值为空（""）或者 null。
  - src 属性的 URL 和用户正在浏览的页面的 URL 完全相同。
  - 图像出于某些原因损坏了，从而无法加载。
  - 图像的元数据被破坏了，无法检索它的分辨率/宽高，而且在 <img> 元素的属性中没有指定宽度和/或高度。
  - 用户代理尚未支持该图片所用的格式。

## 推荐阅读

- [网站可访问性](https://developer.mozilla.org/zh-CN/docs/Glossary/Accessibility)
- [响应式图片](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images)
- [可替换元素](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Replaced_element)
- [网页浏览器图像格式指南](https://developer.mozilla.org/zh-CN/docs/Web/Media/Formats/Image_types)
- [HTML的媒体支持:audio和video元素](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Supported_media_formats)