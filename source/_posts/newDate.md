---
title: Date对象方法总结
date: 2017-07-03 18:31:37
tags: [javascript,lv1]
---
* Date()参数格式：
以 `2017年7月3日，18:31:37// Mon Jul 03 2017 18:31:37 GMT+0800 (CST)` 为例。
	1. 日期时间。时间的格式必须是hh:mm:ss；日期的格式中文英文都可以，中间有分割 `-/,space.` 即可。
```
new Date('7-3-2017 18:31:37');
new Date('2017-7-3 18:31:37');// 我常用
new Date('Jul 3 3017 18:31:37);
```
	2. 年,月,日,时,分,秒
```
new Date(2017,6,3,18,31,37);// 注意月份
```
	3. 时间戳
```
new Date(1499077897000);// 时间戳
```

* 常用的date方法
有get方法，就有相应的set方法
```
var date = new Date(),// 当前时间
	week = date.getDay(),// 星期
	day = date.getDate(),// 日期
	month = date.getMonth() + 1,// 月
	year = date.getFullYear();// 年
	hour = date.getHours();// 小时
	minute = date.getMinutes();// 分
	second = date.getSeconds();// 秒
	time = date.getTime();// 时间戳
```
