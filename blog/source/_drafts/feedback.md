---
title: 反馈
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

### verilog vs chisel
最直观的两个感受：  
1. 代码复用 
1.1 bundle的使用，端口定义的复用。包括，继承，嵌套，重载(改变已有的值)。  
1.2 逻辑的继承，重载。这个一般吧，感觉verilog的module也可以，只不过不能重载。

2. 参数化
这个我感觉我说不清楚，顶层都把参数设置好啦，class如果有implit，例化的时候其实就不需要传参了。这个还是需要再了解了解。


### issue的问题
实际上rename的第二拍压的是issue的第一拍(也就是diapatch)。


### LVT HVT芯片的频率

### 流水级
fetch(3),decode/rename1, rename2/dispatch(issue1), issue2, rrd, exe, mem。
