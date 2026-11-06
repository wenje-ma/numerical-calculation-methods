# week7

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

## 2-6

分别用平方根法和改进平方根法求解方程组:

$$
\begin{bmatrix}1&2&1&-3\\2&5&0&-5\\1&0&14&1\\-3&-5&1&15\end{bmatrix}\begin{bmatrix}x_1\\x_2\\x_3\\x_4\end{bmatrix}=\begin{bmatrix}1\\2\\16\\8\end{bmatrix}.
$$

### 解答 2-6

系数矩阵对称, 且各阶顺序主子式均为正, 由**定理 2.4 (对称正定矩阵的乔列斯基分解)** 可作 $A=LL^{\top}$.

平方根法: 按列计算 $L$ 的元素. $l_{11}=\sqrt{1}=1$, $l_{21}=2/1=2$, $l_{31}=1/1=1$, $l_{41}=-3/1=-3$; $l_{22}=\sqrt{5-2^{2}}=1$, $l_{32}=\left(0-1\times2\right)/1=-2$, $l_{42}=\left(-5-\left(-3\right)\times2\right)/1=1$; $l_{33}=\sqrt{14-1^{2}-\left(-2\right)^{2}}=3$, $l_{43}=\left[1-\left(-3\right)\times1-1\times\left(-2\right)\right]/3=2$; $l_{44}=\sqrt{15-\left(-3\right)^{2}-1^{2}-2^{2}}=1$. 故

$$
L=\begin{bmatrix}1&0&0&0\\2&1&0&0\\1&-2&3&0\\-3&1&2&1\end{bmatrix}.
$$

解 $Ly=b$: $y_1=1$, $y_2=\left(2-2\times1\right)/1=0$, $y_3=\left[16-1\times1-\left(-2\right)\times0\right]/3=5$, $y_4=\left[8-\left(-3\right)\times1-1\times0-2\times5\right]/1=1$. 再解 $L^{\top}x=y$: $x_4=1$, $x_3=\left(5-2\times1\right)/3=1$, $x_2=0-\left(-2\right)\times1-1\times1=1$, $x_1=1-2\times1-1\times1-\left(-3\right)\times1=1$.

改进平方根法: 作 $A=\widetilde{L}D\widetilde{L}^{\top}$, 其中 $D=\mathrm{diag}\left(1,1,9,1\right)$, 单位下三角阵 $\widetilde{L}$ 的非对角元为上述 $L$ 各列除以该列对角元 $\sqrt{d_k}$, 即 $l_{21}=2$, $l_{31}=1$, $l_{41}=-3$, $l_{32}=-2$, $l_{42}=1$, $l_{43}=2/3$. 前代 $Ly=b$ 得 $y=\left(1,0,15,1\right)^{\top}$, 再由 $x_k=y_k/d_k-\sum_{j=k+1}^{n}l_{jk}x_j$ 回代: $x_4=1$, $x_3=15/9-\left(2/3\right)\times1=1$, $x_2=0-\left(-2\right)\times1-1\times1=1$, $x_1=1-2\times1-1\times1-\left(-3\right)\times1=1$. 两种方法结果一致.

故 $x=\left(1,1,1,1\right)^{\top}$. $\blacksquare$
