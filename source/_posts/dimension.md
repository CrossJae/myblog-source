---
title: offset / client / scroll dimension
date: 2017-09-29 22:21:07
tags: [javascript,lv1]
---

1. offset dimension
	* `offsetWidth` `offsetHeight` `offsetTop` `offsetLeft`
	* `offsetWidth / Height` 包括 **内边距、滚动条、边框** 宽高
	* `offsetTop / Left` 与包含元素`offsetParent`边框的距离
2. client dimension
	* `clientWidth` `clientHeight`
	* 元素的实际宽高，包括 **内边距**
	* 最大的用途就是获取浏览器窗口大小
	```
	function getViewport(){
		if(document.compat == 'BackCompat'){ // 混杂模式
			return(
				width : document.body.clientWidth,
				height : document.body.clientHeight
			)
		}else{
			return(
				width : document.documentElement.clientWidth,
				height : document.documentElement.clientHeight
			)
		}
	}
	```
	* `document.body.clientHeight` 获取的body实际高度
		* 没有滚动条时，获取的高度小于窗口高度
		* 在有滚动条时，获取的高度大于窗口高度
	* `document.documentElement.clientHeight` 获取的是窗口高度，无论有无滚动条
3. scroll dimension
	* `scrollWidth` `scrollHeight` `scrollTop` `scrollLeft`
	* `scrollWidth / Height` 元素总宽高
	* `scrollTop / Left` 滚动隐藏的部分，可以设置元素滚动位置
4. window.innerHeight / outerHeight
	* `innerWidth / Height` 窗口内宽高
	* `outerWidth / Height` 窗口外宽高
	* 移动端 `innerHeight` 返回的是窗口实际高度，不包括各种状态栏，比如微信头部，浏览器返回等，`outerHeight`返回的是0。
	* PC端，`innerHeight` 返回的是窗口高度，不包括浏览器状态栏，`outerHeight` 返回的是整个浏览器高度。
5. screen.availHeight / height
	* `screen.width / height` 屏幕宽高
	* `screen.availWidth / availHeight` 除任务栏以外屏幕宽高
	* 移动端返回的是手机屏幕宽高，pc返回的是pc屏幕宽高
