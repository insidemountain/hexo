---
title: spectre
date: 2021-04-26 15:24:14
top: false
cover: false
toc: true
mathjax: true
tags:
- 前沿
categories:
- 芯片安全
---

### spectre的原理
```
void victim_function(size_t x) {
  if (x < array1_size) {
    tmp &= array2[array1[x] * 512];
  }
}
```
上面是漏洞代码，攻击的方式就是首先flush chache line， 让array1\_size这个常量被flush出cache，然后训练分支预测器，让if语句预测跳转，然后由于分支语句数据依赖一个没在cache的数据，所以后面的语句可以执行，然后让x的值等于密码的值，再乘以512保证不在一个cache line。之后，再通过访问array2这一块的地址，通过访问时间来得到下标，反推出密码是多少。

### 防护方法
最简单的两个方法，一个是每次分支预测错误都flush cache，另一个是不进行分支预测。但是显然，这个性能损失太大了。   
所以尽可能的减小这个性能损失，经过观察，这种攻击方式有一些明显的特征。  
1. 有两条load指令在分支指令下面。   
2. 这两条load指令是数据依赖的。   
3. 这两条load指令的地址不在同一个页面上。  
4. 后面的那条指令L1 Dcache Miss。  
根据这四个特征可以得到一个安全断言，在LSU模块进行检查(本来在LSU也需要检查数据依赖)，当满足这四个条件的时候，就不发射这条指令去访存。直到这个条件被不满足。
