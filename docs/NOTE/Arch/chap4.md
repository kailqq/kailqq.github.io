---
comments: true
---

# Instruction-Level Parallelism

## Dynamic scheduling

<figure markdown="span">
![image](./img/chap4-1.png)
<figcaption>dynamic scheduling with Scoreboard</figcaption>
</figure>

在RISC-V中，处理器会在ID阶段检查structure hazards和data hazards；

当一条指令可以在没有危险的情况下执行时，它会从ID阶段发出，因为所有的数据危险都已解决

为了支持乱序执行，将ID阶段分成两个阶段

- **Issue(IS)**  这是指令发射的第一阶段，主要功能是解码指令并检查结构冒险(structural hazards),这是一个按序(in-order)的阶段，意味着指令必须按照程序顺序进入这个阶段

结构冒险检查包括：

- 检查是否有可用的功能单元(如ALU、FPU等)
- 检查是否有可用的寄存器文件端口
- 检查是否有可用的保留站(reservation station)空间

- **Read Operands(RO)** 阶段：这是指令发射的第二阶段，主要功能是等待直到没有数据冒险，然后读取操作数
这是一个乱序(out-of-order)的阶段，意味着指令可以在这个阶段以不同于程序顺序的方式执行

在这个阶段：

- 处理器会等待所有数据依赖都被解决
- 一旦数据可用，就会读取操作数
- 指令可以开始执行

### Scoreboard algorithm

Scoreboard的主要组成部分：

- 指令状态表：
  记录每条指令的执行状态
  包括：Issue、Read Operands、Execute、Write Result等阶段

- 功能单元状态表：
  记录每个功能单元(如ALU、FPU等)的状态
  包括：Busy、Op、Fi、Fj、Fk、Qj、Qk、Rj、Rk等字段  


- 寄存器结果状态表：
  记录每个寄存器的状态
  指示哪个功能单元将写入该寄存器



例如下面的例子


```assembly
FLD F6,34(R2)# 将内存地址为34+R2的值加载到F6

FLD F2 45(R3)# 将内存地址为45+R3的值加载到F2

Fmul F0 F2 F4# 将F2和F4相乘，结果存储到F0 RAW

Fsub F8 F6 F2# 将F6减去F2，结果存储到F8  RAW

Fdiv F10 F0 F6# 将F0除以F6，结果存储到F10  RAW

Fadd F6 F8 F2# 将F8和F2相加，结果存储到F6 WAR RAW
```

<figure markdown="span">
![image](./img/chap4-2.png)
![image](./img/chap4-3.png)
![image](./img/chap4-4.png)
</figure>


首先，第一条指令全部执行，Board上没有其信息，第二条指令执行到EX阶段( *各种指令的EX阶段所需时钟周期不一样* ),第三条指令与第二条指令F2数据依赖，不能进入RO；第四条指令与第二条指令F2数据依赖，不能进入RO；第五条指令与第三条指令F0数据依赖，不能进入RO；第六条指令与第四条指令有结构冲突，都要使用加法单元，不能进入IS；

以上的判断都是处理器根据Scoreboard上的信息做出的；

在这个阶段，Integer单元(进行地址计算，整数访问，内存访问的单元)Busy，其对应的指令是Load，Fi是F2，Fj是R3，Rj是no表示已经读取了R3的值，Qj是null表示没有功能单元正在使用R3的值；


根据已有信息，将第三条指令放入IS阶段，更新表，其使用第一个乘法器，所以Fi是F0，Fj是F2，Fk是F4，Qj是Integer，Qk是null，Rj是no，Rk是yes；代表F2即将来自Integer单元，但是没有准备好，F4准备好了，但是没有读取，这条指令不能进入RO阶段；

然后到SUB指令，由于加法单元是空闲的，所以可以进入IS阶段，更新表，Add被使用，Fi是F8，Fj是F6，Fk是F2，Qk是Integer，Rj是yes，Rk是no；代表F6准备好了，F2即将来自Integer单元，但是没有准备好，这条指令不能进入RO阶段；

然后后是DIV指令，除法单元空闲，所以可以进入IS阶段，更新表，Div被使用，Fi是F10，Fj是F0，Fk是F6，Qj是Mult1，Rj是no，Rk是yes；代表F0的数据来自Mult1单元，还没有准备好，F6的已经准备好了，这条指令可以进入RO阶段；

最后是add指令，发现加法单元busy，停在IS阶段，等待加法单元空闲；

寄存器信息来自哪些单元是通过查找寄存器状态表得到，并不断更新；



