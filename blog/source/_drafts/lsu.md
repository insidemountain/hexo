---
title: lsu
date: 2021-04-02 16:33:14
top: false
cover: false
toc: true
mathjax: true
tags:
- 私人
categories:
- 计划
---

## Tomasolo算法
本质上，LSU，rename，rob，issue都是为实现tomasolo算法。这几个需要一起看。


### LSU的目的
LSU就是为了解决数据RAW依赖，同时也是存储模型实现的重要方式。

### RISC-V的LSU的实现
主要解决两个问题，st-ld这个就是RAW的问题，LDLD这个东西就是有点多余了，是因为实现的不太行。
