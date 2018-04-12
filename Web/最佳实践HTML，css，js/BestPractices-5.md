title: web前端最佳实践（5）
date: 2015-11-28 14:47:39
tags: BestPractices
---
* ##### HTML5新特性使用
	* 使用HTML5中简化的定义方式
		* 定义文档类型声明 <!DOCTYPE html>(标准模式)
		* 定义页面编码
		* 样式和脚本文件的引用
                <link rel="stylesheet" href="...css"/>
	                <script src="...js"></script>
    * async和defer属性
    	* 不使用在内联里面
    	* defer：以并行的方式下载脚本，而不是阻塞的方式下载，在脚本加载完成后，浏览器会在DOM触发之前按照引用顺序运行JS
    	* async：以异步的方式下载脚本，在下载结束后立即执行代码，而不会等待页面解析结束
    	* 在设置async时候，推荐同时设置defer属性，提高脚本加载执行的性能
    * base的target属性
    * input和textarea中的placeholder，required，autofocus
    * 标签上的自定义属性data-\*
    * script可以编写HTML模板和XML数据
    * 音频的兼容：
    	![](http://121.42.163.236/img/1.png)
    * 视频的兼容：
       ![](http://121.42.163.236/img/2.png)

