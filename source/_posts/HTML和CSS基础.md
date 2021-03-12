---
title: HTML/CSS相关基础知识总结
date: 2020-09-10
updated: 2021-01-22
tags: [HTML/CSS]
categories: 编程与开发
references: 
  - title: 前端学习路线图
    url: https://github.com/kamranahmedse/developer-roadmap
  - title: W3school
    url: https://www.w3school.com.cn/h.asp
---

> 前端技术更新快，因此对于文档的阅读和[实际操练](https://learn.freecodecamp.one/)十分重要，当然最基本的知识肯定是基础的`html`, `css`, `js`三剑客了，基础阶段一定要打好，才能向更高峰攀登。笔记是对一些我认为的HTML/CSS相关常用知识的总结。至于想看最全和最权威文档的朋友还是移步[MDN web docs](https://developer.mozilla.org/zh-CN/)吧。

<!--more-->

### HTML简介

- HTML 指的是超文本标记语言 (**H**yper **T**ext **M**arkup **L**anguage)
- HTML 不是一种编程语言，而是一种标记语言 (markup language)，标记语言是一套标记标签 (markup tag)，HTML 使用标记标签来描述网页。

### HTML基础

- `<!DOCTYPE html>` 声明为 HTML5 文档

- `<html></html>` 之间的文本描述网页，`<main></main>` 元素让搜索引擎和开发者瞬间就能找到网页的主要内容。

- `<body></body>` 之间的文本是可见的页面内容

- `<h1></h1>` 之间的文本被显示为标题，`<p></p>` 之间的文本被显示为段落

- `<a href="url">text</a>` 定义HTML链接

- `<img src="url" alt="替换文本">`添加图片，`<map>` /`<area>` 定义地图和可点击部分

- `<br></br>` 表示空元素，`&nbsp;` 表示空格占位符，`&lt;` 表示小于号

- `<head></head>`包含了文档的元（meta）数据，如`<meta charset="utf-8">` 定义网页编码格式为 `utf-8`；`<title></title>`描述了文档的标题；`<base>`标签为页面上的所有链接规定默认地址或目标；`<link>` 标签定义文档与外部资源之间的关系

- `lorem ipsum text`是占位符。`<!--more-->`是注释，`<!--[if IE 8]><![endif]-->`条件注释只有IE8执行

- `id` 或 `name` 属性规定元素唯一id：`<a name="label">文本</a>`，`href` 属性值为井号`#`加上想跳转区域对应的`id`属性值创建内部跳转

- `target="_blank"` 属性在空白页打开标签

- `class` 属性规定元素类名，`style` 属性规定元素行内样式

- `<hr />` 标签在 HTML 页面中创建水平线，`<br /` 标签在不产生新段落的情况下换行

- `<b></b>` 定义粗体文本，`<em></em>` 定义着重文字

- `<code></code>` 定义计算机代码，`<kbd></kbd>` 定义键盘文本，`<pre></pre>` 定义预格式文本，`<var></var>` 定义变量

- `<q></q>` 定义短引用，`<blockquote cite="/link"></blockquote>` 定义长引用，`<dfn abbr title=""></dfn>` 定义项目定义

- `<bdo dir="rtl"></bdo>` 定义文本方向

- `<link rel="stylesheet" type="text/css" href="mystyle.css">` 放在在`<head></head>` 标签中使用外部样式表，也可以通过` <style></style>` 标签定义内部样式表。

- `<table border='1'></table>` 定义表格，其中`<tr></tr>` 定义行，再其中`<td></td>` 定义行中每个单元格，`<th></th>` 放在`<tr></tr>` 下表示表头

- `<ol></ol>` 定义有序列表，` <ul></ul>` 定义无序列表，`<li></li>` 定义列表项，`<dl></dl>` 定义定义列表，`<dt></dt>` 定义定义项目， `<dd></dd>` 定义定义的描述。

- `<div></div>` 定义文档中的分区或节(division/section)。 `<span></span>` 定义span,用来组合文档中行内的元素

- `<frameset cols="25%,75%"></frameset>` 定义HTML框架，`<iframe src="URL"></iframe>`定义内连标签

- `<body></body>` 拥有两个配置背景的标签，`Bgcolor`颜色或者`Background`图像

- `<script type=""></script` 标签用于定义客户端脚本，也可通过`src` 属性指向外部脚本文件，比如 JavaScript

- `<noscript></noscript>` 标签提供无法使用脚本时的替代内容

- 颜色由红色、绿色、蓝色混合而成，每种颜色的最小值是0（十六进制：#00），最大值是255（十六进制：#FF），如黑色`#000000`

- 从 Web 诞生早期至今，已经发展出多个 HTML 版本：

  | 版本      | 年份 |
  | :-------- | :--- |
  | HTML      | 1991 |
  | HTML+     | 1993 |
  | HTML 2.0  | 1995 |
  | HTML 3.2  | 1997 |
  | HTML 4.01 | 1999 |
  | XHTML 1.0 | 2000 |
  | HTML5     | 2012 |
  | XHTML5    | 2013 |

### XHTML

- XHTML 指的是可扩展超文本标记语言，是以 XML 应用的方式定义的 HTML，是更严格更纯净的 HTML 版本
- XHTML文档结构
  - `XHTML DOCTYPE` 是强制性的
  - `<html></html>` 中的 `XML namespace` 属性是强制性的
  - `<html></html>`、`<head></head>`、`<title></title>` 以及 `<body></body> `也是强制性的

- XHTML元素语法
  - XHTML 元素必须正确嵌套
  - XHTML 元素必须始终关闭，包括空元素
  - XHTML 元素必须小写
  - XHTML 文档必须有一个根元素

- XHTML属性语法
  - XHTML 属性必须使用小写
  - XHTML 属性值必须用引号包围
  - XHTML 属性最小化也是禁止的
- 从 HTML 转换到 XHTML
  1. 向每张页面的第一行添加 XHTML <!DOCTYPE>
  2. 向每张页面的 html 元素添加 `xmlns` 属性
  3. 把所有元素名改为小写
  4. 关闭所有空元素
  5. 把所有属性名改为小写
  6. 为所有属性值加引号

### HTML表单

- `<form></form>` 元素定义 HTML 表单搜集输入
- `<input type='text' name="描述字" value="占位字">`  是最重要的表单元素
- `<input type="radio"> `定义单选按钮，`checkbox` 定义复选框，`submit` 定义提交
- `action` 属性定义在提交表单时执行的动作，默认刷新页面
- `method` 属性规定在提交表单时所用的 HTTP 方法（GET 或 POST）
- `<fieldset></fieldset>` 元素组合表单中的相关数据，`<legend></legend>` 元素为其定义标题
- `<select></select>` 元素定义下拉列表，`<option></option>` 元素定义待选择的选项（ `selected` 属性定义预定义选项）
- `<textarea></textarea>` 元素定义多行输入字段（文本域），`<button></button>` 元素定义可点击的按钮
- `<datalist></datalist>` 元素为 `<input></input>` 元素规定预定义选项列表
- value 属性规定输入字段的初始值，readonly 属性规定输入字段为只读，size 属性规定输入字段的尺寸，maxlength 属性规定输入字段允许的最大长度，autocomplete 属性规定表单或输入字段是否应该自动完成，novalidate 属性规定在提交表单时不对表单数据进行验证。。。。。。

### HTML5

- HTML5 是最新的 HTML 标准，是专门为承载丰富的 web 内容而设计的，并且无需额外插件，拥有新的语义、图形以及多媒体元素，提供的新元素和新的 API 简化了 web 应用程序的搭建，是跨平台的，被设计为在不同类型的硬件（PC、平板、手机、电视机等等）之上运行。

- [帮助老版本浏览器处理 HTML5](https://www.w3school.com.cn/html/html5_browsers.asp)

- HTML5 提供的新元素：

  | 标签         | 描述                                                 |
  | :----------- | :--------------------------------------------------- |
  | `<article>` | 定义文档内的文章。                                   |
  | `<aside>`    | 定义页面内容之外的内容。                             |
  | `<bdi>`      | 定义与其他文本不同的文本方向。                       |
  | `<details>`  | 定义用户可查看或隐藏的额外细节。                     |
  | `<dialog>`   | 定义对话框或窗口。                                   |
  | `<figcaption>` | 定义 `<figure> `元素的标题。                         |
  | `<figure>`   | 定义自包含内容，比如图示、图表、照片、代码清单等等。 |
  | `<footer>`   | 定义文档或节的页脚。                                 |
  | `<header>`   | 定义文档或节的页眉。                                 |
  | `<main>`     | 定义文档的主内容。                                   |
  | `<mark>`     | 定义重要或强调的内容。                               |
  | `<menuitem>` | 定义用户能够从弹出菜单调用的命令/菜单项目。          |
  | `<meter>`    | 定义已知范围（尺度）内的标量测量。                   |
  | `<nav>`      | 定义文档内的导航链接。                               |
  | `<progress>` | 定义任务进度。                                       |
  | `<rp>`       | 定义在不支持 ruby 注释的浏览器中显示什么。           |
  | `<rt>`       | 定义关于字符的解释/发音（用于东亚字体）。            |
  | `<ruby>`     | 定义 ruby 注释（用于东亚字体）。                     |
  | `<section>`  | 定义文档中的节。                                     |
  | `<summary>`  | 定义 `<details>` 元素的可见标题。                    |
  | `<time>`     | 定义日期/时间。                                      |
  | `<wbr>`      | 定义可能的折行（line-break）。                       |
  | `<datalist>` | 定义输入控件的预定义选项。       |
  | `<keygen>` | 定义键对生成器字段（用于表单）。 |
  | `<output>` | 定义计算结果。                   |
  | `<canvas>` | 定义使用 JavaScript 的图像绘制。 |
  | `<svg>`  | 定义使用 SVG 的图像绘制。        |
  | `<audio>` | 定义声音或音乐内容。                 |
  | `<embed>` | 定义外部应用程序的容器（比如插件）。 |
  | `<source>` | 定义 `<video> `和` <audio> `的来源。 |
  | `<track>` | 定义 `<video>` 和 `<audio>` 的轨道。 |
  | `<video>` | 定义视频或影片内容。                 |
  
- 详细内容和用法见：[HTML5参考手册](https://www.w3school.com.cn/tags/index.asp)

### CSS基础

- CSS 指层叠样式表 (Cascading *S*tyle *S*heets)，样式定义如何显示 HTML 元素，样式通常存储在样式表中

- 外部样式表可以极大提高工作效率，外部样式表通常存储在 CSS 文件中，多个样式定义可层叠为一

- CSS 规则：`selector {property1: value1; property2: value2, value2sub;}`

- 派生选择器：`li strong {font-style: italic;}`

- id 选择器以 "#" 来定义：`#id-red {color:red;}`

- CSS 类选择器：`.center {text-align: center}`（前提：`class=center`）

- CSS 属性选择器：`[attribute=value]{}`

- CSS 基本样式属性

  | 属性                  | 描述                                                         |
  | :-------------------- | :----------------------------------------------------------- |
  | background            | 简写属性，作用是将背景属性设置在一个声明中。                 |
  | background-attachment | 背景图像是否固定或者随着页面的其余部分滚动。                 |
  | background-color      | 设置元素的背景颜色。                                         |
  | background-image      | 把图像设置为背景。                                           |
  | background-position   | 设置背景图像的起始位置。                                     |
  | background-repeat     | 设置背景图像是否及如何重复。                                 |
  | color                 | 设置文本颜色                                                 |
  | direction             | 设置文本方向。                                               |
  | line-height           | 设置行高。                                                   |
  | letter-spacing        | 设置字符间距。                                               |
  | text-align            | 对齐元素中的文本。                                           |
  | text-decoration       | 向文本添加修饰。                                             |
  | text-indent           | 缩进元素中文本的首行。                                       |
  | text-shadow           | 设置文本阴影。CSS2 包含该属性，但是 CSS2.1 没有保留该属性。  |
  | text-transform        | 控制元素中的字母。                                           |
  | unicode-bidi          | 设置文本方向。                                               |
  | white-space           | 设置元素中空白的处理方式。                                   |
  | word-spacing          | 设置字间距。                                                 |
  | font                  | 简写属性。作用是把所有针对字体的属性设置在一个声明中。       |
  | font-family           | 设置字体系列。                                               |
  | font-size             | 设置字体的尺寸。                                             |
  | font-size-adjust      | 当首选字体不可用时，对替换字体进行智能缩放。（CSS2.1 已删除该属性。） |
  | font-style            | 设置字体风格。                                               |
  | font-variant          | 以小型大写字体或者正常字体显示文本。                         |
  | font-weight           | 设置字体的粗细。                                             |
  | list-style            | 简写属性。用于把所有用于列表的属性设置于一个声明中。         |
  | list-style-image      | 将图象设置为列表项标志。                                     |
  | list-style-position   | 设置列表中列表项标志的位置。                                 |
  | list-style-type       | 设置列表项标志的类型。                                       |
  | marker-offset         |                                                              |
  | border-collapse       | 设置是否把表格边框合并为单一的边框。                         |
  | border-spacing        | 设置分隔单元格边框的距离。                                   |
  | caption-side          | 设置表格标题的位置。                                         |
  | empty-cells           | 设置是否显示表格中的空单元格。                               |
  | table-layout          | 设置显示单元、行和列的算法。                                 |
  | outline               | 在一个声明中设置所有的轮廓属性。                             |
  | outline-color         | 设置轮廓的颜色。                                             |
  | outline-style         | 设置轮廓的样式。                                             |
  | outline-width         | 设置轮廓的宽度。                                             |
  
- CSS链接的四种状态：
  
  - `a:link {}`- 普通的、未被访问的链接
  - `a:visited {}`- 用户已访问的链接
  - `a:hover {}`- 鼠标指针位于链接的上方
  - `a:active {}`- 链接被点击的时刻

- CSS框模型：element : 元素，padding : 内边距，border : 边框，margin : 外边距

- CSS定位（position属性）

  - static：元素框正常生成
  - relative：元素框偏移某个距离
  - absolute：元素框从文档流完全删除，并相对于其包含块定位。
  - fixed：元素框的表现类似于将 position 设置为 absolute，不过其包含块是视窗本身。

- CSS浮动定位（float属性）

- 伪类和伪元素

- [@media](https://www.w3school.com.cn/css/css_mediatypes.asp) 规则使你有能力在相同的样式表中，使用不同的样式规则来针对不同的媒介。

- 更多关于 CSS 的信息，请参阅 [CSS 实例](https://www.w3school.com.cn/example/csse_examples.asp)、[CSS 参考手册](https://www.w3school.com.cn/cssref/index.asp)

### CSS3

- CSS3 完全向后兼容，浏览器通常支持 CSS2，因此您不必改变现有的设计。
- 选择器
- 框模型

  - border-radius
  - box-shadow
  - border-image
- 背景和边框

  - background-size
  - background-origin
- 文本效果

  - text-shadow
  - word-wrap
- 2D/3D 转换

  - translate()
  - rotate()
  - scale()
  - skew()
  - matrix()
  - rotateX()
  - rotateY()
- 动画
  - transition
  - transition-property
  - transition-duration
- transition-timing-function
  - animation
- 多列布局
  - column-count
  - column-gap
  - column-rule
- 用户界面
  - resize
  - box-sizing
  - outline-offset

- [CSS3参考手册](https://www.w3school.com.cn/cssref/index.asp)