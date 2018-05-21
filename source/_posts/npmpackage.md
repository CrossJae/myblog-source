---
title: 编译环境中的几种传参方法
date: 2018-01-14 08:41:20
tags: [javascript,npm,l3,package,webpack]
---

### 在package中获取参数
1. package.json中通过`$1`获取参数
```
"script": {
  "dev": "echo $1" // ${1} 也可以
}
```
2. cli中运行
```
npm run dev -- hello
```
3. cli输出结果
```
hello
```

### 修改`process.argv`
1. package.json中配置
```
"script": {
  "dev": "webpack"
}
```
2. webpack中获取参数
```
console.log('自定义参数：', process.argv);
```
3. cli中运行
```
npm run dev -- hello
```
4. cli输出结果
```
自定义参数：PROJECTDIR:  [ '/usr/local/bin/node',
  '/Users/xxx/Desktop/git/webpack-practise/node_modules/.bin/webpack',
  ‘hello' ]
```

### 修改`process.env`方法1，package.json配置如上
1. webpack中获取参数
```
console.log('自定义参数：', process.env.test);
```
2. cli中运行
```
test=hello npm run dev
```
3. cli输出结果
```
自定义参数：hello
```

### 修改`process.env`方法2，package.json配置如上（目前采用这个方法）
1. webpack中获取参数
```
console.log('自定义参数：', process.env.npm_config_test);
```
2. cli中运行
```
npm run dev --test=hello
```
3. cli输出结果
```
自定义参数：hello
```
