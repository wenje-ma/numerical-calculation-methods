# 作业 4

> **幂法** (求按模最大的特征值与特征向量) <br>设 $n\times n$ 实矩阵 $A$ 的特征值满足 $\left|\lambda_1\right|>\left|\lambda_2\right|\ge\cdots\ge\left|\lambda_n\right|$, 相应特征向量 $u_1,u_2,\dots,u_n$ 线性无关. 取初始向量 $\alpha^{\left(0\right)}\ne0$, 由迭代 $\alpha^{\left(k+1\right)}=A\alpha^{\left(k\right)}$ (式(4.1)) 产生向量序列, 当 $k$ 充分大时 $\alpha^{\left(k+1\right)}$ 即可作为 $\lambda_1$ 相应特征向量的近似, 且 $$\lambda_1\approx\frac{\alpha_i^{\left(k+1\right)}}{\alpha_i^{\left(k\right)}}$$ (式(4.3)) . 为避免迭代中溢出或归零, 实际计算每次归一化: $$\alpha^{\left(k+1\right)}=Ay^{\left(k\right)},\quad y^{\left(k+1\right)}=\frac{\alpha^{\left(k+1\right)}}{\max_i\left|\alpha_i^{\left(k+1\right)}\right|},\quad\lambda_1\approx\max_i\left|\alpha_i^{\left(k+1\right)}\right|$$ (式(4.5)) . 收敛速度由收敛因子 $\left|\lambda_2/\lambda_1\right|$ 决定, 其值越小收敛越快.

> **幂法的艾特肯加速** (算法4.2) <br>若幂法产生的特征值近似序列 $\left\{a_k\right\}$ 线性收敛到 $a$, 即 $\lim_{k\to\infty}\frac{a_{k+1}-a}{a_k-a}=c\ne1$, 则当 $k$ 充分大时 $$\hat a_k=a_k-\frac{\left(a_{k+1}-a_k\right)^2}{a_{k+2}-2a_{k+1}+a_k}$$ 比 $\left\{a_k\right\}$ 更快地收敛到 $a$, 将其用于幂法所产生的序列即可加速收敛.

> **反幂法** (式(4.10), 算法4.3) <br>若 $\lambda,u$ 为 $A$ 的特征值与特征向量, 则 $A^{-1}u=\frac{1}{\lambda}u$, 即 $A^{-1}$ 的特征值为 $A$ 特征值的倒数而特征向量不变. 实际运算以解方程组 $$A\alpha^{\left(k+1\right)}=\alpha^{\left(k\right)}$$ (式(4.10)) 代替 $\alpha^{\left(k+1\right)}=A^{-1}\alpha^{\left(k\right)}$. 若已知 $A$ 的某特征值 $\lambda$ 的近似值 $\lambda^*$, 对 $A-\lambda^*I$ 用反幂法, 因 $\lambda-\lambda^*$ 为 $A-\lambda^*I$ 的按模最小特征值, 收敛很快, 迭代归一化后得分量 $\beta\approx\frac{1}{\lambda-\lambda^*}$, 故 $\lambda\approx\lambda^*+\frac{1}{\beta}$, 且所得 $\alpha^{\left(k\right)}$ 即为相应特征向量.

> **雅可比方法** (式(4.12), 式(4.13), 定理4.1) <br>任意 $n$ 阶实对称矩阵 $A$ 可经正交相似变换化为对角矩阵, 即存在正交矩阵 $Q$ 使 $$Q^{\mathrm T}AQ=\mathrm{diag}\left(\lambda_1,\lambda_2,\dots,\lambda_n\right),$$ 对角元即 $A$ 的全部特征值, $Q$ 各列即为相应特征向量. 取平面旋转变换矩阵 $V_{ij}\left(\varphi\right)$ (式(4.12), 在 $\left(i,j\right)$ 坐标平面旋转角 $\varphi$) , 选 $$\tan2\varphi=\frac{2a_{ij}}{a_{ii}-a_{jj}}$$ 可使变换后 $a_{ij}^{\left(1\right)}=0$ (式(4.13)) . 反复进行上述旋转, 由**定理 4.1**, 非对角元平方和趋于零, 矩阵趋于对角矩阵, 其对角元即 $A$ 的全部特征值.

