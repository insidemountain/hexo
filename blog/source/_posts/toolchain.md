---
title: 工具链
date: 2021-03-20 21:56:00
categories:
- LFS
tags:
- os
---
交叉编译是在新的架构上构建新的软件很重要的技术。

## 交叉编译

### 三元组
所谓三元组就是架构-设备-厂家`machine-vendor-os`。   
`machine`代表架构，即CPU的类型。具体可以参照[gcc installing](https://gcc.gnu.org/install/specific.html)。部分常见的`machine`列表如下:  

| cpu | machine | 
| :---: | :------- | 
| intel 64bit | x8664或amd64 |
| MIPS32 Big endian | mips |
| MIPS32 Little endian | mipsel |
| riscv 64bit | riscv64 |

`vendor`用来对工具链的架构进行配置，如无特殊需求配置为`unknown`或者直接省略，比如`riscv64-unknown-elf`。这里我没有十分理解具体作用是什么，等到做lfs的时候理解了，我会放一个例子在这里。

`os`就是用来指定目标的操作系统环境，一般包括系统名称以及基础C库名称。该项可以设定工具链的一些默认行为，例如目标文件格式和连接时自动使用的C库等。例如`riscv64-unkonuw-elf`就是
指定的是文件的格式，而`riscv64-unknown-gnu`就是指定使用的C库。

### build, host, target
`build`：构建gcc编译器的平台系统环境，编译该软件使用的平台。   
`host`：执行 gcc 编译器的平台系统环境，该软件运行的平台。   
`target`：让 gcc 编译器产生能在什么格式运行的平台的系统环境，该软件处理的目标平台。   
下面举一些简单的例子：

| build | host | target | 解释 | 
| :---: | :---- | ---- | ---- |
| x86 | x86 | riscv64 | 使用X86下构建X86的gcc编译器，编译出能在riscv64下运行的程序。 |
| x86 | riscv64 | riscv64 | 使用X86下构建riscv64的gcc编译器，编译出能在riscv64下运行的程序。 |
| x86 | x86 | x86 | 本地编译 |

总结：`build`是build `gcc`(交叉编译器)的平台，也就是，`host`是`gcc`运行的平台，`target`是用编译出来的`gcc`编译其他程序，其他程序运行的平台。   
更具体点将，`build`就是在一个`build`的环境编译出一个`gcc`，这个`gcc`有这样的两个特性。
1. 这个`gcc`可以在`host`的环境下运行(这句话的意思是，被编译出来的`gcc`可以使用`host`的标准库，以及它的二进制文件是可以符合`host`的指令集的)。
2. 这个`gcc`编译出来的程序可以在`target`的环境下运行(这句话的意思是说，该`gcc`的后端是支持`target`架构的，该`gcc`编译出来的可执行文件是支持`target`架构的指令集的)。   

这里就有一个很有意思的事情了，就是最初的`build`环境里的`gcc`需要支持别的平台的后端，不然没有办法编译出交叉编译器。也就引出了两个条件：
1. `build`环境里的gcc是多后端的。  
2. 交叉编译器需的源码是支持`target`的后端的。

### LFS的交叉编译的步骤
#### 准备
环境变量的准备，把下面的配置加到bashrc中。
`
set +h
umask 022
LFS=/mnt/lfs
LC_ALL=POSIX
LFS_TGT=$(uname -m)-lfs-linux-gnu
PATH=/tools/bin:/bin:/usr/bin
export LFS LC_ALL LFS_TGT PATH
`
umask是掩码，022和777亦或得到的值就是新创建的文件或者目录的FileMode。  
PATH添加了/tools/bin。后续安装的可执行文件都安装到/tools/bin处。

#### 编译安装
在构建LFS的时候，真正开始的第一步除开环境的准备(分区等)，就是构建一个供LFS系统使用的GCC。通过三元组的了解，我们知道，当操作系统发生变化的时候，我们需要构建不同的三元组。
虽然LFS使用的源码都是Linux的配套源码，但是为了完全模拟一个真正的新的操作系统的环境构建，我们应该严格按照新的操作系统构建的流程。   
在构建过程中，第一个编译，安装的包是Binutils。

### Binutils
[GNU Binutils](https://www.gnu.org/software/binutils/)是包括汇编器(as)、连接器(link)以及许多用来操作目标文件的工具。它是GNU的一个项目。


### gcc

### 流程

参考：[交叉编译器介绍](https://oscourse-tsinghua.gitbook.io/loongsoncsprj2020-manual/ucore/crosstools)
