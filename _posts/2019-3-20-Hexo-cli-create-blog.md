---
layout: post
title:  "Hexo-cli + gihub 搭建个人博客"
date:   2019-03-20 16:10:30 +0800
categories: blog 
tags:  Hexo github
author: Xu ShiJie
mathjax: false
---




* content
{:toc}
### 利用hexo+github 搭建个人博客

- 搭建环境
	- 进入root 用户
	
		```
			➜ sudo su
			Password:
			sh-3.2#
		```
	- 安装node包
		- 官网下载安装包直接安装，一直下一步
	- 安装淘宝镜像
	
		```
		npm install -g cnpm --registry=https://registry.npm.taobao.org
		```
	- 安装hexo-cli博客
	
		```
		 cnpm install -g hexo-cli
		```
- 新建博客文件夹
	
	```
	mkdir yourBlog // 创建博客文件夹
	```
	
	```
	cd yourBlog	// 进入博客文件夹
	sudo hexo init	// 用hexo脚手架初始化一个hexo博客项目
	```
- Hexo常用命令

	```
	hexo s   //  Run server 启动
	hexo new 'my new post' // Create a new post
	hexo generate //  Generate static files
	hexo deploy //Deploy to remote sites
	```
---	

	



	
- 部署到github
	- 新建一个git仓库放着一会用

- 终端

	```
	cd your blog
	cnpm install --save hexo-deployer-git // 安装hexo插件
	```
	- 设置插件
		
		```
		vim cd _config.yml // 进入配置文件
		```
	- 拉倒最底部

		```
		deploy:
		type:git
		repo:https://github.com/sj-Mike/sj-Mike.github.io.git
		branch:master
		```
	- 执行 清空 && 生成 && 部署

		``` 
		hexo clean && hexo g && hexo d
		```
	- 浏览器访问你的域名 

		-  [https://sj-mike.github.io/](https://sj-mike.github.io/)

---

