---
media: https://www.bilibili.com/video/BV1Ni4y1o7Au?p=3
tags:
  - OpenGL
  - 计算机图形学
---
# 1 视频笔记
- [00:52](https://www.bilibili.com/video/BV1Ni4y1o7Au?p=3&t=52.487437#t=52.49) ![[S03.使用现代OpenGLPT52.487S.jpeg|S03.使用现代OpenGL - 00:52|800]] Direct
- [02:03](https://www.bilibili.com/video/BV1Ni4y1o7Au?p=3&t=123.165498#t=02:03.17) ![[S03.使用现代OpenGLPT2M3.165S.jpeg|S03.使用现代OpenGL - 02:03|800]] 
- [02:14](https://www.bilibili.com/video/BV1Ni4y1o7Au?p=3&t=134.379002#t=02:14.38) ![[S03.使用现代OpenGLPT2M14.379S.jpeg|S03.使用现代OpenGL - 02:14|800]] OpenGL由显卡制造商实现
- [02:28](https://www.bilibili.com/video/BV1Ni4y1o7Au?p=3&t=148.275784#t=02:28.28) ![[S03.使用现代OpenGLPT2M28.276S.jpeg|S03.使用现代OpenGL - 02:28|800]] 
- [02:29](https://www.bilibili.com/video/BV1Ni4y1o7Au?p=3&t=149.918905#t=02:29.92) ![[S03.使用现代OpenGLPT2M29.919S.jpeg|S03.使用现代OpenGL - 02:29|800]] 
- [02:36](https://www.bilibili.com/video/BV1Ni4y1o7Au?p=3&t=156.985825#t=02:36.99) ![[S03.使用现代OpenGLPT2M36.986S.jpeg|S03.使用现代OpenGL - 02:36|800]] 
- [02:39](https://www.bilibili.com/video/BV1Ni4y1o7Au?p=3&t=159.713787#t=02:39.71) ![[S03.使用现代OpenGLPT2M39.714S.jpeg|S03.使用现代OpenGL - 02:39|800]] 
- [02:43](https://www.bilibili.com/video/BV1Ni4y1o7Au?p=3&t=163.03548#t=02:43.04) ![[S03.使用现代OpenGLPT2M43.035S.jpeg|S03.使用现代OpenGL - 02:43|800]] 
- [02:46](https://www.bilibili.com/video/BV1Ni4y1o7Au?p=3&t=166.540662#t=02:46.54) ![[S03.使用现代OpenGLPT2M46.541S.jpeg|S03.使用现代OpenGL - 02:46|800]] 
- [03:43](https://www.bilibili.com/video/BV1Ni4y1o7Au?p=3&t=223.57969#t=03:43.58) ![[S03.使用现代OpenGLPT3M43.58S.jpeg|S03.使用现代OpenGL - 03:43|800]] 
- [03:51](https://www.bilibili.com/video/BV1Ni4y1o7Au?p=3&t=231.659236#t=03:51.66) ![[S03.使用现代OpenGLPT3M51.659S.jpeg|S03.使用现代OpenGL - 03:51|800]] 
- [03:52](https://www.bilibili.com/video/BV1Ni4y1o7Au?p=3&t=232.739021#t=03:52.74) ![[S03.使用现代OpenGLPT3M52.739S.jpeg|S03.使用现代OpenGL - 03:52|800]] 
- [03:55](https://www.bilibili.com/video/BV1Ni4y1o7Au?p=3&t=235.3509#t=03:55.35) ![[S03.使用现代OpenGLPT3M55.351S.jpeg|S03.使用现代OpenGL - 03:55|800]] 
- [04:09](https://www.bilibili.com/video/BV1Ni4y1o7Au?p=3&t=249.547919#t=04:09.55) ![[S03.使用现代OpenGLPT4M9.548S.jpeg|S03.使用现代OpenGL - 04:09|800]] 
- [04:13](https://www.bilibili.com/video/BV1Ni4y1o7Au?p=3&t=253.439885#t=04:13.44) ![[S03.使用现代OpenGLPT4M13.44S.jpeg|S03.使用现代OpenGL - 04:13|800]] 
- [04:16](https://www.bilibili.com/video/BV1Ni4y1o7Au?p=3&t=256.130852#t=04:16.13) ![[S03.使用现代OpenGLPT4M16.131S.jpeg|S03.使用现代OpenGL - 04:16|800]] 
- [04:17](https://www.bilibili.com/video/BV1Ni4y1o7Au?p=3&t=257.691913#t=04:17.69) ![[S03.使用现代OpenGLPT4M17.692S.jpeg|S03.使用现代OpenGL - 04:17|800]] 
- [06:57](https://www.bilibili.com/video/BV1Ni4y1o7Au?p=3&t=417.506966#t=06:57.51) ![[S03.使用现代OpenGLPT6M57.507S.jpeg|S03.使用现代OpenGL - 06:57|800]] 
- [07:02](https://www.bilibili.com/video/BV1Ni4y1o7Au?p=3&t=422.574107#t=07:02.57) ![[S03.使用现代OpenGLPT7M2.574S.jpeg|S03.使用现代OpenGL - 07:02|800]] 
- [07:07](https://www.bilibili.com/video/BV1Ni4y1o7Au?p=3&t=427.249849#t=07:07.25) ![[S03.使用现代OpenGLPT7M7.25S.jpeg|S03.使用现代OpenGL - 07:07|800]] GLAD也是同样的使用方法
# 2 笔记整理
## 2.1 笔记摘要
- GLEW链接使用
## 2.2 详细笔记
OpenGL的实现由各个显卡厂商提供，这些实现函数是显卡驱动的一部分，OpenGL提供了统一接口实现跨平台，在编译过程中需要找到各自平台上这些具体实现的函数，我们需要得到这些函数的声明，再链接到驱动里的这些函数。