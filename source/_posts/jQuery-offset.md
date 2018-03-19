---
title: jQuery offset()
date: 2018-03-19 14:58:37
tags:
    - jQuery
    - 位置
    - 坐标
    - viewport
    - window
    - document
---

## 定义

.offset()方法返回对应元素边框盒（包括外边距）*基于文档*的坐标值。
The .offset() method allows us to retrieve the current position of an element (specifically its border box, which excludes margins) *relative to the document*.

## 核心源码

```js
// Get document-relative position by adding viewport scroll to viewport-relative gBCR
rect = elem.getBoundingClientRect();
win = elem.ownerDocument.defaultView;
return {
    top: rect.top + win.pageYOffset,
    left: rect.left + win.pageXOffset
};
```

getBoundingClientRect返回的是*基于视口*的坐标。
如果不希望属性值随视口变化，那么只要给top、left属性值加上当前的滚动位置（通过window.scrollX和window.scrollY），这样就可以获取与当前的滚动位置无关的（*基于文档的*）常量值。

## 视口，窗口，文档
* 视口（viewport）：当前浏览器可视区域
* 窗口（window）：当前浏览器
* 文档（document）：当前文档


