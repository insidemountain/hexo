---
title: 提纲
date: 2021-03-30 15:24:14
top: false
cover: false
toc: true
mathjax: true
tags:
- 网络
categories:
- 网络
---
Linux虚拟化技术是一块很大的我不太了解的技术。正好通过docker了解一下。    
实验手段的先进决定验证想法的速度，基础知识的多寡决定解决问题的思路，思路的原则与有序决定路径搜索的快慢。暴力出奇迹往往总是获利偏小的方法，即使凑巧解决了问题。  
合适地记录知识或者经验是一件不太容易的事情，很难做到不浪费太多时间的同时又不遗漏重点。记笔记的目的是什么对我来说一直是一个充满怀疑的事情，记录与记忆往往是矛盾的，
过度依赖记录的东西会阻碍对一件事情的熟练度。但是记忆往往不是那么可靠，合适的记录可以避免许多重复的劳动，同时记录的过程本身可以帮助梳理思路，以及写下来的东西总不是
那么好含糊过去，你很难在逻辑不通顺的时候强迫自己落笔，即使自己骗自己在解决急症的时候是那么容易发生。

这篇就当作一个提纲或者草稿，提醒自己梳理记录一下最近两天在网络上学到的东西。   
有一个好的启示，其实这类问题可以归类，其他相关的问题也可以一起记录一下，同时也可以围绕着学习基础知识。

### Iptables的使用，防火墙,D/SNAT,NAT
http://cn.linux.vbird.org/linux_server/0250simple_firewall.php#netfilter

### TCP/IP(http://docs.52im.net/extend/docs/book/tcpip/vol1/1/)
#### TCP/IP的状态，syn\_sentretransmission, rst等什么时候会出现
#### 重传以外的东西拥塞控制，控流，time\_wait过多等。https://zhuanlan.zhihu.com/p/41197705
#### TCP/IP滑动窗口，naggle算法
#### TCP/IP三次四次握手
#### TCP/IP全连接半连接

### Docker,k8s,ingress,cstate怎么访问接收外网的访问以及怎么访问外网？docker 网络模式

### linux对于网络的虚拟化,netnamespace

### 最近学到的很有用的命令
ip netns list
netstat -s
watch
lsns
nsenter
ss
tsar

### 一些和debug相关有用的参数(基本在/proc/sys/net/ipv4)
`net.ipv4.tcp_tw_recycle`
`net.ipv4.tcp_tw_reuse`
`net.ipv4.tcp_tw_timestamp`
`net.ipv4.tcp_synack_retries` 
`tcp_syncookies https://plantegg.github.io/2017/06/07/%E5%B0%B1%E6%98%AF%E8%A6%81%E4%BD%A0%E6%87%82TCP--%E5%8D%8A%E8%BF%9E%E6%8E%A5%E9%98%9F%E5%88%97%E5%92%8C%E5%85%A8%E8%BF%9E%E6%8E%A5%E9%98%9F%E5%88%97/ https://cloud.tencent.com/developer/article/1571796 https://segmentfault.com/a/1190000008224853`半连接，全连接 

### wireshark的使用过滤规则，checksum offload(造成这个的原因)

几个不错debug过程
https://tech.xing.com/a-reason-for-unexplained-connection-timeouts-on-kubernetes-docker-abd041cf7e02
https://valleylord.github.io/post/201601-docker-network/
https://tech.vijayp.ca/linux-kernel-bug-delivers-corrupt-tcp-ip-data-to-mesos-kubernetes-docker-containers-4986f88f7a19
https://coolshell.cn/articles/18654.html#comments
https://blog.box.com/container-networking-mystery-missing-rsts
https://chennima.github.io/blackout-docker-container-with-iptables
