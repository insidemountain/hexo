---
title: sed
date: 2021-03-20 21:56:00
categories:
- Linux
- 常用linux命令
---
sed命令的用途以及常见用法。

## Hash

### 基础用途

### 原理


### 奇技淫巧
1. @, &的用法
`sed -e 's@/lib\(64\)\?\(32\)\?/ld@/tools&@g' -e 's@/usr@/tools@g' $file.orig > $file`
sed最常用的分隔符是`\`，其余还可以有``|, @, `, !``，这里用的是@，而&符号代表源的所有的内容，这里的结果就然后第一个`sed`表达式在每个「/lib/ld」,
「/lib64/ld」或者「/lib32/ld」实例前面增加「/tools」。

2. `sed -e '/m64=/s/lib64/lib/' -i.orig gcc/config/i386/t-linux64`
这里有两个点：
1. m64=放在s前面，可以类似于m64=.****lib64改成m64=.*lib其中.*不变。  
2. -i.orig代表要修改文件可以加orig后缀。  
但神奇的是这个命令一次只改了一个文件，执行两次，t-linux64和t-linux64.orig才都被修改了。
