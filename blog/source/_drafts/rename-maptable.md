---
title: rename
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

## rename
rename的作用是重命名寄存器，目的是为了解决waw和war，以及调度raw。主要包含三个表，maptable，freelist和busytable。主要解决这几个表的更新问题。  
rename有两个阶段，第一个阶段是读maptable获取源物理寄存器，读freelist获取目的物理寄存器，而第二个阶段是读busytable获取忙与否。   
其中第一个阶段的东西已经可以被送到rob里面去了。第二个阶段只是为了issue做准备。

### maptable
maptable是映射表，它的结构是一个32个独立的单元，这三十二个独立的单元，每一个包含一个element和一个element\_copy，这个element就是逻辑寄存器指向的物理寄存器号，而element\_copy则是一个MAX\_BR\_MOUNT长度，32个宽度的寄存器堆，这个是分支预测错误之后回退用的。
还增加了stadle\_pdst当指令完成的时候释放的寄存器。什么时候会被释放，再一次被写的时候。
rollback的备份是不用记录的，因为rollback是一条一条进行的，自己已经记录了对应的物理寄存器。同时呢，例外处理必须是rollback而不能是想分支预测错误一样，直接刷掉，因为很简单，rollback没有什么特征，例外什么时候都可能发生，你没办法记住。

### freelist
freelist负责完成waw和war。
它只分配目的寄存器的物理寄存器，因为很显然源寄存器已经被分配过了。每一条进来的都分配，自然就解决了这两个问题了。


### busytable
busytable是为了表示一个寄存器忙还是不忙，也就是为了发射做准备，一条指令所涉及到的寄存器都不忙，才能发射。

