# 1 问题描述
对于一些力学问题，由于其受力特点满足特殊条件，可以将其简化为二维平面问题。针对受力特点分类，二维平面问题可以分为*平面应力问题*和*平面应变问题*。使用有限元方法求解二维平面问题时，需要使用2D Solid单元。
## 1.1 平面应力
## 1.2 平面应变
# 2 等参单元
## 2.1 三角形
三角形单元通常使用*面积自然坐标*来构造形函数，三角形的面积公式可表示为：
$$
A_e = \frac{1}{2}
\begin{vmatrix}
	1 & x_1 & y_1\\
	1 & x_2 & y_2\\
	1 & x_3 & y_3
\end{vmatrix}
$$
则三角形内任意点$P$和顶点构成的三个三角形面积可表示为：
$$
A_1 = \frac{1}{2}
\begin{vmatrix}
	1 & x & y\\
	1 & x_2 & y_2\\
	1 & x_3 & y_3
\end{vmatrix}
$$
$$
A_2 = \frac{1}{2}
\begin{vmatrix}
	1 & x_1 & y_1\\
	1 & x & y\\
	1 & x_3 & y_3
\end{vmatrix}
$$
$$
A_3 = \frac{1}{2}
\begin{vmatrix}
	1 & x_1 & y_1\\
	1 & x_2 & y_2\\
	1 & x & y
\end{vmatrix}
$$
点$P$的坐标可表示为：
$$
\begin{pmatrix}
L_1,L_2,L_3
\end{pmatrix}=
\begin{pmatrix}
\frac{A_1}{A_e},\frac{A_2}{A_e},\frac{A_3}{A_e}
\end{pmatrix}
$$
一阶三角形单元的形函数为：
$$
\begin{align}
	N_1=L_1\\
	N_2=L_2\\
	N_3=L_3
\end{align}
$$
形函数满足归一化条件：
$$
N_1+N_2+N_3=L_1+L_2+L_3=1
$$
在*面积自然坐标*中，只有两个独立变量，因此可以令$L_2=\xi, L_3=\eta$,则有：
$$
\begin{align}
	&N_1=1-\xi-\eta\\
	&N_2=\xi\\
	&N_3=\eta
\end{align}
$$
*注意*
1. 选取任意两个面积自然坐标作为等参单元的坐标$(\xi,\eta)$都可以；
2. 选取不同的面积自然坐标，得到的雅可比矩阵$J$、偏导矩阵$B$是不同的，推导过程中，需要保持一致，不要临时更换坐标；
3. 选取不同的坐标，只是中间过程中的矩阵有差异，最终结果是相同的，因此推导过程中，需要保持坐标前后一致。

形函数对全局坐标偏导和对等参坐标偏导有如下关系：
$$
\begin{bmatrix}
	\frac{\partial N_1}{\partial\xi} & \frac{\partial N_2}{\partial\xi} & \frac{\partial N_3}{\partial\xi}\\
	\frac{\partial N_1}{\partial\eta} & \frac{\partial N_2}{\partial\eta} & \frac{\partial N_3}{\partial\eta}
\end{bmatrix}=
\begin{bmatrix}
	\frac{\partial x}{\partial\xi} & \frac{\partial y}{\partial\xi}\\
	\frac{\partial x}{\partial\eta} & \frac{\partial y}{\partial\eta}
\end{bmatrix}
\begin{bmatrix}
	\frac{\partial N_1}{\partial x} & \frac{\partial N_2}{\partial x} & \frac{\partial N_3}{\partial x}\\
	\frac{\partial N_1}{\partial y} & \frac{\partial N_2}{\partial y} & \frac{\partial N_3}{\partial y}
\end{bmatrix}
$$
雅可比矩阵定义为：
$$
J = 
\begin{bmatrix}
	\frac{\partial x}{\partial\xi} & \frac{\partial y}{\partial\xi}\\
	\frac{\partial x}{\partial\eta} & \frac{\partial y}{\partial\eta}
\end{bmatrix}
$$
由于$(x,y)$可表示为：
$$
\begin{bmatrix}
	x\\
	y
\end{bmatrix}=
\begin{bmatrix}
	N_1 & 0 & N_2 & 0 & N_3 & 0\\
	0 & N_1 & 0 & N_2 & 0 & N_3
\end{bmatrix}
\begin{bmatrix}
	x_1\\
	y_1\\
	x_2\\
	y_2\\
	x_3\\
	y_3
