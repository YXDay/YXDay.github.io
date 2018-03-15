---
title: 复盘-fix不同node_modules引起的bug
date: 2018-03-15 14:16:04
tags:
    - 复盘
    - 编译
    - node_modules
    - bug
---
# 复盘-fix不同node_modules引起的bug
一份代码,线上的node_modules包是已有的,线下的node_modules包是我近期通过package.json自行yarn得来的.
当我把线下的node_modules包替换到线上时,线上报错,此时线下正常.
顺着错误信息一番debug,乱七八糟的代码使人眼晕,也查不出什么所以然.
此时冷静分析一下:同一份代码,线下正常,线上出错,二者有何区别?
- 环境
- 构建方式
环境不去说他,小概率事件,构建方式有何不同呢,线下是develop构建,而线上是deploy,
二者的差别是,deploy的gulp流程多了rev,compress两个步骤,分而治之,证明是compress出了问题.
compress中的流程继续分而治之,是gulp-uglify这个包除了问题,对比一下,果然,旧的node_modules里gulp-uglify版本为2.0.0,新的为2.1.2,替换之,遂解决.
具体的原因日后再更新.