### 习题一 (习题 4-1)

用幂法计算下列矩阵的按模最大的特征值及相应的特征向量, 取 $x^{\left(0\right)}=\left(1,0,0\right)^{\mathrm T}$: (1) $A=\begin{bmatrix}-4&14&0\\-5&13&0\\-1&0&2\end{bmatrix}$; (2) $A=\begin{bmatrix}4&-1&1\\-1&3&-2\\1&-2&3\end{bmatrix}$. (仅做第 (2) 小题) ### 解答 习题一

对 (2) 中矩阵 $A=\begin{bmatrix}4&-1&1\\-1&3&-2\\1&-2&3\end{bmatrix}$, 由**幂法** (式(4.5)) , 取 $y^{\left(0\right)}=x^{\left(0\right)}=\left(1,0,0\right)^{\mathrm T}$, 每次迭代后取绝对值最大分量归一化. 计算如下: $$
\alpha^{\left(1\right)}=Ay^{\left(0\right)}=\left(4,-1,1\right)^{\mathrm T},\quad\lambda_1\approx4,\quad y^{\left(1\right)}=\left(1,-0.25,0.25\right)^{\mathrm T},
$$

$$
\alpha^{\left(2\right)}=Ay^{\left(1\right)}=\left(4.5,-2.25,2.25\right)^{\mathrm T},\quad\lambda_2\approx4.5,\quad y^{\left(2\right)}=\left(1,-0.5,0.5\right)^{\mathrm T},
$$

$$
\alpha^{\left(3\right)}=Ay^{\left(2\right)}=\left(5,-3.5,3.5\right)^{\mathrm T},\quad\lambda_3\approx5,\quad y^{\left(3\right)}=\left(1,-0.7,0.7\right)^{\mathrm T},
$$

$$
\alpha^{\left(4\right)}=Ay^{\left(3\right)}=\left(5.4,-4.5,4.5\right)^{\mathrm T},\quad\lambda_4\approx5.4,\quad y^{\left(4\right)}=\left(1,-0.8333,0.8333\right)^{\mathrm T},
$$

$$
\alpha^{\left(5\right)}=Ay^{\left(4\right)}=\left(5.6667,-5.1667,5.1667\right)^{\mathrm T},\quad\lambda_5\approx5.6667,\quad y^{\left(5\right)}=\left(1,-0.9118,0.9118\right)^{\mathrm T},
$$

$$
\alpha^{\left(6\right)}=Ay^{\left(5\right)}=\left(5.8235,-5.5588,5.5588\right)^{\mathrm T},\quad\lambda_6\approx5.8235,\quad y^{\left(6\right)}=\left(1,-0.9545,0.9545\right)^{\mathrm T}.
$$

可见特征值近似 $\lambda_k$ 单调上升并趋于 $6$, 归一化向量 $y^{\left(k\right)}$ 的后两个分量趋于等值反号. 继续迭代得按模最大特征值 $\lambda_1\approx6$, 相应特征向量 $x\approx\left(1,-1,1\right)^{\mathrm T}$. 检验: $A\left(1,-1,1\right)^{\mathrm T}=\left(6,-6,6\right)^{\mathrm T}=6\left(1,-1,1\right)^{\mathrm T}$. $\blacksquare$

### 习题二 (习题 4-2)

用带艾特肯加速的幂法计算第 1 题中矩阵的最大模特征值及相应的特征向量, 要求结果有 4 位有效数字. (即第 1 题 (2) 中矩阵) ### 解答 习题二

由**幂法** (式(4.5)) 已得特征值近似序列

$$
\lambda_1\approx4,\ \lambda_2\approx4.5,\ \lambda_3\approx5,\ \lambda_4\approx5.4,\ \lambda_5\approx5.6667,\ \lambda_6\approx5.8235,\ \lambda_7\approx5.9091,\ \lambda_8\approx5.9538,\ \lambda_9\approx5.9767.
$$

