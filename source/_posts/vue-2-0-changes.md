---
title: vue 2.0 Changes
tags:
  - vue
  - 文档
id: 5
categories:
  - vue
date: 2016-08-22 11:00:56
---

### High Level Changes

*   模板解析不再依赖DOM（除非你使用DOM本身作为你的模板），所以只要你使用字符串模板（&lt;script type="text/x-template"&gt;/*译注：YUI类库自己定义的元素type，用于存放html减少DOM节点*/,内联JavaScript字符串，或者经由单文件组件编译而成的字符串模板），你不再需要面对任何1.x版本中的模板解析局限。然而，如果你（使用el选项）将现存的内容绑定到元素上作为模板，你依旧将面临那些局限。