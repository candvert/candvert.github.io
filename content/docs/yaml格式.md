---
title: yaml 格式
description: yaml 格式
date: 2025-10-15
tags:
  - yaml
---
## 基本概念
- 大小写敏感
- 使用缩进表示层级关系
- 缩进的空格数不重要，只要相同层级的元素左对齐即可
## 注释
```yaml
# 这是注释
number: 5 # 行尾注释
```
## 数据结构
YAML 支持的数据结构有三种：对象、数组、纯量
### 对象
对象是一组键值对，使用冒号结构表示：
```yaml
animal: cat
```
转为 JSON 如下：
```json
{ "animal": "cat" }
```
对于下面内容：
```yaml
navbar:
  displayLogo: true
  logo:
    path: /a.png
```
转为 JSON 如下：
```json
{
    "navbar": {
        "displayLogo": true,
        "logo": { "path": "/a.png" }
    }
}
```
### 数组
一组以 - 开头的行构成一个数组：
```yaml
- cat
- dog
- bird
```
转为 JSON 如下：
```yaml
["cat", "dog", "bird"]
```
数组的元素是一个数组：
```yaml
-
  - cat
  - dog
  - bird
```
转为 JSON 如下：
```js
[["cat", "dog", "bird"]]
```
稍微复杂的结构：
```yaml
menu:
  main:
    - name: 文档
      pageRef: /docs
    - name: 博客
      pageRef: /blog
```
转为 JSON 如下：
```json
{
    "menu": {
        "main": [
            { "name": "文档", "pageRef": "/docs" },
            { "name": "博客", "pageRef": "/blog" }
        ]
    }
}
```
### 纯量
包括整数、浮点数、布尔值、Null、日期、时间、字符串
整数：
```yaml
number: 12
```
浮点数：
```yaml
money: 20.5
```
布尔值：
```yaml
hidden: true
```
Null 用 ~ 表示：
```yaml
title: ~
# 也可以将值直接空着表示 Null
description:
```
日期：
```yaml
date: 2025-07-17
```
时间：
```yaml
time: 2025-07-17T15:02:31+08:00
```
## 字符串
字符串可以使用也可以不使用引号：
```yaml
title: 'Book Life'
autor: "Emily"
description: new book released
```
多行字符串：
```yaml
this: |
  Foo
  Bar
```
转为 JSON 如下：
```js
{ "this": "Foo\nBar\n" }
```
`+` 保留末尾的换行，`-` 删除末尾的换行
```yaml
s1: |
  Foo

s2: |+
  Foo

s3: |-
  Foo
```
转为 JSON 如下：
```json
{ "s1": "Foo\n", "s2": "Foo\n\n", "s3": "Foo" }
```