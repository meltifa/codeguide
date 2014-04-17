# HTML
## HTML5 doctype
```html
<!doctype html>
<html>
  <head>
  </head>
</html>
```
为每个 HTML 页面的第一行添加标准模式（standard mode）的声明，这样能够确保在每个浏览器中拥有一致的展现。
# CSS
## 适当使用`base64`编码图片优化页面性能
```css
.icon { background-image: url(data:image/gif;base64,R0lGODlhBAABAIABAMLBwfLx8SH5BAEAAAEALAAAAAAEAAEAAAICRF4AOw==); }
```
如果一张图片满足以下条件，建议把图片转为base64编码嵌入CSS文件中减少http请求

1. 不能与其他图片以CSS Sprite的形式存在，只能独立
2. 基本上很少被更新
3. 文件尺寸很小，通常在几十字节左右
4. 在网站中大规模使用

[在线转换工具](http://webcodertools.com/imagetobase64converter)
