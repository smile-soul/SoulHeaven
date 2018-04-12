title: web前端最佳实践（8）
date: 2015-11-28 14:48:04
tags: BestPractices
---
* ##### 高性能JS
	* 避免定义全局变量和函数
	* 把变量和方法封装在一个变量对象里，把全局变量包含在一个局部作用域里面
	* 使用return语句，返回需要公开接口
            var mycurrent = (function(){
            var length = 0;
            function init(){..}
            return {
            init:init;
            }})
    * 避免使用with语句，难以阅读，易造成BUG
    * 避免使用eval
    * 不要编写检测浏览器的代码
    * 事件处理和业务逻辑代码分隔开
    * 配置数据和代码逻辑分离
    * 配置数据和代码逻辑分离，用配置数据代替写死的数据（JSON)
    * 逻辑与结构样式分离
    * JS分离HTML结构
    	* 从服务器端动态获取HTML代码（AJAX)
    	* 通过客户端动态生成页面结构（template标签）
    	* JS模板：Mustache，Underscore，Handlebars，jade，ejs（Template-engine-chooser模板引擎）
    	* 尽量不要在模板中滥用逻辑块
    	* 不要构建太复杂的模板
    	* 使用预编译模板
    * 使用MVC格式：
    	* Backbone,Angularjs,Meteor,Ember,Knockout
	* JS规范：
        * Commonjs：以同步的方式加载模块，使用在nodejs服务器端的环境中居多（使用require加载）
        * AMD：以异步方式加载模块，更多使用在有网络延迟存在的浏览器环境中（使用回调函数），在requirejs和curl中居多
* ##### 严格的编码格式
	* 禁用with关键字
	* 防止意外的全局变量
	* this不要默认指向全局
	* 防止函数重名
	* 安全使用eval
	* 不要在全局中启用严格模式
	* 在已有代码中谨慎启用严格模式
	* 检查工具:JSLint，JSHint
* ##### 合理使用AJAX
	* 明确使用AJAX
		* 前端会根据用户需求动态取得后端数据，然后更新网页界面
		* 期望通过不刷新页面获取任何资源或页面
		* 动态进行用户输入的验证
		* 其他任何期望通过异步方式取得资源的情况
		* 缺陷：使用AJAX都是动态的，没有添加额外的处理，AJAX会破坏后退的按钮
	* 使用成熟的AJAX框架，但是不要忘记原声的AJAX使用
		* jQuery,Dojo,YUI,ExtJS
	* 在AJAX操作过程中，做好和用户的交互
	* 使用JSON做为AJAX传输的数据格式
