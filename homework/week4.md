# week4

> **定义 2.1 (三对角方程组)**
> 
> 系数矩阵 $A$ 的非零元素只分布在主对角线及相邻两条次对角线上: $A=\begin{bmatrix}b_1&c_1&&\\a_2&b_2&c_2&\\&\ddots&\ddots&\ddots\\&&a_n&b_n\end{bmatrix}$.

> **定理 2.1 (直接三角分解的存在唯一性)**
> 
> 设 $A$ 为 $n$ 阶方阵, 若 $A$ 的各阶顺序主子式 $\det{A}_i$ ($i=1,2,\dots,n-1$) 均不为零, 则 $A$ 有唯一的杜利特尔分解 $A=LU$, 其中 $L$ 为单位下三角形矩阵, $U$ 为上三角形矩阵. 此时解 $Ax=b$ 等价于依次求解 $Ly=b$, $Ux=y$.

> **定理 2.3 (追赶法)**
> 
> 当三对角矩阵 $A$ 满足按行对角占优条件时, 可分解为 $A=LU$, 其中 $u_1=b_1$, $l_i=a_i/u_{i-1}$, $u_i=b_i-c_{i-1}l_i$; 追 (前代) 为 $y_1=d_1$, $y_k=d_k-l_ky_{k-1}$, 赶 (回代) 为 $x_n=\frac{y_n}{u_n}$, $x_k=\frac{y_k-c_kx_{k+1}}{u_k}$ ($k=n-1,\dots,1$).

> **定义 2.4 (矩阵的条件数)**
> 
> 对非奇异矩阵 $A$, 称 $\mathrm{cond}\left(A\right)=\left\|A\right\|\,\left\|A^{-1}\right\|$ 为 $A$ 的条件数. 条件数越大, 方程组 $Ax=b$ 关于右端项或系数矩阵扰动的病态越严重, 且恒有 $\mathrm{cond}\left(A\right)\ge1$.

> **定理 2.4 (对称正定矩阵的乔列斯基分解)**
> 
> 设 $A$ 为对称正定矩阵, 则存在唯一的对角元皆为正数的下三角形矩阵 $L$, 使 $A=LL^{\top}$, 即平方根法. 由比较 $A=LL^{\top}$ 得 $l_{kk}=\left(a_{kk}-\sum_{j=1}^{k-1}l_{kj}^{2}\right)^{1/2}$, $l_{ik}=\frac{a_{ik}-\sum_{j=1}^{k-1}l_{ij}l_{kj}}{l_{kk}}$. 求解 $Ax=b$ 化为依次解 $Ly=b$ 与 $L^{\top}x=y$. 又 $A$ 可分解为 $A=LDL^{\top}$ (改进平方根法, $L$ 为单位下三角, $D$ 为对角阵), 运算中无须开方.

> **定理 2.5 (矩阵的算子范数)**
> 
> 由向量范数诱导的矩阵范数为 $\left\|A\right\|=\max_{\left\|x\right\|=1}\left\|Ax\right\|$, 且满足相容性 $\left\|Ax\right\|\le\left\|A\right\|\left\|x\right\|$. 常用的 1-范数 (列范数) 与 $\infty$-范数 (行范数) 为 $\left\|A\right\|_1=\max_{1\le{j}\le{n}}\sum_{i=1}^{n}\left|a_{ij}\right|$, $\left\|A\right\|_\infty=\max_{1\le{i}\le{n}}\sum_{j=1}^{n}\left|a_{ij}\right|$.

> **定义 3.3 (谱半径)**
> 
> $\rho\left(A\right)=\max\left|\lambda_i\right|$.

> **定义 3.4 (对角占优矩阵)**
> 
> $\left|a_{ii}\right|\ge\sum_{j\ne{i}}\left|a_{ij}\right|$.

> **定理 3.6 (迭代法收敛的充要条件)**
> 
> $\rho\left(M\right)<1$.

## 习题 3-5

讨论雅可比迭代法收敛时实数 $a$ 的范围.

### 解答 习题 3-5

$\rho\left(B\right)=\left|2/a\right|$, 收敛当 $\left|a\right|>2$.

$\blacksquare$

## 习题 3-7

写出三种迭代法公式并判断收敛性.

### 解答 习题 3-7

$A$ 对称正定, $0<\omega=1.35<2$, 高斯-赛德尔与 SOR 收敛, 雅可比发散.

$\blacksquare$

## 习题 3-8

写出收敛的迭代式.

### 解答 习题 3-8

交换行次序得严格对角占优矩阵.

$\blacksquare$

## 习题 4-1(2)

用幂法求 $A=\begin{bmatrix}4&-1&1\\-1&3&-2\\1&-2&3\end{bmatrix}$ 的最大模特征值.

### 解答 习题 4-1(2)

$\lambda_1\approx6$, 特征向量 $\left(1,-1,1\right)^{\top}$.

$\blacksquare$