对此序列用**幂法的艾特肯加速** (算法4.2) . 先取 $a=\lambda_6=5.8235$, $b=\lambda_7=5.9091$, $c=\lambda_8=5.9538$: $$
\hat a=a-\frac{\left(b-a\right)^2}{c-2b+a}=5.8235-\frac{\left(0.0856\right)^2}{5.9538-2\times5.9091+5.8235}\approx5.8235+0.1794\approx6.003.
$$

再取 $a=\lambda_7=5.9091$, $b=\lambda_8=5.9538$, $c=\lambda_9=5.9767$: $$
\hat a=5.9091-\frac{\left(0.0447\right)^2}{5.9767-2\times5.9538+5.9091}\approx5.9091+0.0916\approx6.001.
$$

两次加速均给出 $\lambda_1\approx6.000$, 达到 4 位有效数字. 相应特征向量与习题一相同, 即 $x\approx\left(1,-1,1\right)^{\mathrm T}$. $\blacksquare$

### 习题三 (习题 4-4)

用反幂法计算矩阵 $A=\begin{bmatrix}2&1&0\\1&3&1\\0&1&4\end{bmatrix}$ 相应于特征值 $1.2679$ 的特征向量.

### 解答 习题三

由**反幂法** (式(4.10), 算法4.3) , 取移位 $\lambda^*=1.2679$, 令

$$
B=A-\lambda^*I=\begin{bmatrix}0.7321&1&0\\1&1.7321&1\\0&1&2.7321\end{bmatrix}.
$$

任取初始向量 $y^{\left(0\right)}=\left(1,1,1\right)^{\mathrm T}$, 反复解方程组 $Bz=y^{\left(k\right)}$ 并按最大分量归一化. 第一次解 $Bz=\left(1,1,1\right)^{\mathrm T}$ 得 $z\approx\left(6776.4,-4960.0,1815.8\right)^{\mathrm T}$, 归一化得 $y^{\left(1\right)}\approx\left(1,-0.7320,0.2680\right)^{\mathrm T}$; 第二次解 $Bz=y^{\left(1\right)}$ 得 $z\approx\left(20327.5,-14880.7,5446.7\right)^{\mathrm T}$, 归一化得 $y^{\left(2\right)}\approx\left(1,-0.7321,0.2679\right)^{\mathrm T}$; 再迭代一次结果不变.

故相应于特征值 $1.2679$ 的特征向量为 $x\approx\left(1,-0.732,0.268\right)^{\mathrm T}$ (可相差一非零常数因子及符号) . 此时最大分量 $m\approx20327.5$, $\beta=\frac{1}{m}\approx4.9\times10^{-5}$, $\lambda\approx1.2679+\beta\approx1.26795$, 与给定特征值一致. $\blacksquare$

### 习题四 (习题 4-7)

设 $A$ 为 $n$ 阶实对称矩阵. 对任意非零向量 $x\in\mathbb R^n$, 称 $\frac{\left\langle Ax,x\right\rangle}{\left\langle x,x\right\rangle}=\frac{x^{\mathrm T}Ax}{x^{\mathrm T}x}$ 为 $A$ 的瑞利商, 求证: $$
\min_{x\ne0}\frac{\left\langle Ax,x\right\rangle}{\left\langle x,x\right\rangle}=\min\lambda\left(A\right),\quad\max_{x\ne0}\frac{\left\langle Ax,x\right\rangle}{\left\langle x,x\right\rangle}=\max\lambda\left(A\right).
$$

### 解答 习题四

由**雅可比方法**所依据的结论, 实对称矩阵 $A$ 可正交对角化, 即存在正交矩阵 $U=\left(u_1,u_2,\dots,u_n\right)$ 使 $U^{\mathrm T}AU=\Lambda=\mathrm{diag}\left(\lambda_1,\lambda_2,\dots,\lambda_n\right)$, 其中 $\lambda_1\le\lambda_2\le\cdots\le\lambda_n$ 为 $A$ 的全部特征值, $u_1,u_2,\dots,u_n$ 为相应规范正交的特征向量.

