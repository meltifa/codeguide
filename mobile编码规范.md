## HTML
### HTML5 doctype

```html
<!doctype html>
<html>
  <head>
  </head>
</html>
```

为每个 HTML 页面的第一行添加标准模式（standard mode）的声明，这样能够确保在每个浏览器中拥有一致的展现。

### 使用 HTML5 新增的表单类型优化输入体验

```html
<input type="email">
```

HTML5 新增的表单类型会大大提升用户在填写表单时输入体验，例如指定输入类型为`email`，那么输入法会把 @ 符号放到键盘首页，用户不必再切到符号键盘里找它，其它常用新增的表单类型如下：

* url：url网址
* date：年月日
* datetime：年月日和时间
* time：时间
* month：月份
* week：周
* number：数字
* tel：电话号码
* search：搜索框

####参考

* [w3schools](http://www.w3schools.com/tags/tag_input.asp)
* [苹果官方文档](https://developer.apple.com/library/safari/documentation/AppleApplications/Reference/SafariHTMLRef/Articles/InputTypes.html#//apple_ref/doc/uid/TP40008055-SW1)

## CSS
### 字体设置

```css
body {
    font-family: "Helvetica Neue", Helvetica, STHeiTi, sans-serif;
}
```

iOS 4.0+ 使用英文字体 Helvetica Neue，之前的iOS版本降级使用 Helvetica。

中文字体设置为华文黑体STHeiTi。

需补充说明，华文黑体并不存在iOS的字体库中(http://support.apple.com/kb/HT5484?viewlocale=en_US)，
但系统会自动将华文黑体STHeiTi兼容命中系统默认中文字体黑体-简或黑体-繁：

```
Heiti SC Light 黑体-简 细体
Heiti SC Medium 黑体-简 中黑
Heiti TC Light 黑体-繁 细体
Heiti TC Medium 黑体-繁 中黑
```

* 原生Android下中文字体与英文字体都选择默认的无衬线字体。
* 4.0之前版本英文字体原生Android使用的是Droid Sans，中文字体原生Android会命中Droid Sans Fallback。
* 4.0+ 中英文字体都会使用原生Android新的Roboto字体。
* 其他第三方Android系统也一致选择默认的无衬线字体。

#### 参考阅读
* [Droid, the default font for older versions of Android](http://en.wikipedia.org/wiki/Droid_fonts)
* [Roboto, the default font for newer versions of Android](http://en.wikipedia.org/wiki/Roboto)

### 适当使用`base64`编码图片优化页面性能

```css
.icon { background-image: url(data:image/gif;base64,R0lGODlhBAABAIABAMLBwfLx8SH5BAEAAAEALAAAAAAEAAEAAAICRF4AOw==); }
```

如果一张图片满足以下条件，建议把图片转为base64编码嵌入CSS文件中减少http请求

1. 不能与其他图片以CSS Sprite的形式存在，只能独立
2. 基本上很少被更新
3. 文件尺寸很小，通常在几十字节左右
4. 在网站中大规模使用

[在线转换工具](http://webcodertools.com/imagetobase64converter)
