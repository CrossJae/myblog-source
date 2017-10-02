---
title: window.onpopstate的用法
date: 2017-07-10 12:15:40
tags: [javascript,l2]
---
`window.onpopstate`是用来监听浏览器的回退前进事件。

与window.onpopstate相关的H5新方法：
1. `history.pushState(state,null,url)` 历史记录中添加一个状态
```example
history.pushState({
	page : 'index',
	id : 1
},null,'index.html');
```
2. `history.replaceState(state,null,url)` 替换一条历史记录
```
history.replaceState({
	page : 'index'
},null,'index.html')
```
在onpopstate事件中，会调取到pushState和replaceState方法中state对象，比如：
```
window.onpopstate = function(e){
	alert(e.state.page);
}
```

**栗子**：给当前页面添加一个历史记录（可跨域）
now.html当前访问的页面添加onpopstate事件
```
window.onpopstate = function(e){
	location.reload();// 回退页面刷新
}
history.replaceState({page : 'other'},null,'other.html');//替换历史状态
history.pushState({page : 'now'},null,'now.html');//创建历史状态
```

other.html跳转页面重定向，实现跨域
```
location.href = 'index.html';//可以跨域
```
