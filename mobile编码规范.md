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
### 为移动设备设置桌面图标
```html
<link rel="apple-touch-icon" sizes="144x144" href="http://a.tbcdn.cn/mw/s/hi/tbtouch/images/touch-icon.png">
<link rel="apple-touch-icon-precomposed" sizes="114x114" href="http://a.tbcdn.cn/mw/s/hi/tbtouch/images/touch-icon.png">
```
- `apple-touch-icon`属性为原图标增加高光光亮效果
- `apple-touch-icon-precomposed`属性为直接使用原图标
- `sizes`属性指定图标的大小并且分别对应不同的iOS设备，`144x144`对应iPad3以后配备视网膜屏幕的iPad；`114x114`对应iPhone4以后配备视网膜屏幕的iPhone；`72x72`对应没有配备视网膜屏幕的iPad，如iPad1、iPad2、iPad mini1

```html
<link rel="apple-touch-icon-precomposed" href="img/l/apple-touch-icon-precomposed.png">
```
对应非视网膜屏幕的iPhone、 iPod Touch 和 Android 2.1以上的设备
### iOS web app设置
```html
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black">
```
添加图标到桌面后以webapp全屏方式显示，
第二行为在web app应用下状态条（屏幕顶部条）的颜色，默认值为`default`（白色），可以定为`black`（黑色）和`black-translucent`（灰色半透明）
```html
<link rel="apple-touch-startup-image" href="milanoo_startup.png">
```
设置启动界面
官方规定启动界面的尺寸必须为 320*640（px），原本以为Retina屏幕可以支持双倍，但是不支持，图片显示不出来。

## CSS
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
