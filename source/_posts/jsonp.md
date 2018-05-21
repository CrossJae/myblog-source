---
title: jsonp
date: 2017-12-12 16:50:08
tags: [javascript,ajax,jsonp]
---

1. 跨域原理
  * 由于script中的src并不受同源策略影响，所以可以根据这一点请求跨域接口，如下，可以拿到服务端返回的数据
  ```
  var apiUrl = '接口地址?callback=callback';

  function callback(data){
    console.log(data)
  }

  var script = document.createElement('script');
  script.src = apiUrl;
  document.body.appendChild(script);
  ```
2. 可以设置callback参数的方法
```
(function(){
  var apiUrl = '接口地址';

  var callbackName = 'Json' + new Date().getTime();

  var url = apiUrl + '&callback=' + callbackName;

  window[callbackName] = function(data){
    console.log(data);
  }

  var script = document.createElement('script');
  script.src = url;
  // script.async = false; // 同步
  document.body.appendChild(script);
})();
```
