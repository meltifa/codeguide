### 禁用浏览器自动检测网页中可能的电话号码

```html
<meta name="format-detection" content="telephone=no">
```

默认为启用，如果需要禁用此功能则需要加如上代码

### 可视区域（viewport）大小设置

```html
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=3">
```

* `width`：控制 viewport 的大小，可以指定一个值，如 600，`device-width` 为当前设备的屏幕宽度，如无特殊需要，推荐使用 `device-width`
* `height`：和 `width` 相对应，指定高度，一般不需要设置，`device-height` 的作用不再赘述
* `initial-scale`：初始缩放比例，也即是当页面第一次 load 的时候缩放比例
* `maximum-scale`：允许用户缩放到的最大比例
* `minimum-scale`：允许用户缩放到的最小比例
* `user-scalable`：用户是否可以手动缩放，如果需要禁止用户缩放则设置为`user-scalable=no`，如无特殊需要，一般不推荐禁止用户缩放

####参考
* [Mozilla 开发者网站](https://developer.mozilla.org/en/Mobile/Viewport_meta_tag)
* [Apple 开发者网站](http://developer.apple.com/library/safari/#documentation/AppleApplications/Reference/SafariWebContent/UsingtheViewport/UsingtheViewport.html)
* [quirksmode.org上的 viewport 在各个手机浏览器不同之处](http://www.quirksmode.org/mobile/viewports2.html)

### 为移动设备设置桌面图标

```html
<link rel="apple-touch-icon" sizes="144x144" href="http://a.tbcdn.cn/mw/s/hi/tbtouch/images/touch-icon.png">
<link rel="apple-touch-icon-precomposed" sizes="114x114" href="http://a.tbcdn.cn/mw/s/hi/tbtouch/images/touch-icon.png">
```

* `apple-touch-icon`属性为原图标增加高光光亮效果
* `apple-touch-icon-precomposed`属性为直接使用原图标
* `sizes`属性指定图标的大小并且分别对应不同的iOS设备，`144x144`对应iPad3以后配备视网膜屏幕的iPad；`114x114`对应iPhone4以后配备视网膜屏幕的iPhone；`72x72`对应没有配备视网膜屏幕的iPad，如iPad1、iPad2、iPad mini1

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
