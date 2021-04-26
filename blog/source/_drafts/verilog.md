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
今天就把这个弄清楚。我就是要比别人强，理解更深刻，掌握更快速，看得更远
## 为什么会觉得verilog难写？
我觉得有两类问题：  
1. 语言本身，怎么正确地描述一个电路。  
2. 电路知识，亚稳态之类的。

### 语言本身
有几个问题要弄清楚：  
1. 什么时候用assign，什么时候用always？    
2. 什么时候用=，什么时候<=？
3. 什么时候用wire， 什么时候用reg？
4. always里面的敏感信号是电平还是边沿？

### 电路设计
