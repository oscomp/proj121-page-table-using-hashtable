# proj121-page-table-using-hashtable
使用哈希页表实现虚拟机的stage-2页表

### 项目描述

RISC-V指令集以其开源运作模式，获得世界各地研究人员和开发人员的青睐。随着RISC-V社区的发展，以及开源工作的不断努力，目前RISC-V指令已经正式支持虚拟化功能，即H-extension。当前，能够运行虚拟化软件的仿真器以及操作系统都在社区可公开使用。

通过虚拟化相关的项目，可以深入理解软件和硬件在操作系统领域的工作原理。在虚拟化领域，内存，中断，IO，调度是几大研究方向。我们聚焦在内存方向，要求采用哈希页表实现虚拟机的stage-2页表。通过本项目，可帮助学生深入理解虚拟化领域中最复杂的也是最重要内存子系统，掌握虚拟化技术、操作系统原理、以及硬件规范等内容。

该项目通过优化stage-2页表的页粒度和页表机制来降低TLB压力，提升访存性能，间接地降低进程切换开销。


### RISC-V虚拟化相关源码

1. [RISC-V QEMU仿真器以及用户态QEMU](https://github.com/qemu/qemu.git)
2. [RISC-V Linux内核以及支持RISC-V H-extension的Hypervisor](https://github.com/torvalds/linux.git)
3. [RISC-V特权架构规范和非特权架构规范](https://github.com/riscv/riscv-isa-manual)

### 所属赛道

2025全国大学生操作系统比赛的“OS功能”挑战赛道

### 参赛要求

（需要更新）

- 以小组为单位参赛，最多三人一个小组，且小组成员是来自同一所高校的本科生、研究生
- 如学生参加了多个项目，参赛学生选择一个自己参加的项目参与评奖
- 请遵循“2025全国大学生操作系统比赛”的章程和技术方案要求

### 项目导师

高金皓

- github
- email gaojinhao@huawei.com

### 难度

高等

### 特征

- 搭建开发环境，支持RISC-V虚拟机运行在RISC-V Hypervisor上。
- 在RISC-V Hypervisor和RISC-V 仿真器中实现16K粒度的stage-2页表，支持RISC-V Guest OS启动。
- 在RISC-V Hypervisor和RISC-V 仿真器中采用哈希页表作为stage-2页表，支持RISC-V Guest OS启动。

### 参考资料

- 哈希页表相关论文
  - Park, Chang Hyun, et al. "Every Walk's a Hit: Making Page Walks Single-Access Cache Hits." 27th ACM International Conference on Architectural Support for Programming Languages and Operating Systems (ASPLOS’22), February 28-March 4 2022, Lausanne. 2022.
  - Yaniv, Idan, and Dan Tsafrir. "Hash, don't cache (the page table)." ACM SIGMETRICS Performance Evaluation Review 44.1 (2016): 337-350.
  - Barr, Thomas W., Alan L. Cox, and Scott Rixner. "Translation caching: skip, don't walk (the page table)." ACM SIGARCH Computer Architecture News 38.3 (2010): 48-59.

### License

# 预期目标

### 注意：选择本项目的同学也可与导师联系，提出自己的新想法，如导师认可，可加入预期目标

通过调研，可以在RISC-V仿真平台（RISC-V QEMU）上运行RISC-V虚拟机，并以此作为开发环境。影响访存性能的因素较多，从页表的角度来看，细粒度页会增加单位内存的TLB条目数量，导致TLB换入换出开销较大。现有的RISC-V只实现了4K页粒度，对内存需求较大的应用不友好。因此，在RISC-V的仿真器和Hypervisor中实现16K粒度的页表，降低TLB压力，提升TLB命中率以提升访存性能。此外，更为激进的做法除了提升页粒度，还可以减少寻址开销。因此，在RISC-V的仿真器和Hypervisor中实现哈希页表，提升地址翻译的效率。

### 第一题：基本的环境搭建和熟悉

- 用RISC-V仿真平台运行带有RISC-V Hypervisor的Host OS
- 用RISC-V QEMU拉起运行在RISC-V Hypervisor之上的Guest OS

### 第二题：在RISC-V的stage-2中实现16K粒度的页表项格式

- 设计RISC-V stage-2的16K粒度的页表项格式
- 在RISC-V Hypervior的stage-2缺页流程中，建立以16K粒度的页表
- 在RISC-V仿真器中，在stage-2的MMU中实现16K粒度的页表寻址的仿真逻辑

### 第三题：在RISC-V的stage-2中实现哈希页表

- 设计RISC-V stage-2的哈希页表
- 在RISC-V Hypervior的stage-2缺页流程中，实现哈希页表建立过程
- 在RISC-V仿真器中，在stage-2的MMU中实现哈希页表寻址的仿真逻辑
