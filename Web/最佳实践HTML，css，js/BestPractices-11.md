title: web前端最佳实践（11）
date: 2015-11-28 14:48:15
tags: BestPractices
---
* ##### 移动端的最佳实践
* HTML最佳实践：
    * 在页面head中添加必要的meta和link信息：
                <!-- 声明文档使用的字符编码 -->
                <meta charset='utf-8'>
                <!-- 优先使用 IE 最新版本和 Chrome -->
                <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1"/>
                <!-- 页面描述 -->
                <meta name="description" content="不超过150个字符"/>
                <!-- 页面关键词 -->
                <meta name="keywords" content=""/>
                <!-- 网页作者 -->
                <meta name="author" content="name, email@gmail.com"/>
                <!-- 搜索引擎抓取 -->
                <meta name="robots" content="index,follow"/>
                <!-- 为移动设备添加 viewport -->
                <meta name="viewport" content="initial-scale=1, maximum-scale=3, minimum-scale=1, user-scalable=no">
                <!-- `width=device-width` 会导致 iPhone 5 添加到主屏后以 WebApp 
                全屏模式打开页面时出现黑边 http://bigc.at/ios-webapp-viewport-meta.orz -->
                <!-- iOS 设备 begin -->
                <meta name="apple-mobile-web-app-title" content="标题">
                <!-- 添加到主屏后的标题（iOS 6 新增） -->
                <meta name="apple-mobile-web-app-capable" content="yes"/>
                <!-- 是否启用 WebApp 全屏模式，删除苹果默认的工具栏和菜单栏 -->
                <meta name="apple-itunes-app" content="app-id=myAppStoreID, 
                affiliate-data=myAffiliateData, app-argument=myURL">
                <!-- 添加智能 App 广告条 Smart App Banner（iOS 6+ Safari） -->
                <meta name="apple-mobile-web-app-status-bar-style" content="black"/>
                <!-- 设置苹果工具栏颜色 -->
                <meta name="format-detection" content="telphone=no, email=no"/>
                <!-- 忽略页面中的数字识别为电话，忽略email识别 -->
                <!-- 启用360浏览器的极速模式(webkit) -->
                <meta name="renderer" content="webkit">
                <!-- 避免IE使用兼容模式 -->
                <meta http-equiv="X-UA-Compatible" content="IE=edge">
                <!-- 不让百度转码 -->
                <meta http-equiv="Cache-Control" content="no-siteapp" />
                <!-- 针对手持设备优化，主要是针对一些老的不识别viewport的浏览器，比如黑莓 -->
                <meta name="HandheldFriendly" content="true">
                <!-- 微软的老式浏览器 -->
                <meta name="MobileOptimized" content="320">
                <!-- uc强制竖屏 -->
                <meta name="screen-orientation" content="portrait">
                <!-- QQ强制竖屏 -->
                <meta name="x5-orientation" content="portrait">
                <!-- UC强制全屏 -->
                <meta name="full-screen" content="yes">
                <!-- QQ强制全屏 -->
                <meta name="x5-fullscreen" content="true">
                <!-- UC应用模式 -->
                <meta name="browsermode" content="application">
                <!-- QQ应用模式 -->
                <meta name="x5-page-mode" content="app">
                <!-- windows phone 点击无高光 -->
                <meta name="msapplication-tap-highlight" content="no">
                <!-- iOS 图标 begin -->
                <link rel="apple-touch-icon-precomposed" href="/apple-touch-icon-57x5-precomposed.png"/>
                <!-- iPhone 和 iTouch，默认 57x57 像素，必须有 -->
                <link rel="apple-touch-icon-precomposed" sizes="114x114" href="/apple-touch-icon-114x14-precomposed.png"/>
                <!-- Retina iPhone 和 Retina iTouch，114x114 像素，可以没有，但推荐有 -->
                <link rel="apple-touch-icon-precomposed" sizes="144x144" href="/apple-touch-icon-144x14-precomposed.png"/>
                <!-- Retina iPad，144x144 像素，可以没有，但推荐有 -->
                <!-- iOS 图标 end -->
                <!-- iOS 启动画面 begin -->
                <link rel="apple-touch-startup-image" sizes="768x1004" href="/splash-screen-768x1004.png"/>
                <!-- iPad 竖屏 768 x 1004（标准分辨率） -->
                <link rel="apple-touch-startup-image" sizes="1536x2008" href="/splash-screen-1536x2008.png"/>
                <!-- iPad 竖屏 1536x2008（Retina） -->
                <link rel="apple-touch-startup-image" sizes="1024x748" href="/Default-Portrait-1024x748.png"/>
                <!-- iPad 横屏 1024x748（标准分辨率） -->
                <link rel="apple-touch-startup-image" sizes="2048x1496" href="/splash-screen-2048x1496.png"/>
                <!-- iPad 横屏 2048x1496（Retina） -->
                <link rel="apple-touch-startup-image" href="/splash-screen-320x480.png"/>
                <!-- iPhone/iPod Touch 竖屏 320x480 (标准分辨率) -->
                <link rel="apple-touch-startup-image" sizes="640x960" href="/splash-screen-640x960.png"/>
                <!-- iPhone/iPod Touch 竖屏 640x960 (Retina) -->
                <link rel="apple-touch-startup-image" sizes="640x1136" href="/splash-screen-640x1136.png"/>
                <!-- iPhone 5/iPod Touch 5 竖屏 640x1136 (Retina) -->
                <!-- iOS 启动画面 end -->
                <!-- iOS 设备 end -->
                <meta name="msapplication-TileColor" content="#000"/>
                <!-- Windows 8 磁贴颜色 -->
                <meta name="msapplication-TileImage" content="icon.png"/>
                <!-- Windows 8 磁贴图标 -->
                <link rel="alternate" type="application/rss+xml" title="RSS" href="/rss.xml"/>
                <!-- 添加 RSS 订阅 -->
                <link rel="shortcut icon" type="image/ico" href="/favicon.ico"/>
                <!-- 添加 favicon icon -->
                <!-- sns 社交标签 begin -->
                <!-- 参考微博API -->
                <meta property="og:type" content="类型" />
                <meta property="og:url" content="URL地址" />
                <meta property="og:title" content="标题" />
                <meta property="og:image" content="图片" />
                <meta property="og:description" content="描述" />
                <!-- sns 社交标签 end -->
    * 利用移动设备的便利性(GPS功能等)
            <a href="tel:1-406-666-xxxx">1-406-666-xxxx</a>
            <a href="sms:1-406-666-xxxx">1-406-666-xxxx</a>
    * 不要使用iframe,谨慎使用table，尽量使用ul，ol代替table来显示数据
    * 如果必须使用table的解决方法：
         * 按照显示数据的优先级，在小屏幕设备中隐藏优先级低的数据列
         * 把表格的横向排列改成纵向排列
         * 链接引入用网页提供的API，内容用XML或者JSON来引入
* CSS最佳实践：
    * 使用相对单位设置尺寸元素
    * 点击控件设置足够大的尺寸
    * 可点控件之间留足够大的空间
    * 尽量少用图片，使用内联图代替小图片
    * 使用图片：web fonts，font Awesome，Bootstrap Glyphicons等
    * 把小图片转化成Base64格式，并借助Data URLs技术把图片直接写在CSS或者HTML文档中，减少图片的请求数目
    * 不要使用伪类hover设置悬停效果
    * 设置合理的字体大小（16px）和行高（1.5px）
    * 在不需要选中文字的区域禁用文字选中功能
* JS最佳实践：
    * 使用移动平台中特有的事件处理（手势触摸touchstart，touchmove，touchend，touchcancel）
    * tap和taphold事件，横竖切换事件（orientationchange）
    * 谨慎使用标准对话框，避免弹出窗口（window.open）
    * 谨慎使用Timer（避免使用准确控制时间的任务）
