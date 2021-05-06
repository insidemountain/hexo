---
title: sgx
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

## 一句话描述SGX
就是为了安全把enclave里的进程和其他进程隔离开来，其他进程没有办法访问enclave拥有的内存(EPC)。
1. 程序和数据加密进入enclave。
2. enclave内的内存(EPC)也是加密的(MEE实现的)。
3. EPC通过权限控制，阻止enclave之间进程访问。(EPCM标志哪个EPC对应哪个enclave，PRM(enclave mode)隔离了普通和enclave之间)。

### 
