title: web前端最佳实践（1）
date: 2015-11-28 14:19:45
tags: BestPractices
---
* ##### web前端开发具备的技能
	* HTML
	* CSS
	* 前端编程：JavaScript
	* 跨平台，跨浏览器：IE7,IE8，HTML5特性兼容
	* 前端框架：jquery,AngluarJs,nodejs
	* 调试工具：IE:IE Dev Toolbar，chrome：Developer Tools，Firefox：Firebug
* ##### web前端发展现状
    * 存在问题：
        * 代码组织混乱
        * 代码格式的问题突出
        * 页面布局随意
        * 网站整体性能差，没有意识到应用诸如缓存，动态加载，脚本压缩，图片压缩等提高性能技术
    * 推荐做法：
        * 压缩样式表和脚本文件
        * 减少HTTP请求次数
        * 简洁和符合W3C标准的HTML和CSS代码能减少浏览器解析的时间，加快渲染过程
        * 页面请求数量越少，相对页面的加载速度更快
        * 在JS代码中选择性能更好的实现方案，如延迟加载，动态加载等技术;
    * 延迟加载
            <script type=”text/javascript” src=”" id=”my”></script> 
            <script type=”text/javascript”> 
            setTimeout(“document.getElementById(‘my').src='include/php100.php'; “,3000);//延时3秒 
            </script> 
    * 最后加载
        * 引入外部js脚本文件时，如果放入html的head中,则页面加载前该js脚本就会被加载入页面，而放入body中，则会按照页面从上倒下的加载顺序来运行javascript的代码，所以可以把js外部引入的文件放到页面底部，来让js最后引入，从而加快页面加载速度
    * 动态加载
            <scrīpt src='' id="s1"></scrīpt> 
            <scrīpt language="javascrīpt"> 
            s1.src="test.js" 
            </scrīpt>    