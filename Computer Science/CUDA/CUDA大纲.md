> 思路：
> 1. 整理CUDA知识体系
> 2. 汇总CUDA实践任务，在实践中学习成长
> 3. 整理CUDA学习笔记，每本书、每个课程一个单独的文件
> 4. 汇总CUDA参考资料，及时进行整理分类
> 5. 汇总CUDA高频考点
> 6. 总结CUDA优化技巧

# 1 CUDA知识体系
## 1.1 并行计算

- [ ] 任务拆分
- [ ] 数据无关性检查
- [ ] 确定任务的 ***串行*** 和 ***并行***
- [ ] 编写CUDA程序实现并行计算
## 1.2 CUDA基本结构
[[Parallel Programming in CUDA C]]
[[CUDA Programming Model]]

- cudaMalloc 申请设备内存
- cudaFree 释放设备内存
- cudaMemcpy 数据拷贝
- CUDA程序标准步骤：拷贝数据到GPU、GPU上计算、拷贝数据到CPU
- 在GPU上启动线程，通过内置变量进行线程索引，然后进行计算

## 1.3 线程协作
[[Thread Cooperation]]

## 1.4 CUDA events
[[Constant Memory and Events]]
## 1.5 CUDA内存模型
### 1.5.1 Global memory
### 1.5.2 Shared memory

### 1.5.3 Constant memory
[[Constant Memory and Events]]
### 1.5.4 Register
### 1.5.5 Local memory
### 1.5.6 Texture memory

## 1.6 Atomics
## 1.7 Streams

## 1.8 Multiple GPUs
## 1.9 CUDA Libraries

# 2 CUDA实践任务
## 2.1 基础任务
| 编号  | 任务名称       | 状态  | 备注       | 链接  |
| --- | ---------- | --- | -------- | --- |
| 1   | 设备信息检查     | 完成  |          |     |
| 2   | CUDA错误检查   | 完成  |          |     |
| 3   | CUDA核函数计时  | 完成  | 封装成计时类   |     |
| 4   | 向量加和       | 完成  | 基础CUDA流程 |     |
| 5   | 向量内积       | 完成  | 规约       |     |
| 6   | 矩阵乘法       |     | 共享内存优化   |     |
| 7   | 矩阵转置       |     |          |     |
| 8   | nsight工具使用 |     |          |     |
### 2.1.1 设备信息检查
- [x] 机器上有多张GPU，检测并选择符合要求的GPU
### 2.1.2 CUDA错误检查
- [x] 定义错误检查的宏，头文件中定义，多次使用
### 2.1.3 CUDA核函数计时
- [x] 封装成计时类
### 2.1.4 向量加和
- [x] 熟悉CUDA编程基础流程
	- [x] 申请GPU内存
	- [x] 拷贝数据
	- [x] 核函数计算
	- [x] 拷贝结果
	- [x] 释放GPU内存
- [x] 面向对象+CUDA
	- [x] 管理GPU内存(申请、释放)
	- [x] 在GPU上完成特定计算任务(kernel)
	- [x] 在类中组织指向GPU内存的指针(数据)，实现特定的任务
	- [x] 多个stream，类比组织多个任务队列
### 2.1.5 向量内积
- [ ] 规约算法
### 2.1.6 矩阵乘法
- [CUDA矩阵运算](https://zhuanlan.zhihu.com/p/573271688)
### 2.1.7 矩阵转置
## 2.2 进阶任务
| 编号  | 任务名称   | 状态   | 备注                       | 链接  |
| --- | ------ | ---- | ------------------------ | --- |
| 1   | 卷积     |      |                          |     |
| 2   | Julia集 | 部分完成 | Pybind11封装、零拷贝、OpenGL互操作 |     |
| 3   | 前缀和    |      | 扫描                       |     |
| 4   | 排序     |      |                          |     |
| 5   | 图像处理   |      |                          |     |
| 6   | CUDA库  |      |                          |     |

### 2.2.1 卷积
### 2.2.2 Julia集
- [ ] Pybind11封装
	- [x] CPU单线程计算
	- [ ] OpenMP并行计算(Ubuntu系统存在链接问题)
	- [x] CUDA计算
	- [x] python-matplotlib渲染
- [ ] OpenGL CUDA互操作
	- [ ] OpenGL注册buffer对象到CUDA
	- [ ] OpenGL注册Texture对象到CUDA
- [ ] 零拷贝


- [OpenGL与CUDA互操作方式总结](https://www.cnblogs.com/csuftzzk/p/cuda_opengl_interoperability.html)
- [[Julia集合]]

### 2.2.3 前缀和
### 2.2.4 排序
### 2.2.5 图像处理
### 2.2.6 CUDA库
## 2.3 综合任务
| 编号  | 任务名称     | 状态  | 备注                        | 链接  |
| --- | -------- | --- | ------------------------- | --- |
| 1   | BVH光追    |     | Ray tracing、OpenGL + CUDA |     |
| 2   | FPM程序    |     | 类封装                       |     |
| 3   | LeetCUDA |     |                           |     |
| 4   | 机器学习     |     |                           |     |
| 5   | 物理渲染引擎   |     | MPM                       |     |
### 2.3.1 BVH光追
### 2.3.2 FPM程序
### 2.3.3 LeetCUDA
### 2.3.4 机器学习
### 2.3.5 物理引擎
- 复现物理渲染算法, 用CUDA加速，打包成完整的项目, MPM, FPM, 粒子等等
- Ray Tracing
# 3 CUDA笔记
1. [[CUDA by Example]]
2. [[CUDA编程基础与实践]]
3. [[Programming in parallel with CUDA]]
4. GPU编程与优化
5. Professional CUDA C Programming
6. [[基于CUDA的异构并行计算]]

# 4 CUDA 参考资料
## 4.1 函数指针
- [cuda核函数传入__device__函数指针的例子](https://blog.csdn.net/qq_39148922/article/details/118584059)



# 5 CUDA高频考点



# 6 CUDA优化技巧
