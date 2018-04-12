title: web前端最佳实践（2）
date: 2015-11-28 14:46:46
tags: BestPractices
---
* ##### 合并相应的代码文件
	*  YUI Compressor：Java平台开发
	*  WEB Optimization：.NET平台开发
* ##### 前端代码重构
	*  删除无用代码，精简代码（不起作用的CSS样式和废弃的JavaScript函数）
	*  前端代码规范化，把CSS代码放到独立的文件中，在JS定义局部变量，把部分全局变量改变成局部变量
	*  整理基础类库
	*  前端代码模块化，引入面向对象的思想来重构JavaScript代码，进一步明确公有接口和私有接口
	*  提高页面性能：
		* 将部分不影响首页展示的JS文件延迟到页面的加载后加载
		* 删除页面中初始隐藏的区域，改为通过JS按需动态生成
		* 页面中的部分图片延迟加载
		* 调整CSS和JS文件引用顺序，即CSS在前，JS在后
		* 给静态文件设置缓存，使用CSS Sprite，合并背景图
		* 合并和压缩发布后的CSS和JS代码模块
	*  前端重构最佳实践
		* 重构前一定要预测风险，最好先完善自动化测试代码
		* 重构的目的和范围要明确，提高代码的可维护性，可读性和性能
		* 最好先易后难，循序渐进。先修改诸如命名，格式等不涉及具体逻辑的内容
		* 重构过程中要持续测试，在多个浏览器测试，确保重构的部分功能正确。切记大量重构后再进行测试，因为大量重构后基本很难记得重构的逻辑，也可能遗漏部分测试用例
		* 性能提升，先进行检测网站的整体性能并量化，找出性能瓶颈。重构过程中要持续监控性能，并进行对比
* ##### 前端框架的使用
	*  项目需求
		* 调查项目是否需要AJAX操作
		* 是否需要模块化
		* 数据传输格式JSON或者XML
		* 需要支持的浏览器
		* 移动还是普通网站
		* 需要的UI模块（模态窗口，滑块控件，进度条，提示框，分割框，幻灯显示，自动填充）
	*  项目的特点
	*  框架的特点
	*  使用较高的框架（完备：jQuery，YUI，Prototype，Extjs,Mootools。轻量：Mondernizr，Underscorejs，Backbonejs，Rapheaeljs）
* ##### HTML5兼容
	*  编写高质量，标准的HTML（标准校验工具，JSLint）
	*  明确浏览器支持范围
		* Chrome和Safari（Webkit内核）IE Tester（IE兼容测试工具）IE9(IE DevToolbar)
	*  避免浏览器兼容性的问题
		* 先考虑更改方案，使用没有兼容问题的代码
		* 考虑如何兼容的问题
		* 兼容IE，使用IE特有的条件表达式
		* 让兼容的代码独立，提高代码的可维护性
	*  HTML5新特性
		* 新标签的兼容，CSS3的兼容，新增的API（使用html5shiv框架）
		* CSS3本身不支持，会直接忽略
		* 新增加的接口的使用，必须添加条件判断（Modernizr）
		* 多看Can I use
* ##### web性能分析
	*  YSlow，pagespeed
		* 基于不同的规则评定网站整体性能评分
		* 给出提高网页性能的建议
		* 统计页面加载的组件
		* 页面的统计信息视图
		* 相关性能分析工具集：JSLint，Smush.it
	*  Chrome开发工具中有Network，Timeline，Profiles，Aidits
		* Network中可以查看各资源请求和下载所用的时间
		* Timeline可以查看网页渲染和交互过程中个步骤所花费的时间，从资源到JS的解析执行，样式的应用和绘制
		* Profiles中可以查看网页的CPU及内存占有情况报告
		* Audits中提供了各种资源和配置优化的建议和未使用CSS规则的列表
* ##### 代码和资源的压缩和合并
	*  加快代码和资源文件传输的方式
		* CDN分发
		* 缓存
		* 压缩代码和资源文件（最优）
		* Gzip算法（压缩，header可以检查是否开启）
		* JS压缩（UglifyJS压缩和优化，YUI Compressor 仅压缩，Closure Compiler压缩和优化）
		* CSS(CSS Compressor,YUI Compressor)
		* HTML(HtmlCompressor使用时仔细调查和测试，避免压缩工具和破坏)
		* 图片资源压缩（TinyPNG，JPEGmini，ImageOptim）
		* 使用ANT（构建代码和资源压缩任务）
		* grunt压缩（js：grunt-contrib-uglify，css：grunt-contrib-cssmin，图片：grunt-contrib-imagemin）
* ##### 前端代码规范
	*  HTML 标签和属性都小写，属性双引号闭合
	*  层级为4个空格
	*  添加必要的注释
	*  class去父辈为前缀
	*  相同模块放在一起，不同模块进行分类
	*  JS首字母小写，其他字母大写
	*  公有接口首字母大写，私有接口首字母小写
	*  使用带括号包含逻辑块，字符串用单引号标记
	*  函数参数逗号后面加一个空格
	*  添加分号，推荐使用//，不使用/\* \*/