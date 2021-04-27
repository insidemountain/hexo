---
title: 准备
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
从现在开始4月27日，每天三个小时：  
1. verilog的题目。  
2. 面试的一些问题总结。    
3. 自己项目的复习，这个每一个模块都要写清楚。  
都要有记录。
面试准备的几个方向：
1. 基础的verilog知识，时序违例，FIFO等。
2. vivado工程怎么建立的。
3. 怎么体现流片的经验，其实流过一次还是不一样，多回忆回忆。
4. RISC-V的项目经验总结一下。

### verilog方面，HDLBits做完，并写一个异步FIFO(这周内)。
序列检测器。
达到随心所欲地实现功能的地步。
testbench的语法。
同步。
阻塞，非阻塞。

### RISC-V方面，去年的基础上再加上后仿的总结。
大不了从头撸一遍。    
fetch:  
decode:     
rename:  
issue:  
regfile\_read:  
exe:  
mem:   
wb:  
特权级:  
我自己的毕业论文:

#### 后仿
两个问题：
1. 门控电路。    
2. 单点故障。  
StuckAt是DFT中的一种故障模型，我们从台积电那边拿到的SRAM IP中有StuckAT，而初始化的时候会对所有的reg以及mem初始化，其中包括控制injectSA的寄存器，这就造成从一开始的模拟故障的点的值就是错的。

### 小宝宝的项目
