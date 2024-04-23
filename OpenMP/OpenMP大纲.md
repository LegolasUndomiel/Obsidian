**核心思想**
- OpenMP通过使用预处理指令来让程序并行化
```cpp
#pragma omp 指令 [子句[子句]…]
```
## 1 常用命令
### 1.1 并行
### 1.2 Reduction
### 1.3 原子操作


## 2 概念术语

- Race condition
- Reduction
- 互斥锁
- 事件同步

## 3 参考文献
- [OpenMP(1)：parallel，for，sections指令的用法](https://blog.csdn.net/qq_40765537/article/details/105962912)
- [OpenMP(4)：一些函数操作](https://blog.csdn.net/qq_40765537/article/details/106035142)
- [OpenMP入门篇-知乎](https://zhuanlan.zhihu.com/p/608946001)
- [OpenMP并行开发（C++）](https://zhuanlan.zhihu.com/p/51173703)
- [多线程使用1--#pragma omp parallel for](https://blog.csdn.net/weixin_44210987/article/details/112388379)
- [OpenMP并行编程指令详解](https://zhuanlan.zhihu.com/p/688331683)
- [C++并行编程探讨分析](https://www.cnblogs.com/carsonzhu/p/17131175.html)