\end{bmatrix}
$$
雅可比矩阵可表示为：
$$
\begin{align}
	J &= 
	\begin{bmatrix}
		\frac{\partial N_1}{\partial\xi} & \frac{\partial N_2}{\partial\xi} & \frac{\partial N_3}{\partial\xi}\\
		\frac{\partial N_1}{\partial\eta} & \frac{\partial N_2}{\partial\eta} & \frac{\partial N_3}{\partial\eta}
	\end{bmatrix}
	\begin{bmatrix}
		x_1 & y_1\\
		x_2 & y_2\\
		x_3 & y_3
	\end{bmatrix}\\
	&=
	\begin{bmatrix}
		-1 & 1 & 0\\
		-1 & 0 & 1
	\end{bmatrix}
	\begin{bmatrix}
		x_1 & y_1\\
		x_2 & y_2\\
		x_3 & y_3
	\end{bmatrix}\\
	&=
	\begin{bmatrix}
		(x_2 - x_1) & (y_2 - y_1)\\
		(x_3 - x_1) & (y_3 - y_1)
	\end{bmatrix}
\end{align}
$$
由此可得形函数对全局坐标的偏导：
$$
\begin{bmatrix}
	\frac{\partial N_1}{\partial x} & \frac{\partial N_2}{\partial x} & \frac{\partial N_3}{\partial x}\\
	\frac{\partial N_1}{\partial y} & \frac{\partial N_2}{\partial y} & \frac{\partial N_3}{\partial y}
\end{bmatrix}=J^{-1}
\begin{bmatrix}
	\frac{\partial N_1}{\partial\xi} & \frac{\partial N_2}{\partial\xi} & \frac{\partial N_3}{\partial\xi}\\
	\frac{\partial N_1}{\partial\eta} & \frac{\partial N_2}{\partial\eta} & \frac{\partial N_3}{\partial\eta}
\end{bmatrix}
$$

## 2.2 四边形
四边形单元的等参单元如图所示。
则一阶四边形单元的形函数可以表示为：
$$
N_i=\frac{1}{4}(1+\xi_i\xi)(1+\eta_i\eta)
$$
其中$(\xi_i,\eta_i)$是等参单元的坐标。

类似于三角形单元，形函数对全局坐标偏导和对等参坐标偏导有如下关系：
$$
\begin{bmatrix}
	\frac{\partial N_1}{\partial\xi} & \frac{\partial N_2}{\partial\xi} & \frac{\partial N_3}{\partial\xi} & \frac{\partial N_4}{\partial\xi}\\
	\frac{\partial N_1}{\partial\eta} & \frac{\partial N_2}{\partial\eta} & \frac{\partial N_3}{\partial\eta} & \frac{\partial N_4}{\partial\eta}
\end{bmatrix}=
\begin{bmatrix}
	\frac{\partial x}{\partial\xi} & \frac{\partial y}{\partial\xi}\\
	\frac{\partial x}{\partial\eta} & \frac{\partial y}{\partial\eta}
\end{bmatrix}
\begin{bmatrix}
	\frac{\partial N_1}{\partial x} & \frac{\partial N_2}{\partial x} & \frac{\partial N_3}{\partial x} & \frac{\partial N_4}{\partial x}\\
	\frac{\partial N_1}{\partial y} & \frac{\partial N_2}{\partial y} & \frac{\partial N_3}{\partial y} & \frac{\partial N_4}{\partial y}
\end{bmatrix}
$$

雅可比矩阵：
$$
\begin{align}
	J &= 
	\begin{bmatrix}
		\frac{\partial x}{\partial\xi} & \frac{\partial y}{\partial\xi}\\
		\frac{\partial x}{\partial\eta} & \frac{\partial y}{\partial\eta}
	\end{bmatrix}\\&= 
	\begin{bmatrix}
		\frac{\partial N_1}{\partial\xi} & \frac{\partial N_2}{\partial\xi} & \frac{\partial N_3}{\partial\xi} & \frac{\partial N_4}{\partial\xi}\\
		\frac{\partial N_1}{\partial\eta} & \frac{\partial N_2}{\partial\eta} & \frac{\partial N_3}{\partial\eta} & \frac{\partial N_4}{\partial\eta}
	\end{bmatrix}
	\begin{bmatrix}
		x_1 & y_1\\
		x_2 & y_2\\
		x_3 & y_3\\
		x_4 & y_4
	\end{bmatrix}\\
	&=\frac{1}{4}
	\begin{bmatrix}
		-(1-\eta) & (1-\eta) & (1+\eta) & -(1+\eta) \\
		-(1-\xi) & -(1+\xi) & (1+\xi) & (1-\xi)
	\end{bmatrix}
	\begin{bmatrix}
		x_1 & y_1\\
		x_2 & y_2\\
		x_3 & y_3\\
		x_4 & y_4
	\end{bmatrix}
\end{align}
$$

# 3 刚度矩阵
# 4 剪切自锁(Shear locking)
# 5 沙漏(Hourglass mode)