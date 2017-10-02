---
title: hexo + github 创建自己的博客
date: 2017-06-30 16:49:45
tags: hexo
---

之前照着网上的教程，试过github pages，后来看到过许多别人的github博客，加上罗罗的推荐，于是决定折腾个自己的博客，分享一些前端经验，更多的是记录学习过程。

第一篇，来记录下我搭建hexo + github 博客的过程，特别是遇到的坑。

系统：mac os
终端：zsh
必备：node / npm / git

折腾过程：
1. 新建你本地的blog目录
	* 打开命令行终端，输入：`cd 你要放blog目录的地方` ，比如我的就是 `cd desktop`
	* 新建blog目录，`mkdir myblog` ，myblog换成你的名字
	* 打开目录 `cd myblog` 进入下一步 
2. 新建github仓库
	* 在github上创建存放blog的仓库时，**Repository name**一定要是你的账号名称 `你的账号.github.io`，比如我的`CrossJae.github.io` ，我因为一开始用了其他名称出错
3. 安装hexo
	* 全局安装hexo `sudo npm install --unsafe-perm --verbose -g hexo` 
	* 过程可能有点慢，稍等一下，如果不知道是否安装成功，还是检测版本号来验证 `hexo -v` or `hexo version`
4. 初始化hexo `hexo init` 
5. 配置
	* 初始化成功后，myblog目录下会生成 **_config.yml** 配置文件，可以用编辑器进行编辑
	* 最基本的配置只要修改 _config.yml 最后的`deploy`
	```
	deploy:
	   type: git
	   repo: https://github.com/CrossJae/CrossJae.github.io.git
	 branch: master
	```
	* type、repo、branch的 `:` 后面一定要有一个空格，以后需要配置hexo其他内容也是一样的
	* repo填的是github的仓库地址
	* branch填的你放blog的分支
6. 安装依赖 `npm install hexo-deployer-git --save`
7. 生成 `hexo generate`
8. 启用本地服务器查看 `hexo server`
	* 此时在浏览器中打开 localhost:4000 即可看到自己的博客啦
	* 启用服务器方便我们在本地进行博客修改
9. 部署到github `hexo deploy`
	* 此时在浏览器中打开你搭建blog的github仓库地址就可以查看线上博客啦


其他：安装hexo时，也可以用 `npm install hexo -g` 来安装，但不知道是不是os系统的问题，一直有error，就算加了sudo也不行。后来找到一种办法是 `sudo npm install hexo --no-optional` 虽然成功了，但是在后续使用hexo的时候还会报 `Error: Cannot find module './build/Release/DTraceProviderBindings’` ，虽然不影响使用，但还是不能忍受每次有一长串的error，最后删除了hexo `sudo uninstall hexo`，使用`sudo npm install -unsafe-perm --verbose -g hexo`安装成功。









 
