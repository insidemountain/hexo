---
title: issue
date: 2021-03-30 15:24:14
top: false
cover: false
toc: true
mathjax: true
tags:
- verilog
categories:
- verilog
---

## issue
issue主要完成两个任务：   
1. 接收rename之后的指令，存在发射槽内。
2. 侦听结果总线发射指令。

### dispatch
所谓dispatch只是选择那个issue单元而已。

### 侦听(issue)
issue发射的条件：  
1. 满足发射条件，所有的源操作数都准备好。   
2. 目标执行单元为空闲。  
3. 如果有好几条都满足，老的先发射。

### 问题
1. rename的阶段和issue的阶段是怎么衔接的？  
rename2和issue不是并行的，他们是在同一个时钟周期里面的。rename1同时送到rename2和rob。
