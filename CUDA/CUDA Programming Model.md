> Professional CUDA C Programming
# 1 Introducing the CUDA Programming Model

> Programming models present an abstraction of computer architectures that act as a bridge between an application and its implementation on available hardware. 

CUDA功能
- 通过层次结构组织线程
- 通过层次结构访问内存

并行计算
- 领域层：解析数据和函数
- 逻辑层：如何组织并发线程
- 硬件层：线程如何映射到核心

## 1.1 CUDA编程结构
- 主机：CPU及主机内存
- 设备：GPU及设备内存

**提议**
主机内存变量以 h_ 为前缀，设备内存以 d_ 为前缀

**统一寻址**(unified memory)：连接主机内存和设备内存，使用指针访问CPU和GPU内存，无需彼此之间拷贝数据

