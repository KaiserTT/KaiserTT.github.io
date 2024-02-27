---
layout: post
title: "From Nand to Tetris: Project 03"
mathjax: true
header-style: text
tags: 
  - CS
  - N2T
---







Project 03 将使用时序逻辑构建一系列的寄存器单元和程序计数器. 使用 Porject 1, 2 中实现过的所有逻辑门以及已实现的 D 触发器 (Data Filp Flop, DFF), 从实现一位寄存器 (Bit) 开始, 逐步实现一个包含 16K 个 16 位寄存器的随机存储器和程序计数器 (Program Counter, PC).



### Bit

一位寄存器的功能如下

``` 
1-bit register:
If load[t] == 1 then out[t+1] = in[t]
                else out does not change (out[t+1] = out[t])
```

代码实现如下

```
CHIP Bit {
    IN in, load;
    OUT out;

    PARTS:
    // Put your code here:
    Mux(a=state, b=in, sel=load, out=tmp);
    DFF(in=tmp, out=out, out=state);
}
```



### Register

这里要实现一个 16 位的寄存器, 可以使用 16 个一位的寄存器来实现.

```
CHIP Register {
    IN in[16], load;
    OUT out[16];

    PARTS:
    // Put your code here:
    Bit(in=in[0], load=load, out=out[0]);
    Bit(in=in[1], load=load, out=out[1]);
    Bit(in=in[2], load=load, out=out[2]);
    Bit(in=in[3], load=load, out=out[3]);
    Bit(in=in[4], load=load, out=out[4]);
    Bit(in=in[5], load=load, out=out[5]);
    Bit(in=in[6], load=load, out=out[6]);
    Bit(in=in[7], load=load, out=out[7]);
    Bit(in=in[8], load=load, out=out[8]);
    Bit(in=in[9], load=load, out=out[9]);
    Bit(in=in[10], load=load, out=out[10]);
    Bit(in=in[11], load=load, out=out[11]);
    Bit(in=in[12], load=load, out=out[12]);
    Bit(in=in[13], load=load, out=out[13]);
    Bit(in=in[14], load=load, out=out[14]);
    Bit(in=in[15], load=load, out=out[15]);
}
```



### RAM8

