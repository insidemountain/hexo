---
title: verilog
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
今天就把这个弄清楚。
## 为什么会觉得verilog难写？
我觉得有两类问题：  
1. 语言本身，怎么正确地描述一个电路。  
2. 电路知识，亚稳态之类的。

### 语言本身
有几个问题要弄清楚：  
1. 什么时候用assign，什么时候用always？    
有两种情况：  
第一，当有时序的时候，一定用always。   
第二，当表达相同的电路的时候，always和assign都可以，是两种风格。  
2. 什么时候用=，什么时候<=？   
=是阻塞，<=是非阻塞，实际除了在initial语句里，<=都是为了生成寄存器用的。
3. 什么时候用wire， 什么时候用reg？  
本质上，wire和reg并没有线或者寄存器(像名字写的那样)的区别，reg和wire完全可以执行一样的功能，都可以综合成线，不同的是reg需要在always块里面，而wire只能在assign的左边。这只是两种不同的代码风格。
4. always里面的敏感信号是电平还是边沿？

### 电路设计
