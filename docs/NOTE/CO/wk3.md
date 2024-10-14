# Instructions: Language of the Computer 

## Introduction

- Language of  the machine
    - Instructions(指令)
    - Instruction set(指令集)
  
- Computer Designer  goals
    - Find a language that makes it easy to build hardware and compiler.(简单易用)
    - Maximize performance(同样的资源性能更好)
    - Minimize cost & energy (同样的性能成本更低)
    - Clarity of its application  (易用)
    - Simplicity:  reduce design time (便于设计)

**Our chosen instruction set: RISC V**

???eg "各种指令集的区别"
     <div align=center><img src="https://raw.githubusercontent.com/kailqq/cdn_img/master/img/202410081053826.png" width="60%"></div>



**Von Neumann’ Computer**

如今的计算机是基于两个核心原理构建的：存储程序概念。
这两个原理分别是：

- 指令被表示为数字；
- 程序可以像数字一样存储在内存中，以便读取或写入。

四个设计理念：

1. Simplicity favors regularity 指令集的设计应该尽可能简单，规则。
2. Smaller is faster 尽可能减少指令集的大小，以便提高速度。
3. Good design demands good compromises 设计指令集时，需要权衡各种因素。
4. Make the common case fast 优化常见情况的执行速度。


当设计ISA时，需要**硬件简单--让芯片只实现基本的原语并能快速运行**，**指令要规整**

## Instruction characteristics

指令集的基本结构

operator+operands
<div align=center><img src="https://raw.githubusercontent.com/kailqq/cdn_img/master/img/202410081104617.png" width="60%"></div>


!!!Note
    不同的操作系统，字的长度不同，比如32位系统，字长为32位(4 Byte)，64位系统，字长为64位(8 Byte)。


边界对齐送地址，最后两位是00