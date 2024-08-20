有限元方法中包含各种类型的单元，按照理论可以分为实体单元和结构单元，实体单元直接离散平衡方程，而结构单元基于平衡方程，针对各自结构的受力特点，先进行简化，再离散简化后的平衡方程，二者虽然形式上有区别，但本质上还是对平衡方程进行离散求解。单元理论主要包括单元内力计算以及沙漏控制等对单元的特殊处理，虽然各种类型的单元各有差异，但是求解过程大体相似，本章对单元求解过程进行总结，为了方便，仅对3D情况进行了推导，其他情况可按照相同步骤推导得到。
# 1 单元内力
$$
f^{int}=\int_{\Omega} B^T\cdot\sigma\mathrm{d}\Omega
$$

# 2 离散
$$
\varepsilon=Lu^h=LNu
$$
$$
\varepsilon=
\begin{bmatrix}
\varepsilon_{xx} \\
\varepsilon_{yy} \\
\varepsilon_{zz} \\
\gamma_{xy} \\
\gamma_{yz} \\
\gamma_{xz} 
\end{bmatrix}
$$
$$
L=
\begin{bmatrix}
\frac{\partial}{\partial x} & 0 & 0 \\
0 & \frac{\partial}{\partial y} & 0 \\
0 & 0 & \frac{\partial}{\partial z} \\
\frac{\partial}{\partial y} & \frac{\partial}{\partial x} & 0 \\
0 & \frac{\partial}{\partial z} & \frac{\partial}{\partial y} \\
\frac{\partial}{\partial z} & 0 & \frac{\partial}{\partial x}
\end{bmatrix}
$$
$$
\textbf{N}=
\begin{bmatrix}
\textbf{N}_{1} & \textbf{N}_{2} & \textbf{N}_{3} & \cdots & \textbf{N}_{m} 
\end{bmatrix}_{3\times3m}
$$
$$
\textbf{N}_{i}=
\begin{bmatrix}
N_{i} & & \\
 & N_{i} & \\
 & & N_{i}
