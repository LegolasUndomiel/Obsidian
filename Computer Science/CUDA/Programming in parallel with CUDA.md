# 1 名词索引
- Moore's law
- GPU
- CUDA
- OpenMP
- MPI
- C++ thread
- memory bandwidth
- kernel function
- trapezoidal rule
- compile time directive (pragma)
- reduce operation
- parallel primitive
- hyper-threading
- thrust

# 2 Preface
GPU最早用来提升图形渲染速度，随着游戏工业发展性能越来越强，人们尝试应用GPU进行科学计算，于是有了CUDA的发展。

早起处理器性能提升主要依靠频率，后来过渡到依靠多核，于是有了并行计算的需求。

由于图形渲染要算屏幕上像素的颜色，需要进行大量的并行计算，GPU使得并行计算进入下一阶段。

200倍性能提升意味着，原来一周的计算可以当天完成计算分析，小时级别的任务可以十几秒内完成，可以探索更复杂的模型参数，秒级的任务可以进行模型人机交互。

# 3 Introduction
## 3.1 Background
CPU并行可以用OpenMP，多个CPU之间可以用MPI实现并行，但是使用GPU比用CPU集群更便宜。

GPU的内存速度更快，处理受内存带宽限制的问题中更有优势。

CUDA是类C风格的语言，在C++基础上扩展了一些关键字和修饰词。

## 3.2 梯形积分
OpenMP指令是编译时指令，编译器会将程序分为若干子任务，每个子任务执行在不同的CPU线程上。

规约在并行计算中时常发生，OpenMP中有相应指令，每个子任务先做运算，再得出最终结果。

$\_\_host\_\_$函数运行在CPU上，$\_\_device\_\_$
函数运行在GPU上，一份代码可以同时在CPU和GPU上运行，这是CUDA高明的特征。

$\_\_global\_\_$函数是核函数，由CPU调用，运行在GPU上，函数开始运行即将控制权返还CPU，因此无法返回值，返回值为void；核函数的参数可以是*值*或者*指针*，当参数是指针时，需要提前在GPU上分配空间，只能识别GPU上的指针。