!!!Note "各个字段的意义"
    1 `Busy`: 功能单元是否正在使用
    
    - yes = 功能单元正忙
    - no = 功能单元空闲

    2 `Op`: 当前执行的操作类型
    
    - Load = 加载操作
    - MUL = 乘法操作
    - SUB = 减法操作
    - DIV = 除法操作

    3 `Fi`: 目标寄存器(存放结果的寄存器)

    4 `Fj`, `Fk`: 源操作数寄存器
    
    - 例如：R3, F2, F4等是源操作数

    5 `Qj`, `Qk`: 产生源操作数的功能单元
    
    - Integer = 整数单元
    - Mult1 = 乘法单元1
    - 如果为空，表示操作数已就绪

    6 `Rj`, `Rk`: 源操作数的就绪状态

    - "yes" = 操作数已就绪但未读取
    - "no" & "Qj = null" = 操作数已读取
    - "no" & "Qj != null" = 操作数未就绪

    寄存器状态表(Register Status)的字段：

    1 寄存器编号：F0, F2, F4等
    
    2 `Qi`: 指示哪个功能单元将会写入该寄存器
    
    - Mult1 = 乘法单元1将写入
    - Integer = 整数单元将写入
    - Add = 加法单元将写入
    - Divide = 除法单元将写入

<figure markdown="span">
![image](./img/chap4-5.png)
![image](./img/chap4-6.png)
</figure>

第二条指令WB后，寄存器状态表更新，此时第三条指令在EX阶段，第四条指令是减法，可以比较快完成，其结束后，ADD指令可以进入到EX阶段，但是由于必须等到DIV阶段进入RO后，才能进入WB阶段，所以ADD指令必须等待，而DIV阶段要进入RO，就必须等待F0的数据准备好，所以DIV指令也要等待；

<figure markdown="span">
![image](./img/chap4-7.png)
![image](./img/chap4-8.png)
</figure>

当MUL指令结束后，FDIV指令进入RO阶段时，ADD指令可以写回，此时没有冲突了，只剩下DIV指令继续执行结束即可；

!!!Example 
    假设EX阶段有以下时钟周期

    - Load： 1
    - MUL： 10
    - SUB/ADD： 2
    - DIV： 40

    其它阶段为1;

    则对于上面的指令，完成的时钟周期为，对于第一条指令，直接顺序完成

    |指令|IS|RO|EX|WB|
    |---|---|---|---|---|
    |FLD F6,34(R2)|1|2|3|4|
    |FLD F2 45(R3)|||||
    |Fmul F0 F2 F4|||||
    |Fsub F8 F6 F2|||||
    |Fdiv F10 F0 F6|||||
    |Fadd F6 F8 F2|||||
    
    由于Integer在第一条指令未结束期间都被占用，所以第二条指令在第一条结束之后才能进入
    
    |指令|IS|RO|EX|WB|
    |---|---|---|---|---|
    |FLD F6,34(R2)|1|2|3|4|
    |FLD F2 45(R3)|5|6|7|8|
    |Fmul F0 F2 F4|||||
    |Fsub F8 F6 F2|||||
    |Fdiv F10 F0 F6|||||
    |Fadd F6 F8 F2|||||

    而IS是需要顺序的，所以第二条指令进入RO阶段，第三条指令才能进入IS，在第二条指令结束之后，第三条指令才能进入RO阶段,之后就继续执行


    |指令|IS|RO|EX|WB|
    |---|---|---|---|---|
    |FLD F6,34(R2)|1|2|3|4|
    |FLD F2 45(R3)|5|6|7|8|
    |Fmul F0 F2 F4|6|9|10-19|20|
    |Fsub F8 F6 F2|||||
    |Fdiv F10 F0 F6|||||
    |Fadd F6 F8 F2|||||

    第四条指令等待Fmul的IS阶段结束之后进入，而其与F2存在冲突，所以也需要等待F2的WB阶段结束再继续进入RO阶段，然后正常执行
    
    |指令|IS|RO|EX|WB|
    |---|---|---|---|---|
    |FLD F6,34(R2)|1|2|3|4|
    |FLD F2 45(R3)|5|6|7|8|
    |Fmul F0 F2 F4|6|9|10-19|20|
    |Fsub F8 F6 F2|7|9|10-11|12|
    |Fdiv F10 F0 F6|||||
    |Fadd F6 F8 F2|||||
    
    第五条指令等待Fmul的WB阶段结束之后进入R0，然后正常执行

    |指令|IS|RO|EX|WB|
    |---|---|---|---|---|
    |FLD F6,34(R2)|1|2|3|4|
    |FLD F2 45(R3)|5|6|7|8|
    |Fmul F0 F2 F4|6|9|10-19|20|
    |Fsub F8 F6 F2|7|9|10-11|12|
    |Fdiv F10 F0 F6|8|21|22-61|62|
    |Fadd F6 F8 F2|||||

    最后一条指令，需要等待Fsub的WB阶段结束后，加法单元被释放，然后进入EX阶段，在这里，需要等待Fdiv的RO结束，F6读走了，才能WB

    |指令|IS|RO|EX|WB|
    |---|---|---|---|---|
    |FLD F6,34(R2)|1|2|3|4|
    |FLD F2 45(R3)|5|6|7|8|
    |Fmul F0 F2 F4|6|9|10-19|20|
    |Fsub F8 F6 F2|7|9|10-11|12|
    |Fdiv F10 F0 F6|8|21|22-61|62|
    |Fadd F6 F8 F2|13|14|15-16|22|











