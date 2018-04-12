title: web前端最佳实践（3）
date: 2015-11-28 14:47:31
tags: BestPractices
---
* ##### 代码符合标准
	* 标准的页面会保证正确的渲染
	* 页面容易被搜索引擎搜索，提高搜索排名
	* 提高网站的易用性
	* 网页更好维护和扩展（Validator，HTML Validator 属于Firefox插件）
* ##### 正确闭合标签
	* 所有自闭的标签：area，base，br，col，command，embed，hr，img，input，keygen，link，meta，param，source，track，wbr）
	* HTML规范：XHTML1.0，HTML4.01，HTML5
	* 严禁标签之间交叉嵌套
* ##### 停止使用不标准的标签和属性，简化HTML代码
	* 标签没有实际意义，仅设置样式（不推荐使用）
	* 不推荐使用blink，marquee
	* 让HTML拥有更好的语义
	* 移除不常用的HTML标签
* ##### 样式和结构分离
	* HTML页面链接一个CSS（最优），提高加载速度
	* HTML内嵌CSS（单一页面最佳，减少加载CSS样式文件的请求数目，加快加载速度
	* 内联CSS样式，可以使用JS动态来统一修改，很少使用，JQ中使用其实现动画效果
	* 在CSS样式文件中引用CSS文件，避免使用
* ##### 添加JS禁用提示信息
	* 使用noscrpt，HTML4只在body中起作用，HTML5中可以出现在head中，支持HTML，不支持XHTML
	* 最好使用noscript，采用渐进增强的模式，平稳降级
* ##### 添加必要的meta的标签
	* meta的属性：name，http-equiv，content，charset
	* name和content属性组合，构成名称/值对
	* name中keywords，description最常用
	* http-equiv和content属性结合，构成http命令
	* 其中content-type，default-style，refresh已经确定，content-language，set-cookie 未正式确定
	* charset设置编码
* ##### 常用的meta方法
	* 设置IE浏览器的兼容性
	* 设置页面在移动设备中的显示
	* 设置IE浏览器的固定网站功能
