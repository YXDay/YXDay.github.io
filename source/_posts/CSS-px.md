---
title: CSS px
date: 2017-03-03 12:52:06
tags:
    - CSS
    - 规范
    - length
---
px在CSS中指CSS像素,是相对于**设备像素**的**相对值**.
在W3C的[Web Style Sheets CSS tips & tricks](https://www.w3.org/Style/Examples/007/units.en.html)中提到

> In fact, CSS requires that 1px must be exactly 1/96th of an inch in all printed output.

所以这就很明白了.
比如iPhone 5使用的是Retina视网膜屏幕，使用2px x 2px的 device pixel 代表 1px x 1px 的 css pixel，所以设备像素数为640 x 1136px，而CSS逻辑像素数为320 x 568px。
需要用的时候,注意换算**像素**比就是了.