---
title: repaint和reflow
date: 2017-11-22 14:16:35
tags: [lv2,javascript,html,css,原理]
---

### 浏览器的渲染原理
* 渲染引擎：firefox用的是geoko，chrome用的是webkit
* 过程：
  1. 解析html生成dom tree
    * 浏览器会解析html / js / css
  2. 构建render tree
    * render tree与dom tree的不同：header标签、样式display:none的元素不在render tree里
  3. 布局render tree
  4. 绘制render tree

### repaint重绘
* 当元素的颜色等样式更改时，会触发repaint。

### reflow回流
* 当元素的尺寸，或者说是布局（定位方式、体积、边距）发生了改变，就会倒回去重新渲染，也就是回流reflow。
* reflow比repaint成本要高。
* 导致reflow的具体情况（从网上看到的总结）
  1. 改变窗囗大小
  2. 改变文字大小
  3. 添加/删除样式表
  4. 内容的改变，如用户在输入框中敲字
  5. 激活伪类，如:hover (IE里是一个兄弟结点的伪类被激活)
  6. 操作class属性
  7. 脚本操作DOM：直接操作子节点，也不要频繁的添加修改元素，先把dom节点抽离到内存中进行复杂的操作然后再插入到页面上。
  8. 计算offsetWidth和offsetHeight
  9. 设置style属性：改变样式时最好统一通过class来修改
