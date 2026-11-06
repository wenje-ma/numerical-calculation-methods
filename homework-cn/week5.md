# week5

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
> 设 $A$ 为对称正定矩阵, 则存在唯一的对角元皆为正数的下三角形矩阵 $L$, 使 $A=LL^\top$, 即平方根法. 由比较 $A=LL^\top$ 得 $l_{kk}=\left(a_{kk}-\sum_{j=1}^{k-1}l_{kj}^{2}\right)^{1/2}$, $l_{ik}=\frac{a_{ik}-\sum_{j=1}^{k-1}l_{ij}l_{kj}}{l_{kk}}$. 求解 $Ax=b$ 化为依次解 $Ly=b$ 与 $L^\topx=y$. 又 $A$ 可分解为 $A=LDL^\top$ (改进平方根法, $L$ 为单位下三角, $D$ 为对角阵), 运算中无须开方.

> **定理 2.5 (矩阵的算子范数)**
> 
> 由向量范数诱导的矩阵范数为 $\left\|A\right\|=\max_{\left\|x\right\|=1}\left\|Ax\right\|$, 且满足相容性 $\left\|Ax\right\|\le\left\|A\right\|\left\|x\right\|$. 常用的 1-范数 (列范数) 与 $\infty$-范数 (行范数) 为 $\left\|A\right\|_1=\max_{1\le{j}\le{n}}\sum_{i=1}^{n}\left|a_{ij}\right|$, $\left\|A\right\|_\infty=\max_{1\le{i}\le{n}}\sum_{j=1}^{n}\left|a_{ij}\right|$.

## 2-1

分别用高斯消去法, 列主元素法和全主元素法解下列方程组, 计算过程保留 3 位小数:

$$
\begin{cases}2x_1+6x_2-4x_3=4,\\x_1+4x_2-5x_3=3,\\6x_1-x_2+18x_3=2.\end{cases}
$$

(仅做第 (1) 小题)

### 解答 2-1

方程组的增广矩阵为

$$
\overline{A}=\begin{bmatrix}2&6&-4&4\\1&4&-5&3\\6&-1&18&2\end{bmatrix}.
$$

先按高斯消去法 消元. 第 1 步取 $a_{11}=2$ 为主元, 乘子 $l_{21}=1/2=0.500$, $l_{31}=6/2=3.000$, 第 2, 3 行分别减去第 1 行的相应倍数, 得

$$
\begin{bmatrix}2&6&-4&4\\0&1&-3&1\\0&-19&30&-10\end{bmatrix}.
$$

第 2 步取 $a_{22}=1$ 为主元, 乘子 $l_{32}=-19/1=-19.000$, 第 3 行加上第 2 行的 $19$ 倍, 得上三角形矩阵

$$
\begin{bmatrix}2&6&-4&4\\0&1&-3&1\\0&0&-27&9\end{bmatrix}.
$$

回代: $x_3=9/\left(-27\right)=-0.333$, $x_2=\left[1-\left(-3\right)\times\left(-0.333\right)\right]/1=0.000$, $x_1=\left[4-6\times0-\left(-4\right)\times\left(-0.333\right)\right]/2=1.333$.

列主元素法在第 1 列中选绝对值最大者 $\left|6\right|$ 作行交换, 全主元素法在全部剩余元素中选最大者作行, 列交换; 本题主元 $2,1,-27$ 均非小量, 选主元交换后消元所得上三角形方程组与上相同, 回代结果一致. 故

$$
x_1=1.333,\quad{x}_2=0.000,\quad{x}_3=-0.333.
$$

$\blacksquare$

## 2-2

用三角分解法求解题 1 中的方程组.

### 解答 2-2

由**定理 2.1 (直接三角分解的存在唯一性)** 及紧凑格式三角分解计算公式, 对题 1 的方程组作杜利特尔分解 $A=LU$, 再依次解 $Ly=b$, $Ux=y$.

方程组 $A=\begin{bmatrix}2&6&-4\\1&4&-5\\6&-1&18\end{bmatrix}$, $b=\left(4,3,2\right)^\top$. 紧凑格式算得

$$
L=\begin{bmatrix}1&0&0\\0.5&1&0\\3&-19&1\end{bmatrix},\quad{U}=\begin{bmatrix}2&6&-4\\0&1&-3\\0&0&-27\end{bmatrix}.
$$

前代: $y_1=4$, $y_2=3-0.5\times4=1$, $y_3=2-3\times4-\left(-19\right)\times1=9$. 回代: $x_3=9/\left(-27\right)=-1/3$, $x_2=\left[1-\left(-3\right)\times\left(-1/3\right)\right]/1=0$, $x_1=\left[4-\left(-4\right)\times\left(-1/3\right)\right]/2=4/3$. 即 $x=\left(4/3,0,-1/3\right)^\top$. $\blacksquare$
