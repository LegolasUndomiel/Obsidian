> 作者：Jason Sanders
> 出版社：Addison-Wesley
# 1 性能提升
早期，处理器性能提升靠提高单个处理器的时钟频率，从MHz提升到GHz，性能提升1000倍，到GHz时代，功耗发热限制了性能进一步提升

借鉴超算的思路，靠多核并行，提升处理器性能，推出2核、4核、8核处理器

# 2 GPU发展历史
gpu早期用于图形处理，2D显示加速器卡提供基于硬件的位图运算功能

3D图形加速卡主要用于游戏、电影特效，此间还出现了OpenGL，DirectX库，提供了图形硬件编程接口API

早期GPU的主要工作是，根据输入的颜色、位置、纹理坐标等信息，计算屏幕上每个像素点的颜色数值

# 3 GPU通用计算
一些尝试：输入数值实际上不代表颜色值，使用API进行编程计算，计算结果(颜色值)是输入数据计算的结果，程序员可以获得这些结果，把计算任务伪装成渲染过程

局限：输入限制、计算限制(分散位置)、浮点数运算、debug调试、学习图形编程语言(着色语言Shading Language)

# 4 CUDA的历史
动机：为了减轻上述GPU通用计算中的限制，推广GPU在通用计算中的应用

- 传统架构：顶点着色器、像素着色器
- CUDA架构：统一的着色器流水线、支持浮点运算、访问共享内存

CUDA使得人们不再需要把通用计算问题伪装成图形计算问题

# 5 名词索引
- CPU时钟频率
- Multicore Revolution
- Graphics Processing Unit
- 位图运算
- 3D图形
- OpenGL Graphics Pipeline
- DirectX
- 图形硬件可编程功能
	- Vertex Shading Stage
	- Pixel Shading Stage
	- Vertex Shader
	- Pixel Shader
	- 纹理坐标
	- 渲染
	- 计算吞吐量
	- Shading Language
		- GLSL(OpenGL)
		- HLSL(DirectX)
- CUDA
	- 着色器流水线
	- Arithmetic Logic Unit, ALU
	- 共享内存，任意读写内存，访问程序管理的缓存
- Host 默认编译器
- Device CUDA编译器
- 核函数(Kernel)
- Runtime
- 分配/释放内存
	- cudaMalloc
	- cudaFree
	- malloc
	- free
- 访问内存
	- cudaMemcpy
	- memcpy
	- cudaMemcpyDeviceToHost
	- cudaMemcpyHostToDevice
	- cudaMemcpyDeviceToDevice
- CUDA设备
	- cudaGetDeviceCount 数量查询
	- cudaDeviceProp 结构体
	- cudaGetDeviceProperties
	- cudaChooseDevice
	- cudaSetDevice
	- Scalable Link Interface, SLI
- 线程格(Grid)
	- gridIdx
	- gridDim
- 线程块(Block)
	- blockIdx
	- blockDim
	- 硬件限制
- 线程(Thread)
	- threadIdx
	- 硬件限制 maxThreadsPerBlock
- 软件并行化过程 与 硬件实际执行 解耦
- CPU线程管理和调度
- 输出缓冲区
- 共享内存
	- 线程通信协作
	- “高速缓存”
	- 线程同步
	- Race Condition
- volatile类型变量(C/C++)
- 线程同步
	- 线程块中线程同步 $\_\_syncthreads$
	- 确保每个线程执行指令后才能执行后面的语句
- 归约(Reduction)
	- 利用共享内存，先在线程块内运算，再得出最终结果
- CUDA QNX 嵌入式操作系统 自动驾驶
- Thread Divergence 线程发散 部分线程执行命令
- 常量内存 Constant Memory
- 内存带宽
- 内存通信量
- 光栅化 Rasterization
- 光线追踪
- Warp 线程束
	- 步调一致 Lockstep
	- 广播机制
- 缓存
- event API
	- 函数计时
- Texture Memory 纹理内存
	- 只读类型
	- 缓存在芯片上
	- Spatial Locality 空间局部性
	- 绑定纹理到内存缓冲区
	- 清除纹理绑定
	- text1Dfetch
	- tex2D
	- 二维纹理
	- 纹理采样器
- 通用计算 和 渲染模式互操作
	- 渲染依赖于计算结果
	- 渲染帧上执行图像处理
- OpenGL交互
	- 共享数据缓冲区
	- OpenGL缓冲区-注册CUDA共享
	- 数据不需要经过CPU
- cudaChooseDevice
- cudaGLSetGLDevice
- 原子操作
	- 数千个线程访问少量内存位置，会发生大量竞争，相同位置访问串行化，导致效率下降
	- atomicAdd
- -arch=sm_xx编译选项 计算功能集版本支持的编译优化
- 并行性
	- 数据并行性
	- 任务并行性 task parallelism
- stream
	- 设备叠加 device overlap
	- 操作队列
	- cudaMemcpyAsync
	- cudaStreamSynchronize 同步流
	- 宽度优先
	- 内存拷贝引擎
	- 核函数执行引擎
- 页锁定
- cudaHostAlloc 主机内存分配
	- 内存驻留物理内存中，os不会对内存分页并交换到磁盘上
	- 内存不被重定位
	- 直接内存访问
- 虚拟内存
- 流编程模式
- 多GPU
	- 零拷贝内存 Zero-Copy Memory
	- 可移动的固定内存 Portable Pinned Memory
	- 多GPU协作、共享内存等