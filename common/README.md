## 目录

### [HTML](#html-1)

* [语法语法和格式](#语法和格式)
* [HTML5 doctype](#html5-doctype)
* [lang属性](#lang属性)
* [IE 兼容模式](#ie-兼容模式)
* [字符编码](#字符编码)
* [实用为王](#实用为王)
* [引入CSSJS](#引入cssjs)
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
* [SCSS相关](#scss相关)
* [注释](#注释)
* [css 命名](#css-命名)
* [选择器](#选择器)

## HTML

### 语法和格式
```html
<!DOCTYPE html>
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
* 缩进使用soft tab（2个空格）；
* 嵌套的节点应该缩进；
* 对于属性的定义，确保全部使用双引号，不要使用单引号；
* 属性名全小写，用中划线做分隔符；
* 不要在自闭合元素的尾部添加斜线 -- HTML5 规范中明确说明这是可选的；
* 不要省略可选的结束标签（例如，`</li>` 或 `</body>`）。

### HTML5 doctype

为每个 HTML 页面的第一行添加标准模式（standard mode）的声明，这样能够确保在每个浏览器中拥有一致的展现。
虽然doctype不区分大小写，但是按照惯例，doctype统一大写。

```html
<!DOCTYPE html>
<html>
  <head>
  </head>
</html>
```

### lang属性

HTML5规范建议html标签上加上lang属性。这会给语音工具和翻译工具帮助，告诉它们应当怎么去发音和翻译。
一些编辑器会自动生成lang属性为en-us，请及时修改为zh-cn。

```html
<!DOCTYPE html>
<html lang="zh-cn">
    ...
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

通过明确声明字符编码，能够确保浏览器快速并容易的判断页面内容的渲染方式，没有特殊需求，统一采用 UTF-8 编码。

### 实用为王

尽量遵循 HTML 标准和语义，但是不要以牺牲实用性为代价。任何时候都要尽量使用最少的标签并保持最小的复杂度。

### 引入CSSJS

```html
<link rel="stylesheet" href="code_guide.css">
<script src="code_guide.js"></script>
```

根据HTML5规范, 通常在引入CSS和JS时不需要指明 type，因为 text/css 和 text/javascript 分别是他们的默认值。

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

### 减少标签的数量

```html
<!-- Not so great -->
<span class="avatar">
  <img src="...">
</span>

<!-- Better -->
<img class="avatar" src="...">
```

编写 HTML 代码时，尽量避免多余的父元素。

### JavaScript 生成的标签

通过 JavaScript 生成的标签让内容变得不易查找、编辑，并且降低性能。能避免时尽量避免。

## CSS

### 语法及格式
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
.selector[type='text'] {
  padding: 15px;
  margin-bottom: 15px;
  background-color: rgba(0,0,0,.5);
  box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
  font-family:simsun, "microsoft yahei";
}
```
* 缩进使用soft tab（2个空格）。
* 每条属性声明末尾都要加分号。
* 十六进制值应该全部小写，例如，`#fff`。
* 尽量使用简写形式的十六进制值，例如，用 `#fff` 代替 `#ffffff`。
* 统一使用单引号。
* 尽量避免 `!important`。
* 不允许有空的规则；
* 只书写不带前缀的选择器、属性和值，前缀由编译工具自动添加；
* 选择器、属性和值统一用小写字母；
* 为了直观，不要省略小数点前面的0；
* 去掉数字中不必要的小数点和末尾的0；
* 属性值'0'后面不要加单位；
* 不要在同个规则里出现重复的属性；
* 不要在一个文件里出现两个相同的规则；
* 选择器不要超过4层；
* 尽量少用'*'选择器。

#### 空格

```css
.element  > .dialog {
    color: red !important;
    background-color: rgba(0, 0, 0, .5);
}
```

以下几种情况需要空格：

* 属性值前
* 选择器'>', '+', '~'前后
* '{'前
* !important '!'前
* @else 前后
* 属性值中的','后（例如，`rgba(0, 0, 0, 0.5)`）
* 注释'/*'后和'*/'前

#### 空行

* 文件最后保留一个空行
* '}'后跟一个空行，包括scss中嵌套的规则

#### 换行

以下几种情况不需要换行：

* '{'前

以下几种情况需要换行：

* '{'后和'}'前
* 每个属性独占一行
* 多个规则的分隔符','后


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

### 简写形式的属性声明

```css
/* Bad example */
.element {
  margin: 0 0 10px;
  padding-bottom: 10px;
  padding-right: 10px;
  padding-top: 10px;
  background: red;
  background: url(image.jpg);
}

/* Good example */
.element {
  margin-bottom: 10px;
  padding: 10px 10px 10px 0;
  background-color: red;
  background-image: url(image.jpg);
}
```

合理使用简写属性声明，同时也要避免滥用简写，在使用简写时要注意一些没有被声明出来的值也有可能被覆盖。比如 `background`，`font` 等，建议margin和padding使用简写，其他属性分开

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

### SCSS相关
```css
/* not good */
@import "_dialog.scss";

/* good */
@import "dialog";

/* not good */
.fatal {
    @extend .error;
}

/* good */
.fatal {
    @extend %error;
}

/* not good */
.element {
    & > .dialog {
        ...
    }
}

/* good */
.element {
    > .dialog {
        ...
    }
}
```
声明顺序：

@extend
不包含 @content 的 @include
包含 @content 的 @include
自身属性
嵌套规则
@import 引入的文件不需要开头的'_'和结尾的'.scss'；

嵌套最多不能超过4层；

@extend 中使用placeholder选择器；

去掉不必要的父级引用符号'&'。

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

### css 命名

```css
/* Bad example */
.t { ... }
.red { ... }
.header { ... }

/* Good example */
.tweet { ... }
.important { ... }
.tweet-header { ... }
/* 变量 */
$colorBlack: #000;
/* 函数 */
@function pxToRem($px) {
    ...
}
/* 混合 */
@mixin centerBlock {
    ...
}
```

* class 名称必须是英文单词或产品名称的拼音，只能出现小写字母和中划线。中划线应当用于相关 class 的命名（类似于命名空间）（例如，.btn 和 .btn-danger）。
* 避免过度任意的简写。.btn 代表 button，但是 .s 不能表达任何意思。
* class 名称应当尽可能短，并且意义明确。
* 使用有意义的名称。使用有组织的或目的明确的名称，不要使用表现形式（presentational）的名称，如 .mt20，.pr30，fz12 等。
* scss中的变量、函数、混合、placeholder采用驼峰式命名

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

* 尽量使用 class 选择器。
* 选择器要尽可能短，并且尽量限制组成选择器的元素个数，建议不要超过 3。
* 只有在必要的时候才将 class 限制在最近的父元素内（也就是后代选择器）（例如，不使用带前缀的 class 时 -- 前缀类似于命名空间）。
* 一条普遍规则，不要添加不必要的约束。（例如`ul#someid {...} .menu#otherid{...}`）

#### 扩展阅读：

* [Scope CSS classes with prefixes](http://markdotto.com/2012/02/16/scope-css-classes-with-prefixes/)
* [Stop the cascade](http://markdotto.com/2012/03/02/stop-the-cascade/)
