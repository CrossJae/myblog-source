---
title: jsonp & callback
date: 2017-09-27 21:07:01
tags: [lv1,javascript,jsonp,callback]
---
#### jsonp
* 由于ajax进行数据交换时无法实现跨域，所以有了非官方的跨域方法jsonp，利用script的src能访问跨域的js，服务端将数据以json的格式，以回调函数的方式交换数据。
* json只是一种数据格式，如`{name : 'Cross', age : 18}`
* ajax也可以通过其他方式解决跨域问题
* jsonp的简单实现
	1. index.html
	```
	// script
	var callback = function(data){
		console.log('Hello ' + data.name); 
	}
	var script = document.createElement('script');
	script.src = 'data.js';
	document.head.appendChild(script);
	```
	2. data.js
	```
	callback({
		name : 'Cross',
		age : 18
	})
	```

#### 回调函数
* 我们写的代码中，很多地方都有用到回调函数，比如 `setTimeout(function(){...},1000)` 中的匿名函数就是一个回调函数
* 回调函数的含义，就是以函数b作为函数a的参数，在函数a中执行函数b
```
var b = function( name, age ){
	console.log('Hello '+name);
}
var a = function( name, age, callback){
	callback(name,age);
}
a( 'cross', 18, b);
```
* 为了防止传入函数a中的callback参数不是一个函数，需要对callback进行验证后再执行
```
callback && typeof callback === 'function' && callback();
```
* 回调函数是函数式编程最主要的技巧
* 回调函数也是闭包

