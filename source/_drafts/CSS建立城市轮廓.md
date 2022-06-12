---
title: 通过建立城市轮廓学习 CSS 变量
date: 2022-06-15
tags: [CSS]
categories: Web前端
references: 
  - title: freeCodeCamp
    url: https://chinese.freecodecamp.org/learn/2022/responsive-web-design
---

> freeCodeCamp 响应式网页设计的认证课程第十二章。CSS 变量负责帮助组织你的样式和重复使用它们。在通过建立城市轮廓学习 CSS 变量的课程中，建立一座城市的轮廓，学习如何配置 CSS 变量，以便可以随时重复使用它们。

<!--more-->

### 一、重点 CSS 代码

In CSS, you can target everything with an asterisk：

```CSS
* {
  border: 1px solid black;
}
```

You have reset the `html` box model, you need to pass that on to the elements within as well.

The `::before` selector creates a pseudo-element which is the first child of the selected element, while the `::after` selector creates a pseudo-element which is the last child of the selected element：

```css
*, ::before, ::after {
  	box-sizing: inherit;
}
```

钢琴、琴键轮廓 🎹：

```CSS
#piano {
    background-color: #00471b;
    width: 992px;
    height: 290px;
    margin: 80px auto;
    padding: 90px 20px 0 20px;
    position: relative;
    border-radius: 10px;
}

.keys {
    background-color: #040404;
    width: 949px;
    height: 180px;
    padding-left: 2px;
    overflow: hidden; /* hide any element that is pushed outside the set width value of .keys */
}

.key {
    background-color: #ffffff;
    position: relative;
    width: 41px;
    height: 175px;
    margin: 2px;
    float: left;
    border-radius: 0 0 3px 3px;
}
```

To create the black keys, add a new `.key.black--key::after` selector. This will target the elements with the class `key black--key`, and select the pseudo-element after these elements in the HTML.

The `content` property is used to set or override the content of the element. By default, the pseudo-elements created by the `::before` and `::after` pseudo-selectors are empty, and the elements will not be rendered to the page：

```CSS
.key.black--key::after {
    background-color: #1d1e22;
    content: "";    /* make the pseudo-elements empty */
    position: absolute;
    left: -18px;
    width: 32px;
    height: 100px;
    border-radius: 0 0 3px 3px;
}
```

Styling the logo：

```CSS
.logo {
    width: 200px;
    position: absolute;
    top: 23px;
}
```

@media 属性 Make it responsive：

```CSS
@media (max-width: 768px) {
    #piano {
        width: 358px;
    }
    .keys {
        width: 318px;
    }
    .logo {
        width: 150px;
    }
}

@media (max-width: 1199px) and (min-width: 769px) {
    #piano {
        width: 675px;
    }
    .keys {
        width: 633px;
    }
}
```

### 二、页面展示

<div style="position: relative; width: 100%; height: 0; padding-bottom: 75%;">
    <iframe src="https://free-code-camp-demo.vercel.app/通过创建一架钢琴来学习响应式网页设计/index.html" border="0" frameborder="no" framespacing="0" allowfullscreen="true" style="position: absolute; width: 100%; height: 100%; left: 0; top: 0;"></iframe>
</div>
