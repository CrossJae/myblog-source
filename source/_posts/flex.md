---
title: flex初体验
date: 2018-03-08 10:22:07
tags: [css3,flex]
---

已经很久没有研究Css3新知识点了，前一阵面试，Css占比较大的题目是“如何垂直居中”，我的回答都是比较原始的办法。某个面试官说，用flex实现垂直居中效果不错，于是决定梳理一下flex的知识点。

首先，是flex垂直居中的解决方案：
```
.contain{
  display:flex;
  align-items:center;
  justify-content:center;
}
```

flex容器的属性
1. flex-direction
2. flex-wrap
3. flex-flow
4. justify-content
5. align-items
6. align-content

flex项目的属性
1. order
2. flex-grow
3. flex-shrink
4. flex-basis
5. flex
6. align-self
