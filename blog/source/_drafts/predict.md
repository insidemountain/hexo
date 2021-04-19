---
title: predictor
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

### SFB
wish-branched-slide: https://www.slideserve.com/mireya/wish-branches-combining-conditional-branching-and-predication-for-adaptive-predicated-execution   
wish-branched-paper: https://people.inf.ethz.ch/omutlu/pub/kim\_micro05.pdf
Low-Cost Branch Folding For Embedded Applications With Small Tight Loops: https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.35.7117&rep=rep1&type=pdf
good question and good answer:https://stackoverflow.com/questions/29522431/does-a-branch-misprediction-flush-the-entire-pipeline-even-for-very-short-if-st
eager https://people.cs.clemson.edu/~mark/eager.html
Power7: https://inst.eecs.berkeley.edu//~cs252/sp17/papers/POWER7-Server-IBM2011.pdf
BOOMv3: https://people.eecs.berkeley.edu/~krste/papers/SonicBOOM-CARRV2020.pdf

这里面有一半是动态预测，换句话说是依赖于编译器的，但是RISC-V没有以来于编译器。它是通过译码做到的，在译码的时候，通过判断br指令跳转的时候的偏移，如果偏移足够小，
就用SFB
