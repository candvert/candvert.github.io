---
title: 在手机上使用termux来实现git操作
description: 在手机上使用termux来实现git操作
date: 2024-10-17
lastmod: 2024-10-17
tags:
  - termux
  - git
---
考虑到有时可能接触不到电脑，但是又想在手机上编辑自己的博客并提交到github
<br/>
此时就可以使用termux
<br/>
## 安装
在 [termux](https://github.com/termux/termux-app/releases) 进行下载安装
## 访问文件
termux 安装后默认没有文件权限，运行如下命令
```sh
termux-setup-storage
```
然后便可以通过 `~/storage` 目录访问手机中的文件
## 使用git
运行如下命令进行下载
```sh
pkg update
pkg install git
```
安装后运行 `git config --global --list` 会报错，因为 git 会默认调用分页程序，需要禁用 git 分页器​
```sh
git config --global core.pager ""
```
进行 git 配置
```sh
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
git config --global --list
```
## 生成密钥文件
```sh
ssh-keygen -t rsa -b 4096 -C "leiyue159@gmail.com"
cd
cat ../home/.ssh/id_rsa.pub 
```
## 设置命令别名
```sh
nano ~/.bashrc
```
我将通过 termux 下载的文件都放在 ~/storage/downloads/termux 中
所以在 .bashrc 中输入
```sh
alias cda='/data/data/com.termux/files/home/storage/downloads/termux'
```