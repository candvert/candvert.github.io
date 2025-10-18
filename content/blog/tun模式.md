---
title: tun模式
description: tun模式
date: 2025-10-18
lastmod: 2025-10-18
tags:
  - proxy
---
之前我在电脑上安装 google play 时，总是会报错网络问题
<br/>
后来发现必须要使用 tun 模式
<br/>
那什么是 tun 模式呢
## 基本概念
其实 tun 模式就是虚拟网卡，是一种工作在网络层（OSI第三层）的虚拟网络设备技术，其可以代理所有流量
## 为什么要使用tun模式
因为通常使用的系统代理是基于 HTTP/Socks5 等应用层代理协议，但某些应用可能不使用 HTTP/Socks5 等应用层代理协议，而使用 UDP 或其他协议。此时便需要使用 tun 模式代理所有流量