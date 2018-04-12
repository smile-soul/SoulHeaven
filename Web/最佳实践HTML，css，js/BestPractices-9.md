title: web前端最佳实践（9）
date: 2015-11-28 14:48:08
tags: BestPractices
---
* ##### 加快JS文件加载速度
	*　最有效的减少初始加载的文件体积和加载次数
	*　延迟加载：避免代码加载和执行过程阻止页面的解析
	*　尽量把js放在body的底部
	*　使用成熟的加载框架HeadJS，RequireJS，LABjs
	*　最佳实践提高性能：
		* 少用for-in循环
		* 谨慎使用eval
		* 正确使用数组
		* 尽量不使用全局变量
		* 确保解除已经不需要的事件监听，如要那些要移除的DOM对象上绑定的事件
		* 不要在闭包中返回外部不需要的对象
		* 减少变量访问时在作用域链上查找的层级，最好定义为局部变量
* ##### 高效的DOM操作
	* 在浏览器中DOM和ES的实现是分离的
	* 在IE中ES在jscript.dll中，而DOM在mshtml.dll中
	* 在chrome中，使用webkit中的webcore处理DOM和渲染，在V8中处理ES
	* 减少DOM操作的最佳实践：
		* 合并多次的DOM操作为单次的DOM操作
		* 把DOM元素离线或隐藏后修改
			* 使用文档片段
                    var fragment = document.createDocumentFragment();
                    document.getElementById('myElement').appendChild(fragment);
            * 通过设置DOM元素的display样式来设置none来隐藏元素
                    var myElement = document.getElementById('Myelement');
                    myElement.style.display = 'none';
                    .....DOM操作
                    myElement.style.display = 'display';
            * 克隆DOM元素到内存中
                    var myElement = document.getElementById('Myelement');
                    var clone = myElement.cloneNode(true);
                    .....DOM操作
                    myElement.parentNode.replaceChild(clone,myElement);
        * 设置页面具有动画效果的DOM元素的positon：fixed和absolute
        * 谨慎取得DOM元素的布局信息
        	* 把布局信息提取出来，在连续对DOM进行操作，这样会优化连续的DOM操作，这样只会重排一次
        * 使用事件托管方式绑定事件
        	* 绑定事件会占用事件
        	* 浏览器保存事件绑定会占用内存
        	* 采用冒泡机制，只在父元素上绑定事件，用于处理所有的子元素
                    document.getElementById('list').addEventListener("click",function(e){
                    if(e.target && e.target.nodeName.toUpperCase == "LI"){
                    //针对子元素进行处理
                    .....}})
        * 高性能网页，达到理想要求60帧/秒,30帧/秒
        * Timeline：黄色占有很大的部分，则性能瓶颈在JS上，如果内存有异常，则要仔细检查内存溢出
        * 使用测试工具：在线jsPerf，JSLitmus


