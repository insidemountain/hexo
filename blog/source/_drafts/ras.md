---
title: rsa改进
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
rsa的功能，在call的时候存入call指令的pc+4，然后等到ret的时候pop跳转到那里去。

而boomv2有什么问题呢？  
1. 在fetch的时候更新rsa。   
2. 当出现分支预测错误的时候rsa就全乱套了。  
3. 当出现call， ret， call的时候就找不回，原来的地址了。

解决方法：  
1. 分支预测的时候跟着rsa的counter和pos。当出现分支预测错误的时候，回退回去。  
2. 仍然是有问题的，因为找不到target，当上述2的pattern出现的时候，就没办法，这个时候就需要一个备份，记着被覆盖的那些内容，也就是call存入的内容。都是分支指令也记住备份的位置，然后把该位置到顶部的部分recover到ras中去。然后把对应的东西在rollback的时候写回去。然后就是例外的时候怎么办？
例外的时候是一样的。相同的代码就可以解决了。
