---
title: XMLHttpRequest基础知识
date: 2018-06-12 21:43:41
tags: [javascript, l1]
---

1. 解决了什么痛点
之前的浏览器请求，每次返回都是整个页面，传输的数据很大，等待时间也很长，所以使用XMLHttpRequest对象来进行局部更新，只返回所需数据。

2. 原理
通过构建函数生成一个XMLHttpRequest对象，建立请求，浏览器监听响应状态

3. 使用方法
```
const xhr = new XMLHttpRequest();
xhr.open('GET', url, true);
xhr.send();
xhr.onreadystatechange = ()=>{
  if(xhr.readyState === 4 && xhr.status === 200){
    console.log(xhr.responseText);
  }
}
```
