---
title: css 细节
tags:
  - css
id: 7
categories:
  - css
date: 2016-08-22 16:35:15
---

1.  position包含块

    *   relative、static包含块由最近的块级框、表单元格或行内块祖先框的**内容边界**构成。
    *   absolute包含块设置为最近的position不是static的祖先元素（可以是任何类型），如果这个祖先元素是块级元素，包含块则设置为该块元素的**内边距边界**，换句话说，就是由边框界定的区域。

2.  百分数数值计算

    *   top、bottom相对于包含块**高度**计算，与此同时padding、margin四个方向的计算**全部**基于包含块**宽度。**
    *   border**不接受**百分数。
    *   height相对于包含块**高度**