对任意非零向量 $x\in\mathbb R^n$, 在规范正交基 $\left\{u_j\right\}$ 下展开 $x=\sum_{j=1}^n c_ju_j$, 则

$$
\left\langle Ax,x\right\rangle=x^{\mathrm T}Ax=\sum_{j=1}^n\lambda_jc_j^2,\quad\left\langle x,x\right\rangle=x^{\mathrm T}x=\sum_{j=1}^nc_j^2.
$$

故瑞利商为

$$
R\left(x\right)=\frac{\left\langle Ax,x\right\rangle}{\left\langle x,x\right\rangle}=\frac{\sum_{j=1}^n\lambda_jc_j^2}{\sum_{j=1}^nc_j^2}.
$$

由 $\lambda_1\le\lambda_j\le\lambda_n\left(j=1,2,\dots,n\right)$, 得

$$
\lambda_1\sum_{j=1}^nc_j^2\le\sum_{j=1}^n\lambda_jc_j^2\le\lambda_n\sum_{j=1}^nc_j^2,
$$

两边同除以正数 $\sum_{j=1}^nc_j^2$, 即得 $\lambda_1\le R\left(x\right)\le\lambda_n$.

取 $x=u_1$ (即 $c_1=1$, 其余 $c_j=0$) , 则 $R\left(u_1\right)=\lambda_1=\min\lambda\left(A\right)$; 取 $x=u_n$, 则 $R\left(u_n\right)=\lambda_n=\max\lambda\left(A\right)$. 因此

$$
\min_{x\ne0}\frac{\left\langle Ax,x\right\rangle}{\left\langle x,x\right\rangle}=\min\lambda\left(A\right),\quad\max_{x\ne0}\frac{\left\langle Ax,x\right\rangle}{\left\langle x,x\right\rangle}=\max\lambda\left(A\right).
$$

$\blacksquare$

### 习题五 (习题 4-8)

用雅可比方法求下列矩阵的全部特征值: (1) $A=\begin{bmatrix}4&2&2\\2&5&1\\2&1&6\end{bmatrix}$; (2) $A=\begin{bmatrix}2&-1&0\\-1&-2&-1\\0&-1&2\end{bmatrix}$. (仅做第 (2) 小题) ### 解答 习题五

对 (2) 中实对称矩阵 $A=\begin{bmatrix}2&-1&0\\-1&-2&-1\\0&-1&2\end{bmatrix}$, 由**雅可比方法** (式(4.12), 式(4.13), 定理4.1) , 每次取绝对值最大的非对角元作旋转变换.

第一次取 $i=1,j=2$: $a_{12}=-1$, $a_{11}=2$, $a_{22}=-2$, 由 $\tan2\varphi=\frac{2a_{12}}{a_{11}-a_{22}}=\frac{-2}{4}=-0.5$, 得 $\varphi=-0.2318$, $\cos\varphi=0.9733$, $\sin\varphi=-0.2298$. 经 $V_{12}\left(\varphi\right)$ 变换后

$$
A^{\left(1\right)}\approx\begin{bmatrix}2.2361&0&0.2298\\0&-2.2361&-0.9733\\0.2298&-0.9733&2\end{bmatrix}.
$$

第二次取 $i=2,j=3$, 旋转后

$$
A^{\left(2\right)}\approx\begin{bmatrix}2.2361&-0.2245&0.0491\\-0.2245&2.2129&0\\0.0491&0&-2.4490\end{bmatrix}.
$$

第三次取 $i=1,j=2$, 旋转后

$$
A^{\left(3\right)}\approx\begin{bmatrix}2.4492&0&0.0356\\0&1.9997&0.0338\\0.0356&0.0338&-2.4490\end{bmatrix}.
$$

继续按**定理 4.1** 作旋转, 非对角元平方和趋于零, 矩阵趋于对角矩阵, 对角元收敛为 $2.449$, $2.000$, $-2.449$. 故 $A$ 的全部特征值为

$$
\lambda_1\approx2.449,\quad\lambda_2\approx2.000,\quad\lambda_3\approx-2.449
$$ (准确值为 $\sqrt6,\ 2,\ -\sqrt6$) . $\blacksquare$
