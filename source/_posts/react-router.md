---
title: react-router使用方法
date: 2017-08-14 18:52:28
tags: [react,router,l2]
---

1. 安装router `npm install --save-dev react-router`
2. 在入口文件中引入router `import { Router, Router, hashHistory} from 'react-router'`
3. 普通的路由使用方法
```
ReactDOM.render(
	(
		<Router history={hashHistory}>
			<Route path="/page" component={Page}></Route>
			<Route path="/list" component={List}></Route>
		</Router>
	),
	document.querySelector("#App")
)
```
4. 嵌套路由的使用方法
	* 入口index.jsx
	```
	ReactDOM.render(
		(
			<Router history={hashHistory}>
				<Route path="/" component={App}>
					<Route path="/page" component={Page} />
					<Route path="/list" component={List} />
				</Route>
			</Router>
		),
		document.querySelector("#App")
	)
	```
	* App.jsx,render返回
	```
	return(<div className="wide">{this.props.children}</div>)
	```
5. 嵌套中使用IndexRoute组件
IndexRoute就是根路径`/`时访问的页面
```
ReactDOM.render(
	(
		<Router history={hashHistory}>
			<Route path="/" component={App}>
				<IndexRoute component={Main} />
				<Route path="/page" component={Page} />
				<Route path="/list" component={List} />
			</Route>
		</Router>
	),
	document.querySelector("#App")
)
```