\end{bmatrix}_{3\times3}
$$
$$
u=
\begin{bmatrix}
u_{1} \\
v_{1} \\
w_{1} \\
\vdots \\
u_{m} \\
v_{m} \\
w_{m}
\end{bmatrix}_{3m\times1}
$$
$$
B=LN
$$
$$
\begin{bmatrix}
\frac{\partial N_{1}}{\partial\xi} & \frac{\partial N_{2}}{\partial\xi} & \cdots & \frac{\partial N_{m}}{\partial\xi} \\
\frac{\partial N_{1}}{\partial\eta} & \frac{\partial N_{2}}{\partial\eta} & \cdots & \frac{\partial N_{m}}{\partial\eta} \\
\frac{\partial N_{1}}{\partial\zeta} & \frac{\partial N_{2}}{\partial\zeta} & \cdots & \frac{\partial N_{m}}{\partial\zeta}
\end{bmatrix}_{3\times m}=
\begin{bmatrix}
\frac{\partial x}{\partial\xi} & \frac{\partial y}{\partial\xi} & \frac{\partial z}{\partial\xi} \\
\frac{\partial x}{\partial\eta} & \frac{\partial y}{\partial\eta} & \frac{\partial z}{\partial\eta} \\
\frac{\partial x}{\partial\zeta} & \frac{\partial y}{\partial\zeta} & \frac{\partial z}{\partial\zeta}
\end{bmatrix}
\begin{bmatrix}
\frac{\partial N_{1}}{\partial x} & \frac{\partial N_{2}}{\partial x} & \cdots & \frac{\partial N_{m}}{\partial x} \\
\frac{\partial N_{1}}{\partial y} & \frac{\partial N_{2}}{\partial y} & \cdots & \frac{\partial N_{m}}{\partial y} \\
\frac{\partial N_{1}}{\partial z} & \frac{\partial N_{2}}{\partial z} & \cdots & \frac{\partial N_{m}}{\partial z}
\end{bmatrix}_{3\times m}
$$
定义$J$为：
$$
J=
\begin{bmatrix}
\frac{\partial x}{\partial\xi} & \frac{\partial x}{\partial\eta} & \frac{\partial x}{\partial\zeta} \\
\frac{\partial y}{\partial\xi} & \frac{\partial y}{\partial\eta} & \frac{\partial y}{\partial\zeta} \\
\frac{\partial z}{\partial\xi} & \frac{\partial z}{\partial\eta} & \frac{\partial z}{\partial\zeta}
\end{bmatrix}
$$
根据关系式：
$$
\begin{bmatrix}
\mathrm{d}x \\
\mathrm{d}y \\
\mathrm{d}z
\end{bmatrix}=
\begin{bmatrix}
\frac{\partial x}{\partial\xi} & \frac{\partial x}{\partial\eta} & \frac{\partial x}{\partial\zeta} \\
\frac{\partial y}{\partial\xi} & \frac{\partial y}{\partial\eta} & \frac{\partial y}{\partial\zeta} \\
\frac{\partial z}{\partial\xi} & \frac{\partial z}{\partial\eta} & \frac{\partial z}{\partial\zeta}
\end{bmatrix}
\begin{bmatrix}
\mathrm{d}\xi \\
\mathrm{d}\eta \\
\mathrm{d}\zeta
\end{bmatrix}
$$
由此可知，$J$矩阵将等参坐标系下微元$[\mathrm{d}\xi\quad\mathrm{d}\eta\quad\mathrm{d}\zeta]^T$映射到到当前构型坐标系下微元$[\mathrm{d}x\quad\mathrm{d}y\quad\mathrm{d}z]^T$，上式可以写为：
$$
\begin{bmatrix}
\frac{\partial N_{1}}{\partial\xi} & \frac{\partial N_{2}}{\partial\xi} & \cdots & \frac{\partial N_{m}}{\partial\xi} \\
\frac{\partial N_{1}}{\partial\eta} & \frac{\partial N_{2}}{\partial\eta} & \cdots & \frac{\partial N_{m}}{\partial\eta} \\
\frac{\partial N_{1}}{\partial\zeta} & \frac{\partial N_{2}}{\partial\zeta} & \cdots & \frac{\partial N_{m}}{\partial\zeta}
\end{bmatrix}_{3\times m}=J^{T}
\begin{bmatrix}
\frac{\partial N_{1}}{\partial x} & \frac{\partial N_{2}}{\partial x} & \cdots & \frac{\partial N_{m}}{\partial x} \\
\frac{\partial N_{1}}{\partial y} & \frac{\partial N_{2}}{\partial y} & \cdots & \frac{\partial N_{m}}{\partial y} \\
\frac{\partial N_{1}}{\partial z} & \frac{\partial N_{2}}{\partial z} & \cdots & \frac{\partial N_{m}}{\partial z}
\end{bmatrix}_{3\times m}
$$
利用等参坐标关系式：
$$
J^T=
\begin{bmatrix}
\frac{\partial x}{\partial\xi} & \frac{\partial y}{\partial\xi} & \frac{\partial z}{\partial\xi} \\
\frac{\partial x}{\partial\eta} & \frac{\partial y}{\partial\eta} & \frac{\partial z}{\partial\eta} \\
\frac{\partial x}{\partial\zeta} & \frac{\partial y}{\partial\zeta} & \frac{\partial z}{\partial\zeta}
\end{bmatrix}=
\begin{bmatrix}
\frac{\partial N_{1}}{\partial\xi} & \frac{\partial N_{2}}{\partial\xi} & \cdots & \frac{\partial N_{m}}{\partial\xi} \\
\frac{\partial N_{1}}{\partial\eta} & \frac{\partial N_{2}}{\partial\eta} & \cdots & \frac{\partial N_{m}}{\partial\eta} \\
\frac{\partial N_{1}}{\partial\zeta} & \frac{\partial N_{2}}{\partial\zeta} & \cdots & \frac{\partial N_{m}}{\partial\zeta}
\end{bmatrix}_{3\times m}
\begin{bmatrix}
x_{1} & y_{1} & z_{1} \\
x_{2} & y_{2} & z_{2} \\
\vdots & \vdots & \vdots \\
x_{m} & y_{m} & z_{m}
\end{bmatrix}_{m\times3}
$$
由此可得：
$$
\begin{bmatrix}
\frac{\partial N_{1}}{\partial x} & \frac{\partial N_{2}}{\partial x} & \cdots & \frac{\partial N_{m}}{\partial x} \\
\frac{\partial N_{1}}{\partial y} & \frac{\partial N_{2}}{\partial y} & \cdots & \frac{\partial N_{m}}{\partial y} \\
\frac{\partial N_{1}}{\partial z} & \frac{\partial N_{2}}{\partial z} & \cdots & \frac{\partial N_{m}}{\partial z}
\end{bmatrix}_{3\times m}=J^{-T}
\begin{bmatrix}
\frac{\partial N_{1}}{\partial\xi} & \frac{\partial N_{2}}{\partial\xi} & \cdots & \frac{\partial N_{m}}{\partial\xi} \\
\frac{\partial N_{1}}{\partial\eta} & \frac{\partial N_{2}}{\partial\eta} & \cdots & \frac{\partial N_{m}}{\partial\eta} \\
\frac{\partial N_{1}}{\partial\zeta} & \frac{\partial N_{2}}{\partial\zeta} & \cdots & \frac{\partial N_{m}}{\partial\zeta}
\end{bmatrix}_{3\times m}
$$
需要注意的是，等式右边第二项，形函数对参数坐标的偏导是不随时间变化的，大多数情况下是常数矩阵。
$$
F=
\begin{bmatrix}
\frac{\partial x}{\partial X} & \frac{\partial x}{\partial Y} & \frac{\partial x}{\partial Z} \\
\frac{\partial y}{\partial X} & \frac{\partial y}{\partial Y} & \frac{\partial y}{\partial Z} \\
\frac{\partial z}{\partial X} & \frac{\partial z}{\partial Y} & \frac{\partial z}{\partial Z}
\end{bmatrix}
$$
由此可得：
$$
\begin{align*}
F^T=&
\begin{bmatrix}
\frac{\partial x}{\partial X} & \frac{\partial y}{\partial X} & \frac{\partial z}{\partial X} \\
\frac{\partial x}{\partial Y} & \frac{\partial y}{\partial Y} & \frac{\partial z}{\partial Y} \\
\frac{\partial x}{\partial Z} & \frac{\partial y}{\partial Z} & \frac{\partial z}{\partial Z}
\end{bmatrix}\\=&
\begin{bmatrix}
\frac{\partial N_{1}}{\partial X} & \frac{\partial N_{2}}{\partial X} & \cdots & \frac{\partial N_{m}}{\partial X} \\
\frac{\partial N_{1}}{\partial Y} & \frac{\partial N_{2}}{\partial Y} & \cdots & \frac{\partial N_{m}}{\partial Y} \\
\frac{\partial N_{1}}{\partial Z} & \frac{\partial N_{2}}{\partial Z} & \cdots & \frac{\partial N_{m}}{\partial Z}
\end{bmatrix}_{3\times m}
\begin{bmatrix}
x_{1} & y_{1} & z_{1} \\
x_{2} & y_{2} & z_{2} \\
\vdots & \vdots & \vdots \\
x_{m} & y_{m} & z_{m}
\end{bmatrix}_{m\times3}\\=&J^{-T}_{0}
\begin{bmatrix}
\frac{\partial N_{1}}{\partial\xi} & \frac{\partial N_{2}}{\partial\xi} & \cdots & \frac{\partial N_{m}}{\partial\xi} \\
\frac{\partial N_{1}}{\partial\eta} & \frac{\partial N_{2}}{\partial\eta} & \cdots & \frac{\partial N_{m}}{\partial\eta} \\
\frac{\partial N_{1}}{\partial\zeta} & \frac{\partial N_{2}}{\partial\zeta} & \cdots & \frac{\partial N_{m}}{\partial\zeta}
\end{bmatrix}_{3\times m}
\begin{bmatrix}
x_{1} & y_{1} & z_{1} \\
x_{2} & y_{2} & z_{2} \\
\vdots & \vdots & \vdots \\
x_{m} & y_{m} & z_{m}
\end{bmatrix}_{m\times3}\\=&
J_{0}^{-T}\cdot J^{T}
\end{align*}
$$
所以有：
$$
F=J\cdot J_{0}^{-1}
$$
根据$F$的定义有：
$$
\begin{align*}
\mathrm{d}\textbf{x}&=F\cdot\mathrm{d}\textbf{X}\\
&=J\cdot J_{0}^{-1}\cdot\mathrm{d}\textbf{X}
\end{align*}
$$
所以这个关系式表明，$F$将参考构型下微元$\mathrm{d}\textbf{X}$映射到当前构型下微元$\mathrm{d}\textbf{x}$，这种映射关系可以拆分为两部分，第一步，先把参考构型下微元$\mathrm{d}\textbf{X}$映射到等参坐标系中$(J_{0}^{-1}\cdot\mathrm{d}\textbf{X})$；第二步，再从等参坐标系下映射到当前构型下$J\cdot(J_{0}^{-1}\cdot\mathrm{d}\textbf{X})$。由于等参坐标系不随时间而变化，因此保证了这种映射拆分的正确性。
# 3 等参单元
