---
title: 使用 hextra 主题
description: 使用 Hugo 的 hextra 主题创建静态网站
date: 2025-10-15
tags:
  - hugo
  - hugo主题
weight: "10"
---

- [推荐配置](#推荐配置)
- [目录结构](#目录结构)

- [front matter](#front%20matter)
- [hugo.yaml](#hugo.yaml)
- [about页面](#about页面)
- [设置网站为中文网站](#设置网站为中文网站)
- [右上角菜单](#右上角菜单)
- [嵌套菜单](#嵌套菜单)
- [左上角徽标与标题](#左上角徽标与标题)
- [左侧边栏额外链接](#左侧边栏额外链接)
- [切换主题](#切换主题)
- [页脚的版权信息](#页脚的版权信息)
- [网站图标](#网站图标)
- [每篇文章编辑链接](#每篇文章编辑链接)
- [每篇文章最后修改时间](#每篇文章最后修改时间)
- [显示标签](#显示标签)
- [页面宽度](#页面宽度)
- [搜索功能](#搜索功能)
- [评论功能](#评论功能)
- [多语言](#多语言)
- [自定义css](#自定义css)
- [自定义脚本](#自定义脚本)
- [自定义页脚额外部分](#自定义页脚额外部分)
- [md文件中的代码块](#md文件中的代码块)

`./hugo new site <site_name> --format yaml`
`cd <site_name>`
`git init`
`git submodule add https://github.com/imfing/hextra themes/hextra`

官方示例网站：[https://imfing.github.io/hextra/zh-cn/](https://imfing.github.io/hextra/zh-cn/)
在 github pages 上部署：[https://imfing.github.io/hextra/zh-cn/docs/guide/deploy-site/](https://imfing.github.io/hextra/zh-cn/docs/guide/deploy-site/)
## 推荐配置
```go
// hugo.yaml
baseURL: https://candvert.github.io/
title: Candvert
theme: 'hextra'

defaultContentLanguage: zh-cn
languageCode: zh-cn

hasCJKLanguage: true

params:
  navbar:
    displayTitle: true
    displayLogo: true
    logo:
      path: 
      link: /
      width: 48
      height: 27

  editURL:
    enable: true
    base: "https://github.com/candvert/candvert.github.io/blob/main/content/"

  displayUpdatedDate: true
  dateFormat: "2006年1月2日"
  
  blog:
    list:
      displayTags: true
  toc:
    displayTags: true

  navbar:
    width: full

  footer:
    enable: true
    displayCopyright: true
    displayPoweredBy: true
    width: normal

menu:
  main:
    - name: 文档
      pageRef: /docs
      weight: 1
    - name: 博客
      pageRef: /blog
      weight: 2
    - identifier: who
      name: 关于
      pageRef: /about
      weight: 3
    - name: 搜索
      weight: 4
      params:
        type: search
    - name: GitHub
      weight: 5
      url: "https://github.com/imfing/hextra"
      params:
        icon: github

  sidebar:
    - name: 更多
      params:
        type: separator
      weight: 1
    - name: "关于"
      pageRef: "/about"
      weight: 2
    - name: "Hugo 文档 ↗"
      url: "https://gohugo.io/documentation/"
      weight: 3

markup:
  highlight:
    noClasses: false
  goldmark:
    renderer:
      unsafe: true
    extensions:
      passthrough:
        delimiters:
          block: [['\[', '\]'], ['$$', '$$']]
          inline: [['\(', '\)']]
        enable: true


// content/_index.md
---
title: Hextra 主题
layout: hextra-home
---
{{< hextra/feature-grid >}}
  {{< hextra/feature-card
    title="轻如羽毛"
    subtitle="使用 Hextra 无需依赖 Node.js。由 Hugo 提供支持，Hugo 是最快的静态网站生成器之一，只需一个二进制文件即可在数秒内创建网站。"
  >}}
{{< /hextra/feature-grid >}}


// content/docs/_index.md
---
linkTitle: 文档
title: 简介
comments: false
---
👋 你好！欢迎来到 Candvert 的文档中心！


// content/blog/_index.md
---
title: "博客"
---


// 普通 md 文件
---
title: "GO"
description: "what"
date: '2024-10-12'
tags: ["Go"]
---


// i18n/zh-cn.yaml
copyright: "© 2025 All Rights Reserved"
poweredBy: "由 Candvert 制作"
```
## 目录结构
```go
// Hextra 为不同类型的内容提供了三种布局：
// content/docs/	适合结构化文档
// content/blog/	用于博客文章，包含列表和详细文章视图
// 其他所有目录	    单页文章视图，无侧边栏

content
├── _index.md                         // <- /
├── docs
│   ├── _index.md                     // <- /docs/
│   ├── getting-started.md            // <- /docs/getting-started/
│   └── guide
│       ├── _index.md                 // <- /docs/guide/
│       └── organize-files.md         // <- /docs/guide/organize-files/
└── blog
    ├── _index.md // <- /blog/
    └── post-1.md // <- /blog/post-1/
```
## front matter
```go
// 设置 BreadCrumb 显示的内容
linkTitle: Foo Bar

// 隐藏 BreadCrumb
breadcrumbs: false

// 侧边栏的排序
weight: 2

// 不在左侧边栏中显示
sidebar:
  exclude: true

// 不显示目录
toc: false

// 创建时间
date: '2024-10-08'

// 最后修改时间
lastmod: '2024-10-12'

// 标签
tags: ['hello']

// 摘要
description: "learn Go"

// 不显示评论
comments: false

// 作者
authors:
  - name: imfing
    link: https://github.com/imfing
    image: https://github.com/imfing.png
  - name: Octocat
    link: https://github.com/octocat
    image: https://github.com/octocat.png

// 从搜索中排除
excludeSearch: true

// 页面编辑链接
editURL: "https://example.com/edit/this/page"
```
## hugo.yaml
```yaml
# 如果 defaultContentLanguage 是 zh-ch、ja、ko，则设置为 true
hasCJKLanguage: true

enableInlineShortcodes: true

params:
  description: Modern, responsive Hugo theme.
  
  banner:
    key: 'announcement-v0.11'
    message: New version Released!

  footer:
    enable: true
    displayCopyright: true
    displayPoweredBy: true
    width: normal

  blog:
    list:
      displayTags: true
      # date | lastmod | publishDate | title | weight
      sortBy: date
      sortOrder: desc # or "asc"
      # Pagination
      pagerSize: 20
    article:
      displayPagination: true

  highlight:
    copy:
      enable: true
      # hover | always
      display: hover

markup:
  highlight:
    noClasses: false
  goldmark:
    renderer:
      unsafe: true
    extensions:
      passthrough:
        delimiters:
          block: [['\[', '\]'], ['$$', '$$']]
          inline: [['\(', '\)']]
        enable: true
```
## about页面
创建 `content/about/index.md` 文件
```yaml
---
title: 关于
toc: false
comments: false
---

这是由 [Candvert](https://github.com/candvert/) 创建的网站，使用 [Hugo](https://gohugo.io/) 的主题 [hextra](https://github.com/imfing/hextra/) 创建。
```
## 设置网站为中文网站
```yaml
defaultContentLanguage: zh-cn
languageCode: zh-cn
```
## 右上角菜单
```yaml
# pageRef 链接到站内页面
# url 链接到外部网址
# weight 调整菜单项的排序

menu:
  main:
    - name: 文档
      pageRef: /docs
      weight: 1
    - name: 博客
      pageRef: /blog
      weight: 2
    - name: 关于
      pageRef: /about
      weight: 3
    - name: 搜索
      weight: 4
      params:
        type: search
    - name: GitHub
      weight: 5
      url: "https://github.com/imfing/hextra"
      params:
        icon: github


# 还可以添加主题切换
menu:
  main:
    - name: Theme Toggle
      params:
        type: theme-toggle
        label: true # 可选，默认为 false

# 还可以添加网站语言切换
menu:
  main:
    - name: 语言切换器
      params:
        type: language-switch
        label: true # 可选，默认为 false
        icon: "globe-alt" # 可选，默认为 "translate"
```
## 嵌套菜单
```yaml
# 通过定义子菜单项可以创建下拉菜单，点击父菜单项时会显示子菜单
# 子菜单项需要通过 parent 参数指定父菜单的 identifier 值
menu:
  main:
    - identifier: sdk
      name: SDK
    - identifier: python
      name: Python ↗
      url: https://python.org
      parent: sdk
    - identifier: go
      name: Go
      url: https://go.dev
      parent: sdk
```
## 左上角徽标与标题
```yaml
title: Like Big Breast

params:
  navbar:
    displayTitle: true
    displayLogo: true
    logo:
      path: /b.png
      dark: /b.png
      link: /
      width: 40
      height: 20
```
## 左侧边栏额外链接
```yaml
menu:
  sidebar:
    - name: 更多
      params:
        type: separator
      weight: 1
    - name: "关于"
      pageRef: "/about"
      weight: 2
    - name: "Hugo 文档 ↗"
      url: "https://gohugo.io/documentation/"
      weight: 3
```
## 切换主题
```yaml
params:
  theme:
    # light | dark | system
    default: system
    displayToggle: false
```
## 页脚的版权信息
创建 `i18n/zh-cn.yaml` 文件
```yaml
copyright: "© 2025 All Rights Reserved"
poweredBy: "由 Candvert 制作"
```
## 网站图标
```go
// 要自定义网站的 favicon，将图标文件放在 static 文件夹下以覆盖主题默认的网站图标
// 如果想增强暗色模式支持，在 static 文件夹中添加 favicon-dark.svg
```
## 每篇文章编辑链接
```yaml
# 编辑链接将基于提供的 URL 作为根目录自动为每个页面生成
params:
  editURL:
    enable: true
    base: "https://github.com/your-username/your-repo/edit/main"
```
## 每篇文章最后修改时间
```yaml
# 使用 Git 提交日期作为来源显示最后修改日期时使用该选项
enableGitInfo: true

params:
  # 显示最后修改日期
  displayUpdatedDate: true
  dateFormat: "2006年1月2日"
```
## 显示标签
```yaml
params:
  blog:
    list:
      displayTags: true
  toc:
    displayTags: true
```
## 页面宽度
```yaml
params:
  page:
    # full (100%), wide (90rem), normal (1280px)
    width: wide



# 导航栏和页脚的宽度
params:
  navbar:
    # full (100%), wide (90rem), normal (1280px)
    width: wide
  footer:
    # full (100%), wide (90rem), normal (1280px)
    width: wide
```
## 搜索功能
```yaml
# 默认启用由 FlexSearch 提供的全文搜索


# 要自定义搜索索引，设置 params.search.flexsearch.index 参数
params:
  # 搜索
  search:
    enable: true
    type: flexsearch

    flexsearch:
      # 索引页面方式: content | summary | heading | title
      index: content
	  tokenize: forward
```
## 评论功能
该主题目前只支持 giscus
giscus 的配置可以从 [giscus.app](https://giscus.app/) 网站生成
```yaml
params:
  comments:
    enable: true
    type: giscus

    giscus:
      repo: <仓库>
      repoId: <仓库 ID>
      category: <分类>
      categoryId: <分类 ID>
	  lang: zh-CN
      # mapping: pathname
      # strict: 0
      # reactionsEnabled: 1
      # emitMetadata: 0
      # inputPosition: top
      # theme: noborder_dark
```
## 多语言
```yaml
languages:
  en:
    languageName: English
    weight: 1
  fr:
    languageName: Français
    weight: 2
  ja:
    languageName: 日本語
    weight: 3
  zh-cn:
    languageName: 简体中文
    languageCode: zh-CN
    weight: 4
    title: Hextra
    params:
	  # 网页顶部的 banner
      banner:
        message: New version released!
```
## 自定义css
```go
// 创建 assets/css/custom.css 文件

// 自定义字体族
.content {
  font-family: "Times New Roman", Times, serif;
}
```
## 自定义脚本
创建 `layouts/_partials/custom/head-end.html` 文件在每个页面添加自定义脚本
```html
<script>
document.addEventListener('DOMContentLoaded', function() {
	var startDate = new Date("2025-10-15 00:00:00");
	var currentDate = new Date();
	var timeDifference = currentDate - startDate;
	var days = Math.floor(timeDifference / (1000 * 60 * 60 * 24));
	document.getElementById("runtime").innerHTML = "本站已稳定运行: " + days + "天 ";
});
</script>
```
## 自定义页脚额外部分
创建 `layouts/_partials/custom/footer.html` 文件来添加页脚的额外部分
添加的部分将出现在页脚的版权部分之前
## md文件中的代码块
```go
// 通过设置 filename 属性可为代码块添加文件名或标题：
// ```python {filename="hello.py"}
// def say_hello():
//     print("Hello!")
// ```


// 通过 base_url 属性可设置基础 URL，该 URL 会与 filename 组合生成可点击的链接
// ```go {base_url="https://github.com/",filename="candvert"}
// go 1.20
// ```


// 设置 linenos=table 可启用行号，并通过 linenostart 指定起始行号：
// ```python {linenos=table,linenostart=42}
// def say_hello():
//     print("Hello!")
// ```


// 通过 hl_lines 属性可高亮指定行号（支持数组格式）：
// ```python {linenos=table,hl_lines=[2,4],linenostart=1,filename="hello.py"}
// def say_hello():
//     print("Hello!")
// def main():
//     say_hello()
// ```
```