## 1 CUDA介绍
[[Introduction to CUDA]]
[[基于CUDA的异构并行计算]]

### 1.1 并行计算

- [ ] 任务拆分
- [ ] 数据无关性检查
- [ ] 确定任务的 ***串行*** 和 ***并行***
- [ ] 编写CUDA程序实现并行计算

## 2 CUDA基础知识
### 2.1 CUDA基本结构
[[Parallel Programming in CUDA C]]
[[CUDA Programming Model]]

- cudaMalloc 申请设备内存
- cudaFree 释放设备内存
- cudaMemcpy 数据拷贝
- CUDA程序标准步骤：拷贝数据到GPU、GPU上计算、拷贝数据到CPU
- 在GPU上启动线程，通过内置变量进行线程索引，然后进行计算

### 2.2 线程协作
[[Thread Cooperation]]

### 2.3 CUDA events
[[Constant Memory and Events]]
### 2.4 CUDA内存模型
#### 2.4.1 Global memory
#### 2.4.2 Shared memory

#### 2.4.3 Constant memory
[[Constant Memory and Events]]
#### 2.4.4 Register memory
#### 2.4.5 Local memory
#### 2.4.6 Texture memory

## 3 CUDA进阶
### 3.1 Atomics
### 3.2 Streams

### 3.3 Multiple GPUs
### 3.4 CUDA Libraries

## 4 Projects
- 搞一些物理渲染项目, 用CUDA进行加速, MPM, FPM, 粒子等等
- 复现物理渲染算法, CUDA加速
- [CUDA矩阵运算](https://zhuanlan.zhihu.com/p/573271688)
### 4.1 Julia Set
[[Julia集合]]
### 4.2 Ray Tracing
### 4.3 Matrix Class