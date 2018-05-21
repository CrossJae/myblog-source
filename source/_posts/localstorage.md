---
title: localStorage / sessionStorage
date: 2018-01-31 14:29:56
tags: [lv2,javascript,html5,缓存]
---

### sessionStorage
本地存储，与localStorage不同的只有：数据在页面会话结束的时候被清除。（刷新不是结束会话）
其他方法同`localStorage`
`Cookie`的作用是与服务器进行交互，作为HTTP规范的一部分而存在 ，而Web Storage仅仅是为了在本地“存储”数据而生。

### localStorage
本地存储，解决cookie的存储量只有4k的缺点，大部分浏览器localStorage的存储量是5M。
特点：同源、只支持字符串类型的存储、没有失效时间、在浏览器隐私模式下不可读取、存储内容多会消耗内存空间，导致页面卡顿、
方法：
  * `window.localStorage.setItem("a", 1)`
  * `window.localStorage.getItem("a")`
  * `window.localStorage.clear()`
  * `window.localStorage.removeItem("a")`
  * `window.localStorage.key(i)`

用法：
```
// 存储
window.localStorage["a"] = 1;
window.localStorage.a = 1;
window.localStorage.setItem("a", 1);

// 读取
window.localStorage["a"]
window.localStorage.a;
window.localStorage.getItem("a");

// 删除所有
window.localStorage.clear();

// 删除单个
window.localStorage.removeItem("a");

// 获取键
window.localStorage.key(i);

// json数据需要转成字符串存储
window.localStorgae.setItem("a", JSON.stringify(data));

// 读取的字符串转成json
var jsonObj = JSON.parse(window.localStorage.getItem("a"));
```
