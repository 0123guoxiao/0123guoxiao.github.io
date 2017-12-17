---
title: Hexo 博客资源备份方式
date: 2017-12-17 14:59:14
categories: "Github"
tags: [Hexo,Github]
---
# Hexo 博客资源备份方式

## 前置条件
* 安装 Node.js
* 安装 Git
* 拥有 Github 帐号

<!-- more -->

## 操作步骤
### 1. 在 Github 中建立仓库, http://0123guoxiao.github.io
### 2. 创建两个分支：master 与 hexo
#### 2.1 初始化
```github
touch README.md
git init
git add README.md
git commit -m "add README"
git remote add origin https://github.com/0123guoxiao/0123guoxiao.github.io.git
git push -u origin master
```
#### 2.2 在本地新建一个分支：
```github
git branch hexo
```
#### 2.3 切换到你的新分支：
```github
git checkout hexo
```
#### 2.4 将新分支发布在 github 上：
```github
git push origin hexo
```
### 3. 在 github 网站设置 hexo 为默认分支
### 4. Hexo 创建
#### 4.1 在本地 0123guoxiao.github.io 文件夹下通过 Git bash 依次执行
```github
npm install hexo 
hexo init
npm install
npm install hexo-deployer-git
hexo generate  %生成网站%
hexo server    %启动本地服务器%
```
#### 4.2 网站本地预览，地址 http://localhost:4000( port 可在 _config.yml 设定 ）

### 5. Hexo 和 Github 关联
> * 5.1 修改 _config.yml 中的 deploy 参数，分支应为 master；
> * 5.2 hexo generate -deploy(可以简化为 hexo g -d) 生成推送到 github 的 master 分支
> * 5.3 此时访问 0123guoxiao.github.io 即可查看生成的 Blog 内容

### 6. Hexo 源码备份
#### 6.1.  进入本地的 0123guoxiao.github.io 文件夹下
```github
git clone https://github.com/0123guoxiao/0123guoxiao.github.io.git
git add --all
git commit -m "Blog source commit"
git push origin hexo
```
注意第一行代码执行完后分支应为 hexo
至此博客源代码就备份到了 hexo 分支上面。
### 7. 后期维护以及博客更新
在本地对博客进行修改（添加新博文、修改样式等等）后，通过下面的流程进行管理。
```github
git add .
git commit -m "..."
git push origin hexo
hexo g -d
```
前三步指令将改动推送到 GitHub（此时当前分支应为 hexo）。
第四步发布网站更新内容到 master 分支上。
本篇文章即是这样发布的。