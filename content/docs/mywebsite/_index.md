---
linkTitle: 个人网站
title: 个人网站
comments: false
next: /docs/mywebsite/Hugo从零开始创建网站
sidebar:
  open: true
---
网站可以分为静态网站和动态网站两类。
<br/>
静态网站不需要数据库，也就不需要后端。目前有许多静态网站生成器，但我最推荐的是 [Hugo](https://github.com/gohugoio/hugo)。也有很多其他静态网站生成器，比如 astro，hexo，jekyll，typecho，halo 等。对于我来说，Hugo 已经完全满足我的需求了，其他非要选择的话选择 [astro](https://github.com/withastro/astro) ，虽然我还没有尝试过。
<br/>
对于动态网站，如果不想编写代码，那么肯定选 WordPress。因为它太成熟，使用量也最多。如果要自己编写代码，就可以选择 Nextjs、Nuxt 等各种框架。
<br/>
部署方面的话，静态网站推荐 Github Pages。动态网站（不包括 WordPress）推荐 Vercel，Netlify 等部署平台，因为它们会处理 cdn，ssh 证书，ddos 攻击，防火墙等一系列问题。
<br/>
对于 WordPress，如果想在本地开发以便学习和测试，那么需要搭建本地开发环境。推荐使用 [LocalWP](https://localwp.com/) 或小皮面板，其可以一键搭建环境并运行 WordPress。如果要进行上线，WordPress 网站通常使用自托管平台，使用最多的是 [Hostinger](https://www.hostinger.com) 和 [SiteGround](https://world.siteground.com/)。


本部分讲述如何使用 Hugo 创建个人静态网站

<!--more-->

{{< cards >}}
  {{< card link="hugo从零开始创建网站" title="Hugo从零开始创建网站" icon="chart-square-bar" >}}
  {{< card link="使用hextra主题" title="使用hextra主题" icon="sparkles" >}}
{{< /cards >}}