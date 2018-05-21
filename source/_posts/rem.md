---
title: rem适配方案
date: 2017-10-31 22:20:20
tags: [javascript,rem,l2]
---

移动端网页适配时，时常采用rem方法。
原理：以`750px`宽的设计稿为基准，计算出对应的字号，设置html的`fontSize`属性，css中，所有元素的尺寸都以rem为单位，这样可以适配大部分机型，js部分代码如下：
```
var clientWidth = document.documentElement.clientWidth, // 获取浏览器宽度
    fontSize = 10 * 10; // 默认值

if (!clientWidth) return;
if(clientWidth < 1080) {
    fontSize = 100 * (clientWidth / 750);
} else { // 超过1080的宽度时，字号保持不变
    fontSize = 100 * (1080 / 750);
}
```
再将fontSize赋值给html。
但如果系统字号设置成放大，或者是所在的客户端字号放大，很可能导致页面混乱。
针对这种情况，优化的办法是，获取页面html的fontsize属性，对比我们设置的值，如果阈值过大，则重置html的fontsize属性。
```
// 获取元素某种样式属性
function getStyle(obj, attr){
  if(obj.currentStyle) {
    return obj.currentStyle[attr];
  }else{
    return getComputedStyle(obj, false)[attr];
  }
}
var html = document.documentElement;
var changeFontSize = parseInt(getStyle(html, 'fontSize'));
// 阈值暂且设置为2，差异大于2像素，就认定是客户端有放大字号行为，进行重置
if(changeFontSize - fontSize > 2){
  document.documentElement.style.fontSize = ''; // 清除fontSize
  var oriFontSize = parseInt(getStyle(html, 'fontSize')); // 获取页面基准值
  document.documentElement.style.fontSize = parseInt(fontSize) / oriFontSize * 100 + '%'; // 在基准值的基础上设置百分比字号
}
```
几点注意的地方：
1. 必须先清除样式的目的是获取页面基准值，一般不修改客户端字号的情况下，基准值是16px。
2. 重置样式，必须排除em跟px单位（这点不是很理解，实践后不管用），可以设置百分比和pt，相比较百分比比较好设置。
