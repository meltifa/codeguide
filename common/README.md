## 目录

### [HTML](#html-1)

* [语法](#语法)
* [HTML5 doctype](#html5-doctype)
* [字符编码](#字符编码)
* [IE 兼容模式](#ie-兼容模式)
* [实用为王](#实用为王)
* [布尔（boolean）型属性](#%E5%B8%83%E5%B0%94boolean%E5%9E%8B%E5%B1%9E%E6%80%A7)
* [减少标签的数量](#减少标签的数量)
* [JavaScript 生成的标签](#javascript-生成的标签)

### [CSS](#css-1)

* [语法](#语法-1)
* [不要使用 @import](#%E4%B8%8D%E8%A6%81%E4%BD%BF%E7%94%A8-import)
* [媒体查询（Media query）的位置](#%E5%AA%92%E4%BD%93%E6%9F%A5%E8%AF%A2media-query%E7%9A%84%E4%BD%8D%E7%BD%AE)
* [带前缀的属性](#带前缀的属性)
* [单行规则声明](#单行规则声明)
* [简写形式的属性声明](#简写形式的属性声明)
* [尽可能精简规则](#尽可能精简规则)
* [Less 和 Sass 中的嵌套](#less-和-sass-中的嵌套)
* [注释](#注释)
* [class 命名](#class-命名)
* [选择器](#选择器)
* [代码组织](#代码组织)

## HTML

### 语法

```html
<!doctype html>
<html>
  <head>
    <title>Page title</title>
  </head>
  <body>
    <img src="images/company-logo.png" alt="Company">
    <h1 class="hello-world">Hello, world!</h1>
  </body>
</html>
```

* 在代码完成后应该用格式化工具来保证你的代码缩进换行等风格统一，如 Sublime Text 插件 HTML-CSS-JS Prettify。WebStorm、Dreamweaver等IDE也内建了格式化代码功能。
* 对于属性的定义，确保全部使用双引号，绝不要使用单引号。
* 不要在自闭和（self-closing）元素的尾部添加斜线 -- HTML5 规范中明确说明这是可选的。
* 不要省略可选的结束标签（closing tag）（例如，`</li>` 或 `</body>`）。

### HTML5 doctype

为每个 HTML 页面的第一行添加标准模式（standard mode）的声明，这样能够确保在每个浏览器中拥有一致的展现。

```html
<!doctype html>
<html>
  <head>
  </head>
</html>
```

### IE 兼容模式

```html
<meta http-equiv="X-UA-Compatible" content="IE=Edge">
```

IE 支持通过特定的 <meta> 标签来确定绘制当前页面所应该采用的 IE 版本。除非有强烈的特殊需求，否则最好是设置为 edge mode，从而通知 IE 采用其所支持的最新的模式。

[阅读这篇 stack overflow 上的文章可以获得更多有用的信息](http://stackoverflow.com/questions/6771258/whats-the-difference-if-meta-http-equiv-x-ua-compatible-content-ie-edge-e)

### 字符编码

```html
<head>
  <meta charset="UTF-8">
</head>
```

通过明确声明字符编码，能够确保浏览器快速并容易的判断页面内容的渲染方式。这样做的好处是，可以避免在 HTML 中使用字符实体标记（character entity），从而全部与文档编码一致（一般采用 UTF-8 编码）。

### 实用为王

尽量遵循 HTML 标准和语义，但是不要以牺牲实用性为代价。任何时候都要尽量使用最少的标签并保持最小的复杂度。

### 布尔（boolean）型属性

```html
<input type="text" disabled>

<input type="checkbox" value="1" checked>

<select>
  <option value="1" selected>1</option>
</select>
```

布尔型属性可以在声明时不赋值。XHTML 规范要求为其赋值，但是 HTML5 规范不需要。

[更多信息请参考 WhatWG section on boolean attributes](http://www.whatwg.org/specs/web-apps/current-work/multipage/common-microsyntaxes.html#boolean-attributes)

> 元素的布尔型属性如果有值，就是 true，如果没有值，就是 false。

如果一定要为其赋值的话，请参考 WhatWG 规范：

> 如果属性存在，其值必须是空字符串或 [...] 属性的规范名称，并且不要再收尾添加空白符。

简单来说，就是不用赋值。

### 减少标签的数量

```html
<!-- Not so great -->
<span class="avatar">
  <img src="...">
</span>

<!-- Better -->
<img class="avatar" src="...">
```

编写 HTML 代码时，尽量避免多余的父元素。很多时候，这需要迭代和重构来实现。

### JavaScript 生成的标签

通过 JavaScript 生成的标签让内容变得不易查找、编辑，并且降低性能。能避免时尽量避免。

## CSS

### 语法

```css
/* Bad CSS */
.selector, .selector-secondary, .selector[type=text] {
  padding:15px;
  margin:0px 0px 15px;
  background-color:rgba(0, 0, 0, 0.5);
  box-shadow:0px 1px 2px #CCC,inset 0 1px 0 #FFFFFF;
  font-family: 宋体, 微软雅黑;
}

/* Good CSS */
.selector,
.selector-secondary,
.selector[type="text"] {
  padding: 15px;
  margin-bottom: 15px;
  background-color: rgba(0,0,0,.5);
  box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
  font-family:simsun, "microsoft yahei";
}
```

* css里的字体名用英文名来设置，中文名可能会有编码问题导致字体设置失效。如宋体用simsun，微软雅黑用microsoft yahei，注意带空格的字体名必须用引号括起来。
* 在代码完成后应该用格式化工具来保证你的代码缩进换行等风格统一，如Sublime Text插件CSS Format。WebStorm、Dreamweaver等IDE也内建了格式化代码功能。
* 所有声明语句都应当以分号结尾。最后一条声明语句后面的分号是可选的，但是，如果省略这个分号，你的代码可能更易出错。
* 对于以逗号分隔的属性值，每个逗号后面都应该插入一个空格（例如，`box-shadow`）。
* 对于属性值或颜色参数，省略小于 1 的小数前面的 0 （例如，.5 代替 0.5；-.5px 代替 -0.5px）。
* 十六进制值应该全部小写，例如，`#fff`。在扫描文档时，小写字符易于分辨，因为他们的形式更易于区分。
* 尽量使用简写形式的十六进制值，例如，用 `#fff` 代替 `#ffffff`。
* 为选择符中的属性添加双引号，例如，`input[type="text"]`。只有在某些情况下是可选的，但是，为了代码的一致性，建议都加上双引号。
* 避免为 0 值指定单位，例如，用 `margin: 0;` 代替 `margin: 0px;`。
* 避免 `!important`，其实你应该也可以使用其他优质的选择器。
* 对于这里用到的术语有疑问吗？请参考 Wikipedia 上的 syntax section of the Cascading Style Sheets article。

### 不要使用 `@import`

```css
<!-- Use link elements -->
<link rel="stylesheet" href="core.css">

<!-- Avoid @imports -->
<style>
  @import url("more.css");
</style>
```

与 `<link>` 标签相比，`@import` 指令要慢很多，它会在页面其他资源加载完毕才开始加载，在慢速网络中尤其明显，可能会导致样式闪动，替代方案如下：

* 使用多个 `<link>` 元素
* 通过 Sass 或 Less 类似的 CSS 预处理器将多个 CSS 文件编译为一个文件

### 媒体查询（Media query）的位置

将媒体查询放在尽可能相关规则的附近。不要将他们打包放在一个单一样式文件中或者放在文档底部。如果你把他们分开了，将来只会被大家遗忘。下面给出一个典型的实例。

```css
.element { ... }
.element-avatar { ... }
.element-selected { ... }

@media (min-width: 480px) {
  .element { ...}
  .element-avatar { ... }
  .element-selected { ... }
}
```

### 带前缀的属性

```css
/* Prefixed properties */
.selector {
  -webkit-box-shadow: 0 1px 2px rgba(0,0,0,.15);
          box-shadow: 0 1px 2px rgba(0,0,0,.15);
}
```

当使用特定厂商的带有前缀的属性时，最后一行必须有不带前缀的标准 CSS3 属性，有些现代浏览器只支持不带前缀的 CSS3 属性，如 IE10 &amp; 11。

### 单行规则声明

```css
/* Single declarations on one line */
.span1 { width: 60px; }
.span2 { width: 140px; }
.span3 { width: 220px; }

/* Multiple declarations, one per line */
.sprite {
  display: inline-block;
  width: 16px;
  height: 15px;
  background-image: url(../img/sprite.png);
}
.icon           { background-position: 0 0; }
.icon-home      { background-position: 0 -20px; }
.icon-account   { background-position: 0 -40px; }
```

对于只包含一条声明的样式，可以将语句放在同一行。对于带有多条声明的样式，还是应当将声明分为多行。

这样做的关键因素是为了错误检测 -- 例如，CSS 校验器指出在 183 行有语法错误。这种情况多行比单行更容易定位问题所在。

### 简写形式的属性声明

```css
/* Bad example */
.element {
  margin: 0 0 10px;
  padding-bottom: 10px;
  padding-right: 10px;
  padding-top: 10px;
  background: red;
  background: url("image.jpg");
}

/* Good example */
.element {
  margin-bottom: 10px;
  padding: 10px 10px 10px 0;
  background-color: red;
  background-image: url("image.jpg");
}
```

合理使用简写属性声明，同时也要避免滥用简写，在使用简写时要注意一些没有被声明出来的值也有可能被覆盖。比如 `background`，`font` 等

### 尽可能精简规则

```css
/* Bad example */
.someclass {
  color: red;
  background: blue;
  height: 150px;
  width: 150px;
  font-size: 16px;
}
.otherclass {
  color: red;
  background: blue;
  height: 150px;
  width: 150px;
  font-size: 8px;
}

/* Good example */
.someclass,
.otherclass {
  color: red;
  background: blue;
  height: 150px;
  width: 150px;
}
.someclass { font-size: 16px; }
.otherclass { font-size: 8px; }
```

尽可能合并不同类里的重复的规则

### Less 和 Sass 中的嵌套

```css
// Without nesting
.table > thead > tr > th { … }
.table > thead > tr > td { … }

// With nesting
.table > thead > tr {
  > th { … }
  > td { … }
}
```

避免非必要的嵌套。这是因为虽然你可以使用嵌套，但是并不意味着应该使用嵌套。只有在必须将样式限制在父元素内（也就是后代选择器），并且存在多个需要嵌套的元素时才使用嵌套。

### 注释

```css
/* Bad example */
/* Modal header */
.modal-header {
  ...
}

/* Good example */
/* Wrapping element for .modal-title and .modal-close */
.modal-header {
  ...
}
```

代码是由人编写并维护的。请确保你的代码能够自描述、注释良好并且易于他人理解。好的代码注释能够传达上下文关系和代码目的。不要简单地重申组件或 class 名称。

对于较长的注释，务必书写完整的句子；对于一般性注解，可以书写简洁的短语。

对于外部独立的 js 或 css 文件，在使用中文注释时要保证文件和引用页面的编码完全一致，否则 IE6 下会出现代码无法解析的BUG！

### class 命名

```css
/* Bad example */
.t { ... }
.red { ... }
.header { ... }

/* Good example */
.tweet { ... }
.important { ... }
.tweet-header { ... }
```

* class 名称必须是英文单词或产品名称的拼音，只能出现小写字母和破折号（dashe）（不是下划线，也不是驼峰命名法）。破折号应当用于相关 class 的命名（类似于命名空间）（例如，.btn 和 .btn-danger）。
* 避免过度任意的简写。.btn 代表 button，但是 .s 不能表达任何意思。
* class 名称应当尽可能短，并且意义明确。
* 使用有意义的名称。使用有组织的或目的明确的名称，不要使用表现形式（presentational）的名称，如 .mt20，.pr30，fz12 等。
* 基于最近的父 class 或基本（base） class 作为新 class 的前缀。
* 在为 Sass 和 Less 变量命名是也可以参考上面列出的各项规范。

常见class关键词：

布局类：header, footer, container, main, content, aside, page, section

包裹类：wrap, inner

区块类：region, block, box

结构类：hd, bd, ft, top, bottom, left, right, middle, col, row, grid, span

列表类：list, item, field

主次类：primary, secondary, sub, minor

大小类：large, small

状态类：active, current, checked, hover, fail, success, warn, error, on, off

导航类：nav, prev, next, breadcrumb, forward, back, indicator, paging, first, last

交互类：tips, alert, modal, pop, panel, tabs, accordion, slide, scroll, overlay, dialog

星级类：rate, star

分割类：group, seperate, divider

等分类：full, half, third, quarter

表格类：table, tr, td, cell, row

图片类：img, thumbnail, original, album, gallery

语言类：cn, en

论坛类：forum, bbs, topic, post, avatar

方向类：up, down, left, right

其他语义类：btn, close, ok, cancel, switch; link, title, info, intro, more, icon; form, label, search, contact, phone, date, email, user; view, loading...

### 选择器

```css
/* Bad example */
span { ... }
.page-container #stream .stream-item .tweet .tweet-header .username { ... }
.avatar { ... }
.avatar { ... }
ul#someid { ... }
.menu#otherid { ... }

/* Good example */
.avatar { ... }
.tweet-header .username { ... }
.tweet .avatar { ... }
#someid { ... }
#otherid { ... }
```

* 对于通用元素使用 class ，这样利于渲染性能的优化。
* 对于经常出现的组件，避免使用属性选择器（例如，`[class^="..."]）`。浏览器的性能会受到这些因素的影响。
* 选择器要尽可能短，并且尽量限制组成选择器的元素个数，建议不要超过 3 。
* 只有在必要的时候才将 class 限制在最近的父元素内（也就是后代选择器）（例如，不使用带前缀的 class 时 -- 前缀类似于命名空间）。
* 一条普遍规则，不要添加不必要的约束。（例如`ul#someid {...} .menu#otherid{...}`）

#### 扩展阅读：

* [Scope CSS classes with prefixes](http://markdotto.com/2012/02/16/scope-css-classes-with-prefixes/)
* [Stop the cascade](http://markdotto.com/2012/03/02/stop-the-cascade/)

### 代码组织

```css
/*
 * Component section heading
 */

.element { ... }


/*
 * Component section heading
 *
 * Sometimes you need to include optional context for the entire component. Do that up here if it's important enough.
 */

.element { ... }

/* Contextual sub-component or modifer */
.element-heading { ... }
```

* 以组件为单位组织代码段。
* 制定一致的注释规范。
* 使用一致的空白符将代码分隔成块，这样利于扫描较大的文档。
* 如果使用了多个 CSS 文件，将其按照组件而非页面的形式分拆，因为页面会被重组，而组件只会被移动。
