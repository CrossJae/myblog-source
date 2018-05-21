---
title: js中与正则表达式有关系的方法
date: 2018-02-01 19:31:35
tags: [javascript,l2,regexp]
---

#### RegExp对象属性
* global 全局
* ignoreCase 大小写
* lastIndex
* multiline 多行
* source 表达式

#### RegExp对象方法
* compile
* exec
@return 没有匹配 返回null
```
RegExpObject.exec(string)
```
* test
```
RegExpObject.test(string)
```

#### 支持正则表达式的string对象的方法
* search
* match
使用方法：`str.match('需要匹配的字符串 | 正则表达式')`
返回：没有匹配返回 `null`。
有一个匹配项时返回 `["匹配到的字符串", index:3, input: str]`
多个匹配项时（需要配置正则全局g）返回 `['第一个匹配到的字符串', '第二个匹配到的字符串', ...]`
```
stringObject.match(regexp|string)
```
* replace
使用方法：`str.replace('需要替换的字符串 | 正则表达式', '替换后的字符串')`
返回：匹配的 `str` 被修改
```
name = "Doe, John";
name.replace(/(\w+)\s*, \s*(\w+)/, "$2 $1"); // John, Dow
```
* split
