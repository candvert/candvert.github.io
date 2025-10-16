---
title: Github 个人主页美化
description: Github 个人主页美化
date: 2025-10-15
tags:
  - github
lastmod: 2025-10-16
---
## 原理
在 GitHub 上，如果你创建一个与你的用户名​**​同名的公共仓库​**​（例如，你的用户名是 `Ilya`，那么仓库名就应该是 `Ilya`），那么这个仓库里的 `README.md`文件的内容就会自动显示在你的 GitHub 个人主页的顶部
## 我的配置
```md
<h1 align="center">👋</h1>

<p align="center">
  <samp>
    <a href="https://candvert.top">homepage</a>
  </samp>
</p>

<a href="https://github.com/anuraghazra/github-readme-stats">
  <img height=200 align="center" src="https://github-readme-stats.vercel.app/api?username=candvert&show_icons=true" />
</a>
<img height=200 align="center" src="https://github-readme-stats.vercel.app/api/top-langs/?username=candvert&layout=compact&langs_count=8&card_width=320" />

<a href="https://github.com/candvert/candvert.github.io">
  <img align="center" src="https://github-readme-stats.vercel.app/api/pin/?username=candvert&repo=candvert.github.io" />
</a>
<a href="https://github.com/candvert/candvert">
  <img align="center" src="https://github-readme-stats.vercel.app/api/pin/?username=candvert&repo=candvert" />
</a>
```
## 显示GitHub统计数据
使用 [github-readme-stats](https://github.com/anuraghazra/github-readme-stats) 实现
### 统计卡
将 ?username= 值更改为您的 GitHub 用户名
```md
![Candvert's GitHub stats](https://github-readme-stats.vercel.app/api?username=tokyonight)
```
可以传递查询参数 &hide= 来隐藏任何以逗号分隔的值的特定统计数据
选项：&hide=stars、commits、prs、issues、contribs
```md
![Candvert's GitHub stats](https://github-readme-stats.vercel.app/api?username=candvert&hide=contribs,prs)
```
可以传递查询参数 &show= 来显示任何以逗号分隔的值的特定附加统计数据
选项：&show=reviews,discussions_started,discussions_answered,prs_merged,prs_merged_percentage
```md
![Candvert's GitHub stats](https://github-readme-stats.vercel.app/api?username=candvert&show=reviews,discussions_started,discussions_answered,prs_merged,prs_merged_percentage)
```
要启用图标，您可以在查询参数中传递 &show_icons=true
```md
![Candvert's GitHub stats](https://github-readme-stats.vercel.app/api?username=candvert&show_icons=true)
```
可以指定年份，并通过将 &commits_year=YYYY 传递给参数来仅获取该年份所做的提交
```md
![Candvert's GitHub stats](https://github-readme-stats.vercel.app/api?username=candvert&commits_year=2025)
```
使用内置主题，您可以自定义卡片的外观
使用 &theme=THEME_NAME 参数（一些好看的主题：tokyonight、catppuccin_latte、calm_pink、ambient_gradient）
```md
![Candvert's GitHub stats](https://github-readme-stats.vercel.app/api?username=candvert&show_icons=true&theme=tokyonight)
```
## pin仓库
将 api/pin?username=anuraghazra&repo=github-readme-stats 更改为您的用户名和仓库
```md
[![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=candvert&repo=candvert.github.io)](https://github.com/candvert/candvert.github.io)
```
添加 &show_owner=true 参数会显示仓库所有者
## 显示最多使用的编程语言
将 api/top-langs?username=anuraghazra 更改为您的用户名
```md
![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=candvert)
```