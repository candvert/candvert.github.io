---
title: yaml格式
description: yaml的语法
lastmod: 2025-10-15
tags:
  - yaml
---
## 基本概念
- 大小写敏感
- 使用缩进表示层级关系
- 缩进的空格数不重要，只要相同层级的元素左对齐即可
- # 表示注释

```yaml
# 示例
title: Candvert
theme: 'hextra'

menu:
  main:
    - name: 文档
      pageRef: /docs
      weight: 1
    - name: 博客
      pageRef: /blog
      weight: 2

params:
  navbar:
    displayTitle: true
    displayLogo: true
    logo:
      path: 
      link: /
```
## 数据结构
YAML 支持的数据结构有三种：对象、数组、纯量
## 对象
对象是一组键值对，使用冒号结构表示：
```yaml
animal: cat
```
## 数组
一组以 - 开头的行构成一个数组：
```yaml
- a
- b
- c
```
使用行内表示：
```yaml
key: [a, b, c]
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
一个相对复杂的例子：
```yaml
companies:
    -
        id: 1
        name: company1
        price: 200W
    -
        id: 2
        name: company2
        price: 500W
```
## 纯量
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
description: ~
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
字符串可以不使用引号：
```yaml
description: new book released
```
某些情况需要使用引号（单引号或双引号都可）：
```yaml
# 字符串包含特殊字符时​，例如冒号:、井号#、花括号{}、方括号[]、逗号,、或竖线|等
description: 'authors: [Amily, Lucy]'

# 与 YAML 关键字冲突时，例如 true、false、yes、on 等
description: 'that is not true'

# 数字（如 123）、日期（如 2023-12-01），但你希望它被当作普通字符串处理，必须加引号
description: 'number is 236'

# ​字符串首尾有空格时
description: ' value '
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