title: web前端最佳实践（10）
date: 2015-11-28 14:48:11
tags: BestPractices
---
* ##### 高性能的JS
	*　xss:跨站点脚本攻击
	*　CSRF:跨站请求伪造，诱导用户发出请求
	*　界面操作劫持：点击劫持和拖放劫持
	* 不要轻易信任用户，输入的内容
	* 不要轻信任何传入的第三方数据
	* DDos攻击：借助于客户/服务器技术，将多个计算机联合起来作为攻击平台，对一个或多个目标发动DDoS攻击，从而成倍地提高拒绝服务攻击的威力
	* 使用html5中的CORS，或者使用白名单或者CookieToken来进行限制
	* 安全使用cookie，js不安全，保存数据最好使用localStorage
	* 如果cookie含有敏感信息，使用Cookie的Secure设置
	* Cookie中的Domain（域）和path（路径），设置这两个属性把范围缩小，避免不相关的路径或者域中访问到cookie
	* 防止网页被其他网站内嵌为iframe
	* 从浏览器兼容性上来说，脚本的方式是目前用来阻止网页被内嵌的最佳方式
	* X-Frame-Options:DENY,SAMEORIGIN,ALLOWFROM uri分别表示禁止，允许相同及特定域页面
	* 仅仅禁止被内嵌，设置X-Frame-Options是最简单有效的方案
* ##### 移动端WEB前端开发最佳实践
	* Safari，Android Browser，Chrome都是以WebKit为核心的
	* 移动设备和PC之间的页面现实存在差异（Safari中定义了viewport）
	* 在移动设备和桌面端WEB前端开发中，事件绑定存在差异（移动触点）
	* 页面控件设计存差异（点触不灵敏，虚拟键盘弹出框）
	* 移动设备的网络带宽普遍比PC慢，移动页面要设置更简洁
* ##### PC页面兼容移动设备
	* 使用流式布局
	* 借助CSS Media queries（媒体查询）技术
	* 使用合适的图片显示兼容方案
	* 保持页面简洁，不要使用页面不兼容的技术（Flash技术降级方案，尽量不使用，使用HTML5 Canvas，避免使用播放，网络连接，存储，访问本地文件等）
	* 设置viewport
            <meta name=viewport content="width=device-width,initial-scale=1">
    * 增加链接和按钮的可操作区域
    * 使用响应式设计框架（bootstrap,Zurb Foundation,Skeleton）
    * 使用工具检查网页的移动设备兼容性:MobiReady,W3C mobileOK Checker,iPadPeek让用户输入测试网址,Howtogomo除了显示截屏还提供建议
* ##### 开发移动WEB站点的准备工作
	* 确定支持的移动设备（尺寸，DPI，内存，CPU性能，常用浏览器版本等）
	* 处理和桌面端主网站的交互（User-Agent，用js判断推荐使用Mobile-Detect,isMobile,提供了很多的接口调用，最简单包括isMobile，isTablet）
	* 设计移动站点为单页模式，避免页面跳转
	* 选择一个合适的前端框架（JQuery-mobile，Sencha Touch，Kendo-UI，Ionic）
	* 如何调试移动页面（chrome自带的DEV，包括设备型号，屏幕尺寸，User Agent等）