title: web前端最佳实践（7）
date: 2015-11-28 14:48:00
tags: BestPractices
---
* ##### 使用高效的CSS选择器
	* 匹配原理：从右到左
	* 避免使用通配符
	* 避免使用标签和单个属性选择器作为关键选择器
	* 不要再ID选择器前使用标签名
	* 尽量在选择符中定义过多的层级（3）
	* CSScomb排序,CSS selectors Test 选择器性能测试网站
* ##### CSS相关图片处理
	* 不要设置图片的尺寸
	* 使用CSS sprite
		* 缺点：
			* 开发过程繁琐
			* 维护过程复杂
			* 使用不当，导致性能问题
		* 最佳实践：
			* 在项目后期应用CSS Sprite技术
			* 合理组织雪碧图
			* 控制雪碧图的大小和尺寸
			* 合理控制背景图单元之间的距离以及背景图的位置
			* 使用工具：CSS Sprite Generator(Sprite生成器)，Sprite Cow(自动生成CSS代码)，使用SpriteMe代码
* ##### 减少CSS代码量
	* 定义简介的CSS规则
	* 合并相关的CSS规则
	* 定义简介的属性
	* 合并相同的定义
	* 删除无效的定义（增加解析时间）
            font:italic bold 12px georgia serif
            .8em
            \#3ee
* ##### 其他高性能实践
	* 避免使用@imoport
	* 避免使用IE浏览器独有的样式：图片滤镜和CSS表达式
* ##### 浏览器的支持情况
	* 在线工具：CSS3 Click Chart（提供兼容代码的实例），CSS content and browser compatibility
	* 添加前缀：Prefix，AutoPrefix（sublime插件），借助SASS和LESS
	* 不要过度添加前缀
	* 添加CSS3标准属性定义,看html5please