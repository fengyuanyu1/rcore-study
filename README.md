# rcore-study

[TOC]

---
## Day1(2022-11-09)
第一天开始学习：（21:00-22:20）
### Rustlings在线使用
具体步骤：
1. [入口](https://classroom.github.com/a/U37u3veU)
2. [进入](https://github.com/os2edu/rustlings-fengyuanyu1)
3. 点击Run on Repl.it
4. 进入在线classroom输入以下命令：
```C
curl https://sh.rustup.rs -sSf | sh
# long time
cargo install --path .
# testing
# Push on the "Run" button
```
4. （非第一次进入）环境可以在[该网页](https://replit.com/@fengyuanyu1)重新找到
### 学习Rust语言，尝试完成相关测试
学习Rust语言变量相关知识，并通过Rustlings的变量部分测试。
比较新颖的知识点：同名变量重复命名隐藏、变量默认不可变、常量显式指定类型、宏与函数区别于末尾的感叹号
## Day2(2022-11-10)
第二天开始学习：（08:40-09:40）
### 使用Rustlings报错：
```
# 运行Run按钮
ERROR: No working python installation was found
Please install python and add it to the PATH variable
# 没有重新安装python，于Shell处输入python命令，选择了一个python终端后，Run可以正常使用。

cargo install --path .
# 报错：no override and no default toolchain set
rustup install stable
rustup default stable
```
在线环境中rustlings提示磁盘不够（rustlings Disk quota exceeded），按照某博客删除了rustlings/objects下的文件后发生：fatal: reference is not a tree: tags/5.2.1
转向本地搭建环境。
### 学习Rust语言
比较新颖的知识点：（高级语言常有的）多变量解构（前面被赋值的要加对应的括号）、函数定义位置无关、函数签名（函数声明处）**必须显式**指明参数类型、**表达式**与语句的返回值、函数返回值类型**必须**在箭头后**显式**指定、函数隐式返回最后一个表达式的值、代码的条件表达式**必须返回**bool类型值、所有if分支可能返回值**必须**同类型、loop-while-for循环（for是类似于python的语法，且（1...5）表示1到5的序列）。

## Day3(2022-11-14)
之前有考试，没有记录，看了《Rust权威指南》所有权一章。
### 学习Rust语言（没记录的几天学习的）
比较新颖的知识点：
字符串与String类型（前者简单不可变在栈，后者复杂可变在堆，可变与否的**根本原因**在于不同的内存处理方式）、Rust无GC但可以保证内存安全，所有权使得变量在离开作用域后可以隐式调用drop特殊函数（trait）、Rust隐藏原则一：永不会隐式使用深拷贝，显式用clone方法，简单类型深浅拷贝无差别、复杂类型赋值后**所有权转移**（原引用因所有权自动失效，有高级编译技术那味儿了）、Copy和Drop互斥、**任何简单标量组合**都可以Copy。
### Rustlings在线使用
将Day1的“Rustlings在线使用”中的第3步替换为：Open in GitPod，（之后可以从Dashboard的主页打开之前的环境）

### 学习Rust语言（今日学习），尝试完成相关测试
- 函数参数所有权保留通过引用更加好用，这种通过引用将变量传递给函数的方法称为“借用”
- &表示引用，允许不获得所有权情况下使用该变量
- 引用默认不可变，可以使用&mut来为函数传入可变引用
- 同一（特定）作用域范围内的同一（特定）数据，只能声明一个可变引用
- 数据不能在拥有不可变引用的同时创建可变引用（这个我认为是和C完全不同的）
通过：variable、function、if章节的测试。


## Day4(2022-11-16)
### 今天没有学习Rust语言！
### 学习了RISCV-privileged基本知识：[PPT for RISC-V特权指令级架构](https://content.riscv.org/wp-content/uploads/2018/05/riscv-privileged-BCN.v7-2.pdf)(P1-P15)+[RISC-V手册：一本开源指令集的指南](http://riscvbook.com/chinese/RISC-V-Reader-Chinese-v2p1.pdf)
前者：CSR地址空间、部分地址翻译的知识
后者：
TODO：RISC-V手册第十章没有总结
问题：p105，什么是软件TLB refill？？？？？？


## Day5(2022-11-17)
### 今天没有学习Rust语言！
### 学习了RISCV-privileged基本知识：PPT for RISC-V特权指令级架构（P16-P28）
TODO:PPT for RISC-V特权指令级架构-p21
物理内存的属性：平台和实现所特有的？
将范围映射为总线事务类型，或者是错误。
看到p28页。


## Day6(2022-11-18)
### 学习Rust语言（今日学习）
通过：primitive_type章节的测试。主要内容包括Rust语言字符串等基础类型的built-in方法
- 字符的is_alphabetic、is_numeric方法
- 字符串的len
- 字符串的切片，不包含最后一个索引指向的位置
- 元组a访问第x个元素，写法为a.x-1
通过《Rust权威指南》P101的切片部分
- 切片是一种**不持有所有权**的数据类型
- 字符串切片/常量的类型是&str，String类型变量切片后即为字符串切片
- 字符串的as_bytes属性（获得一个元组），之后添加iter().enumerate()，可以用于循环遍历字符串的每个字节
- String类型的clear方法



[OS实验环境入口](https://github.com/codespaces)



## Day7(2022-11-19)
### 学习Rust语言（今日学习）
《Rust权威指南》第5章（p116前）：
- 结构体实例可变，则其所有字段可变，Rust不允许单独声明其中一部分字段的可变性。
- 字段初始化简写
- 结构体更新语法
- 元组结构体在声明时无须对其字段进行命名
- 



- 闭包的语法P358，vector的vec2练习，用闭包和迭代器重构实现。
- move_semantic1-4的对比，没做出来？？？
- 
- https://rustlang-rustlings-0fiv78puddv.ws-us77.gitpod.io/

## Day8(2022-11-21)
### rCore-tutorial第一章手册学习
开始有一些疑惑，代码都给了还学啥？
正如[应用程序执行环境与平台支持](http://rcore-os.cn/rCore-Tutorial-Book-v3/chapter1/1app-ee-platform.html)一文中执行环境栈所示：
- 无论用户态应用如何编写，是手写汇编代码，还是基于某种高级编程语言调用其标准库或三方库，某些功能总要直接或间接的通过内核/操作系统提供的 系统调用 (System Call) 来实现。

![执行环境栈](http://rcore-os.cn/rCore-Tutorial-Book-v3/_images/app-software-stack.png)

一个程序的成功运行需要标准库、操作系统的支持。而第一章：
- 移除标准库依赖
  - 标准库包含：常用的宏，main函数入口约定，panic_handler错误处理函数
- 构建用户态执行环境，即不依赖于标准库的前提下成功运行程序需要**手动添加**
  - _start入口函数。它会调用了sys_exit函数，向操作系统发出了退出的系统调用请求
  - 手工调用系统调用，因为程序总有执行完成时调用exit的时刻
  - 同时，为了实现输出功能，必须手工调用OS的write系统调用
- 构建裸机执行环境
  - 将上一节中不依赖标准库，直接依赖OS的程序改造：将exit系统调用改为调用RustSBI关机。
    - TODO：疑问：这里是直接调用RustSBI吗，也就是从U直接调用M。
  - 应用程序访问操作系统提供的系统调用的指令是 ecall ，操作系统访问 RustSBI提供的SBI调用的指令也是 ecall ， 虽然指令一样，但它们所在的特权级是不一样的
### rCore-tutorial第一章对应的代码学习
- .cargo/config

```Shell
# build操作的属性，build时的平台目标三元组设定为如下：
# 平台目标三元组 (Target Triplet) 描述了目标平台的 CPU 指令集、操作系统类型和标准运行时库
# http://rcore-os.cn/rCore-Tutorial-Book-v3/chapter1/1app-ee-platform.html#id5
# riscv64gc-unknown-none-elf 的 CPU 架构是 riscv64gc，厂商是 unknown，操作系统是 none（表明是裸机平台）， elf 表示没有标准的运行时库。没有任何系统调用的封装支持，但可以生成 ELF 格式的执行程序。
# 我们不选择有 linux-gnu 支持的 riscv64gc-unknown-linux-gnu，是因为我们的目标是开发操作系统内核，而非在 linux 系统上运行的应用程序。
[build]
target = "riscv64gc-unknown-none-elf"

# 目标的riscv64gc-unknown-none-elf模板中的编译时flag设置
[target.riscv64gc-unknown-none-elf]
rustflags = [
    "-Clink-arg=-Tsrc/linker.ld", "-Cforce-frame-pointers=yes"
]
```
  - src/main.c为第一章中的内核态操作系统
    - TODO:extern "C"，其中的fn bss啥的，只是引用外部符号吗（那为啥不是汇编语言而是C语言呢），具体应该如何理解？

## Day9(2022-11-22)
### rCore-tutorial第一章手册学习
发现一个是手册(http://rcore-os.cn/rCore-Tutorial-Book-v3/)，一个是部分文档构建（https://learningos.github.io/rust-based-os-comp2022/），**前者更为详细**，所以，重看手册第一章，补充部分细节：
- 内核的第一条指令（原理篇）
  - 0x80000000 是由 Qemu 规定的
  - 0x80200000 是RustSBI与内核的约定
  - 需要注意的是，对于不同的 bootloader 而言，下一阶段软件的入口不一定相同，而且获取这一信息的方式和时间点也不同：入口地址可能是一个预先约定好的固定的值，也有可能是在 bootloader 运行期间才动态获取到的值。
  - TODO：最后一部分的叙述有点没搞懂，看实践篇应该就懂了
    - 1.生成的镜像的元数据的问题，这里就是因为QEMU不会识别元数据，它看不见，所以他会直接加载进来导致错误。
    - 2.地址与OS镜像的问题，就是OS镜像的各个段是从低到高还是从高到低？这个要看一下脚本的含义，应该是text最低，逐渐增高？
    - ![经典程序二进制文件布局](http://rcore-os.cn/rCore-Tutorial-Book-v3/_images/MemoryLayout.png)
    - 3.PC从高到低还是从低到高走？
    - > 同时代码段所在的地址应低于其他段。这是因为 Qemu 物理内存中低于 0x80200000 的区域并未分配给内核，而是主要由 RustSBI 使用。
    - 上面的意思就是：0x80200000以下的区域不能让内核用。
  - 内核的第一条指令（实践篇）




0-U，1-S，2-Reserved，3-M
其中保留的特权等级 2 是留给虚拟化用的。在 H 扩展(Hypervisor Extension)中，把 S 模式扩展成 HS 模式(Hypervisor-Extended Supervisor mode)

