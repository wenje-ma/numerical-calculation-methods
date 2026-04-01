# week5

> **定理 4.1 (古典 Jacobi 法的收敛性)**
> 
> 设 $A$ 为 $n$ 阶实对称矩阵, 对 $A$ 用古典 Jacobi 法得到矩阵序列 $\left\{A^{\left(k\right)}\right\}$, 则 $\left\{A^{\left(k\right)}\right\}$ 收敛于对角矩阵, 其对角元即为 $A$ 的全部特征值. (教材 $\S4.3$, p112)

> **定理 5.1 (插值多项式的存在唯一性)**
> 
> 设 $x_0,x_1,\ldots,x_n$ 是区间 $\left[a,b\right]$ 上的互异节点, 则满足插值条件 $P_n\left(x_i\right)=y_i$ ($i=0,1,\ldots,n$) 的次数不超过 $n$ 的多项式 $P_n\left(x\right)$ 存在且唯一. (教材 $\S5.2$, p132)

## 习题 4-2 (带 Aitken 加速的幂法)

用带 Aitken 加速的幂法计算第 $1$ 题中矩阵的最大模特征值及相应的特征向量, 要求结果有 $4$ 位有效数字. 两个矩阵为

$$
A_1=\begin{pmatrix}-4&14&0\\-5&13&0\\-1&0&2\end{pmatrix},\qquad A_2=\begin{pmatrix}4&-1&1\\-1&3&-2\\1&-2&3\end{pmatrix},
$$

均取 $x^{\left(0\right)}=\left(1,0,0\right)^{\mathrm{T}}$.

### 解答 4-2

幂法每步给出一个近似值 $\mu_k$, 其误差按 $\left(\lambda_2/\lambda_1\right)^{k}$ 等比衰减, 故 $\mu_k$ 是等比数列加极限值的形式. Aitken 加速就是把连续三个 $\mu$ 当作等比数列的三个项, 直接外推出极限

$$
\tilde{\mu}_k=\mu_{k+1}-\frac{\left(\mu_{k+1}-\mu_k\right)^{2}}{\left(\mu_{k+1}-\mu_k\right)-\left(\mu_k-\mu_{k-1}\right)}.
$$

(1) $A_1$ 的幂法迭代. $A_1$ 是分块三角形矩阵, 特征值为 $\left(2,\ 3,\ 6\right)$ (前 $2\times2$ 块的特征多项式 $\lambda^{2}-9\lambda+18=\left(\lambda-3\right)\left(\lambda-6\right)$, 第三对角元为 $2$), 主特征值为 $6$.

迭代 $\mu_k$ 与归一化向量 $\left(x^{\left(k\right)}\right)^{\mathrm{T}}=\left(1,\cdot,\cdot\right)$ 如下 (取 $\mu_k$ 为 $y^{\left(k\right)}$ 中按模最大的分量):

| $k$ | $\mu_k$ | $x^{\left(k\right)}$ |
|---|---|---|
| $1$ | $-5.000$ | $\left(0.8,\ 1,\ 0.2\right)^{\mathrm{T}}$ |
| $2$ | $10.800$ | $\left(1,\ 0.8333,\ -0.0370\right)^{\mathrm{T}}$ |
| $3$ | $7.667$ | $\left(1,\ 0.7609,\ -0.1401\right)^{\mathrm{T}}$ |
| $4$ | $6.652$ | $\left(1,\ 0.7353,\ -0.1924\right)^{\mathrm{T}}$ |
| $5$ | $6.294$ | $\left(1,\ 0.7243,\ -0.2200\right)^{\mathrm{T}}$ |
| $6$ | $6.140$ | $\left(1,\ 0.7192,\ -0.2345\right)^{\mathrm{T}}$ |
| $7$ | $6.068$ | $\left(1,\ 0.7167,\ -0.2421\right)^{\mathrm{T}}$ |

按 Aitken 公式逐组计算:

$$
\tilde{\mu}_3=7.667-\frac{\left(7.667-10.800\right)^{2}}{\left(7.667-10.800\right)-\left(10.800+5.000\right)}=8.185,
$$

$$
\tilde{\mu}_4=6.652-\frac{\left(6.652-7.667\right)^{2}}{\left(6.652-7.667\right)-\left(7.667-10.800\right)}=6.166,\qquad \tilde{\mu}_5=6.099,\quad \tilde{\mu}_6=6.024,\quad \tilde{\mu}_7=6.006.
$$

外推值与 $6$ 的偏差为 $2.185\to0.166\to0.099\to0.024\to0.006$, 比原序列的偏差 $1.667\to0.652\to0.294\to0.140\to0.068$ 衰减快得多. 故主特征值 $\lambda_1=6.000$ (4 位有效数字).

特征向量由表中 $x^{\left(k\right)}$ 的第 $2$ 与第 $3$ 分量趋于 $0.7143$ 与 $-0.2500$ 读出, 即 $\left(1,\ 5/7,\ -1/4\right)^{\mathrm{T}}$. 校验: 

$$
A_1\left(1,\frac{5}{7},-\frac{1}{4}\right)^{\mathrm{T}}=\left(-4+\frac{70}{7},\ -5+\frac{65}{7},\ -1-\frac{1}{2}\right)^{\mathrm{T}}=\left(6,\ \frac{30}{7},\ -1.5\right)^{\mathrm{T}}=6\left(1,\frac{5}{7},-\frac{1}{4}\right)^{\mathrm{T}},
$$

故 $\lambda_1=6$, 相应特征向量为 $\left(1,\ 0.7143,\ -0.2500\right)^{\mathrm{T}}$.

$\blacksquare$

(2) $A_2$ 的幂法迭代. $A_2$ 的特征值为 $\left(1,\ 3,\ 6\right)$, 主特征值 $6$.

| $k$ | $\mu_k$ | $x^{\left(k\right)}$ |
|---|---|---|
| $1$ | $4.000$ | $\left(1,\ -0.2500,\ 0.2500\right)^{\mathrm{T}}$ |
| $2$ | $4.500$ | $\left(1,\ -0.5000,\ 0.5000\right)^{\mathrm{T}}$ |
| $3$ | $5.000$ | $\left(1,\ -0.7000,\ 0.7000\right)^{\mathrm{T}}$ |
| $4$ | $5.400$ | $\left(1,\ -0.8333,\ 0.8333\right)^{\mathrm{T}}$ |
| $5$ | $5.667$ | $\left(1,\ -0.9118,\ 0.9118\right)^{\mathrm{T}}$ |
| $6$ | $5.824$ | $\left(1,\ -0.9545,\ 0.9545\right)^{\mathrm{T}}$ |
| $7$ | $5.909$ | $\left(1,\ -0.9769,\ 0.9769\right)^{\mathrm{T}}$ |

注意 $k=1,2,3$ 三步的差 $\mu_2-\mu_1=0.5=\mu_3-\mu_2$, 分母为零, Aitken 公式在此处失效 (三个点恰成等差数列, 不能确定公比). 从 $k=4$ 起可用:

$$
\tilde{\mu}_4=5.400-\frac{\left(5.400-5.000\right)^{2}}{\left(5.400-5.000\right)-\left(5.000-4.500\right)}=7.000,
$$

$$
\tilde{\mu}_5=6.200,\quad \tilde{\mu}_6=6.048,\quad \tilde{\mu}_7=6.012.
$$

偏差 $1.000\to0.200\to0.048\to0.012$ 迅速趋于零, 故 $\lambda_1=6.000$.

特征向量趋向 $\left(1,-1,1\right)^{\mathrm{T}}$, 与 $A_2\left(1,-1,1\right)^{\mathrm{T}}=6\left(1,-1,1\right)^{\mathrm{T}}$ 一致.

$\blacksquare$

(3) 两题的加速效果对比. 对 $A_2$, 原序列 $\mu_7=5.909$ 与 $6$ 相差 $0.091$; 加速后 $\tilde{\mu}_7=6.012$ 已达 $4$ 位有效数字. 加速的代价是每三步要多做两次乘除, 在 $\left|\lambda_2/\lambda_1\right|$ 接近 $1$ 时收益最大.

## 习题 4-4 (反幂法求指定特征值对应的特征向量)

用反幂法计算矩阵

$$
A=\begin{pmatrix}2&1&0\\1&3&1\\0&1&4\end{pmatrix}
$$

相应于特征值 $1.2679$ 的特征向量.

### 解答 4-4

$A$ 的特征值为 $3-\sqrt{3}=1.267949$ 与 $3$ 与 $3+\sqrt{3}=4.732051$, $1.2679$ 是其中最小的特征值. 反幂法取移位 $\mu=1.2679$, 迭代格式为解线性方程组

$$
\left(A-\mu I\right)y^{\left(k\right)}=x^{\left(k-1\right)},\qquad x^{\left(k\right)}=\frac{y^{\left(k\right)}}{\max_i\left|y_i^{\left(k\right)}\right|},
$$

其收敛因子为 $\left|\lambda_{\text{近}}-\mu\right|/\min_{j\ne\text{近}}\left|\lambda_j-\mu\right|$, 因 $\mu$ 与 $3-\sqrt{3}$ 只差 $5\times10^{-5}$, 第一步就几乎到位.

取 $x^{\left(0\right)}=\left(1,1,1\right)^{\mathrm{T}}$, 移位矩阵

$$
A-\mu I=\begin{pmatrix}0.7321&1&0\\1&1.7321&1\\0&1&2.7321\end{pmatrix}.
$$

解 $\left(A-\mu I\right)y^{\left(1\right)}=\left(1,1,1\right)^{\mathrm{T}}$: 按顺序消元, 第 $1$ 步乘子 $m_{21}=1/0.7321=1.3660$ (第 $3$ 行首元为零, $m_{31}=0$), 第 $2$ 步乘子 $m_{32}=1/0.3661=2.7315$, 第 $3$ 个主元只剩 $u_{33}=2.7321-2.7315=0.0011$, 回代得

$$
y^{\left(1\right)}=\left(6776.3988,\ -4960.0016,\ 1815.8199\right)^{\mathrm{T}},
$$

归一化(除以第一分量 $6776.3988$)得

$$
x^{\left(1\right)}=\left(1,\ -0.731952,\ 0.267962\right)^{\mathrm{T}}.
$$

再迭代一次即稳定:

$$
x^{\left(2\right)}=\left(1,\ -0.732051,\ 0.267949\right)^{\mathrm{T}},\quad x^{\left(3\right)}=x^{\left(2\right)}.
$$

用 Rayleigh 商检验特征值: $\left(x^{\mathrm{T}}Ax\right)/\left(x^{\mathrm{T}}x\right)=1.267949$, 与 $3-\sqrt{3}$ 吻合到小数点后 $6$ 位.

保留 $4$ 位有效数字, 所求特征向量为 $\left(1,\ -0.7321,\ 0.2679\right)^{\mathrm{T}}$. 校验 $\left(A-\left(3-\sqrt{3}\right)I\right)x=0$: 第一个方程 $2-0.732051=1.267949=\left(3-\sqrt{3}\right)\times1$; 第二个方程 $1-2.196153+0.267949=-0.928204$ 而 $\left(3-\sqrt{3}\right)\times\left(-0.732051\right)=-0.928204$; 第三个方程 $-0.732051+1.071796=0.339745$ 而 $\left(3-\sqrt{3}\right)\times0.267949=0.339745$, 三式全部成立.

$\blacksquare$

## 习题 4-7 (Rayleigh 商的两个极值性质)

设 $A$ 为 $n$ 阶实对称矩阵, 对任意非零向量 $x\in\mathbb{R}^{n}$, 称 $\dfrac{\left\langle Ax,x\right\rangle}{\left\langle x,x\right\rangle}=\dfrac{x^{\mathrm{T}}Ax}{x^{\mathrm{T}}x}$ 为 $A$ 的 Rayleigh 商, 求证

$$
\min_{x\ne0}\frac{\left\langle Ax,x\right\rangle}{\left\langle x,x\right\rangle}=\min\lambda\left(A\right),\qquad \max_{x\ne0}\frac{\left\langle Ax,x\right\rangle}{\left\langle x,x\right\rangle}=\max\lambda\left(A\right).
$$

### 解答 4-7

$A$ 实对称, 故存在正交矩阵 $Q=\left(q_1,\ldots,q_n\right)$ 使 $Q^{\mathrm{T}}AQ=\Lambda=\operatorname{diag}\left(\lambda_1,\ldots,\lambda_n\right)$, 其列 $q_i$ 是标准正交的特征向量. 对任意 $x\ne0$ 令 $x=Qc$, $c=\left(c_1,\ldots,c_n\right)^{\mathrm{T}}\ne0$, 则 $\left\langle x,x\right\rangle=c^{\mathrm{T}}Q^{\mathrm{T}}Qc=c^{\mathrm{T}}c=\sum_i c_i^{2}$, 而

$$
\left\langle Ax,x\right\rangle=x^{\mathrm{T}}Ax=c^{\mathrm{T}}Q^{\mathrm{T}}AQc=c^{\mathrm{T}}\Lambda c=\sum_{i=1}^{n}\lambda_ic_i^{2}.
$$

记 $R\left(x\right)=\dfrac{\left\langle Ax,x\right\rangle}{\left\langle x,x\right\rangle}$, 于是

$$
R\left(x\right)=\frac{\sum_{i=1}^{n}\lambda_ic_i^{2}}{\sum_{i=1}^{n}c_i^{2}}.
$$

这是 $\lambda_1,\ldots,\lambda_n$ 以 $c_i^{2}/\sum_jc_j^{2}$ 为权的加权平均 (权非负且和为 $1$), 故

$$
\min_i\lambda_i\le R\left(x\right)\le\max_i\lambda_i.
$$

即 $\min\lambda\left(A\right)\le R\left(x\right)\le\max\lambda\left(A\right)$ 对一切 $x\ne0$ 成立, 故

$$
\inf_{x\ne0}R\left(x\right)\ge\min\lambda\left(A\right),\qquad \sup_{x\ne0}R\left(x\right)\le\max\lambda\left(A\right).
$$

另一方向: 取 $x$ 为 $\lambda_{\min}$ 对应的特征向量 $q_{i_0}$, 则 $c=e_{i_0}$, $R\left(x\right)=\lambda_{i_0}=\min\lambda\left(A\right)$; 取 $x$ 为 $\lambda_{\max}$ 对应的特征向量, 同理 $R\left(x\right)=\max\lambda\left(A\right)$. 两个极值都能取到, 且 $\left\{R\left(x\right):x\ne0\right\}$ 是闭区间 $\left[\min\lambda,\max\lambda\right]$ (因 $R$ 在单位球面上连续), 故 $\min$ 与 $\max$ 都写成可得的最小值与最大值.

$\blacksquare$

## 习题 4-8(2) (Jacobi 方法求全部特征值)

用 Jacobi 方法求矩阵

$$
A=\begin{pmatrix}2&-1&0\\-1&-2&-1\\0&-1&2\end{pmatrix}
$$

的全部特征值.

### 解答 4-8(2)

$A$ 实对称, 按**定理 4.1 (古典 Jacobi 法的收敛性)**, 逐次用平面旋转变换 $A^{\left(k\right)}=P_k^{\mathrm{T}}A^{\left(k-1\right)}P_k$ 把非对角元逐个化为零, 对角元收敛于全部特征值.

每步取剩余元素中绝对值最大者 $\left(p,q\right)$, 由 $\tau=\left(a_{qq}-a_{pp}\right)/\left(2a_{pq}\right)$ 定出旋转角 $\theta$:

$$
t=\frac{\operatorname{sgn}\tau}{\left|\tau\right|+\sqrt{1+\tau^{2}}},\qquad c=\frac{1}{\sqrt{1+t^{2}}},\qquad s=tc.
$$

(1) 第 $1$ 步. $\left|a_{12}\right|=1$ 最大, $p=1$, $q=2$, $\tau=\left(-2-2\right)/\left(2\times\left(-1\right)\right)=2$, $t=0.236068$, $\theta=13.3^{\circ}$, 变换后

$$
A^{\left(1\right)}=\begin{pmatrix}2.236068&0&0.229753\\0&-2.236068&-0.973249\\0.229753&-0.973249&2\end{pmatrix}.
$$

(2) 第 $2$ 步. $\left|a_{23}\right|=0.973249$ 最大, $p=2$, $q=3$, $\tau=-2.176251$, $t=-0.218758$, $\theta=-12.3^{\circ}$, 得

$$
A^{\left(2\right)}=\begin{pmatrix}2.236068&0.049099&0.224445\\0.049099&-2.448974&0\\0.224445&0&2.212906\end{pmatrix}.
$$

(3) 第 $3$ 步. $\left|a_{13}\right|=0.224445$ 最大, $p=1$, $q=3$, $\tau=-0.051598$, $t=-0.949732$, $\theta=-43.5^{\circ}$, 得

$$
A^{\left(3\right)}=\begin{pmatrix}2.449231&0.035602&0\\0.035602&-2.448974&-0.033812\\0&-0.033812&1.999743\end{pmatrix}.
$$

(4) 第 $4$ 至 $7$ 步. 继续按最大非对角元旋转, 旋转角依次为 $-0.4^{\circ}$ 与 $-0.4^{\circ}$ 与 $0.0^{\circ}$ 与 $0.0^{\circ}$, 非对角元迅速降到 $10^{-6}$ 以下, 得

$$
A^{\left(7\right)}=\begin{pmatrix}2.449490&0&0\\0&-2.449490&0\\0&0&2.000000\end{pmatrix}.
$$

对角元即特征值: $\lambda_1=2.449490$ 与 $\lambda_2=2.000000$ 与 $\lambda_3=-2.449490$.

校验: 直接算 $A$ 的特征多项式

$$
\det\left(\lambda I-A\right)=\left(\lambda-2\right)\left[\left(\lambda-2\right)\left(\lambda+2\right)-1\right]-\left(\lambda-2\right)=\left(\lambda-2\right)\left(\lambda^{2}-6\right),
$$

故特征值为 $2$ 与 $\pm\sqrt{6}=2.449490$, 与迭代结果一致. Jacobi 方法每步只做正交相似变换, 所以对角元之和(迹 $2$)与特征值乘积(行列式 $2\times\left(-6\right)=-12$)都与原矩阵相同, 可作过程校验.

$\blacksquare$

## 习题 5-3 (三阶 Lagrange 插值多项式)

已知函数表

| $x_i$ | $1$ | $3$ | $4$ | $6$ |
|---|---|---|---|---|
| $f\left(x_i\right)$ | $-7$ | $5$ | $8$ | $14$ |

试求其三阶 Lagrange 插值多项式, 并以此计算 $f\left(2\right)$ 的近似值.

### 解答 5-3

四个节点互异, 由**定理 5.1 (插值多项式的存在唯一性)**, 过这四个点的次数不超过 $3$ 的多项式存在且唯一, 即三阶 Lagrange 插值多项式

$$
L_3\left(x\right)=\sum_{j=0}^{3}f\left(x_j\right)l_j\left(x\right),\qquad l_j\left(x\right)=\prod_{k\ne j}\frac{x-x_k}{x_j-x_k}.
$$

先算各基函数的分母:

$$
\prod_{k\ne0}\left(x_0-x_k\right)=\left(-2\right)\left(-3\right)\left(-5\right)=-30,\qquad \prod_{k\ne1}\left(x_1-x_k\right)=2\times\left(-1\right)\times\left(-3\right)=6,
$$

$$
\prod_{k\ne2}\left(x_2-x_k\right)=3\times1\times\left(-2\right)=-6,\qquad \prod_{k\ne3}\left(x_3-x_k\right)=5\times3\times2=30,
$$

故

$$
L_3\left(x\right)=-\frac{7}{-30}\left(x-3\right)\left(x-4\right)\left(x-6\right)+\frac{5}{6}\left(x-1\right)\left(x-4\right)\left(x-6\right)-\frac{8}{6}\left(x-1\right)\left(x-3\right)\left(x-6\right)+\frac{14}{30}\left(x-1\right)\left(x-3\right)\left(x-4\right).
$$

把四个三次乘积展开:

$$
\left(x-3\right)\left(x-4\right)\left(x-6\right)=x^{3}-13x^{2}+54x-72,
$$

$$
\left(x-1\right)\left(x-4\right)\left(x-6\right)=x^{3}-11x^{2}+34x-24,
$$

$$
\left(x-1\right)\left(x-3\right)\left(x-6\right)=x^{3}-10x^{2}+27x-18,
$$

$$
\left(x-1\right)\left(x-3\right)\left(x-4\right)=x^{3}-8x^{2}+19x-12.
$$

代入 $L_3$ 并按 $x^{3}$, $x^{2}$, $x$ 与常数项分别合并:

$$
\left[x^{3}\right]:\ \frac{7}{30}+\frac{5}{6}-\frac{4}{3}+\frac{7}{15}=\frac{7+25-40+14}{30}=\frac{6}{30}=\frac{1}{5},
$$

$$
\left[x^{2}\right]:\ \frac{7}{30}\times\left(-13\right)+\frac{5}{6}\times\left(-11\right)+\left(-\frac{4}{3}\right)\times\left(-10\right)+\frac{7}{15}\times\left(-8\right)=\frac{-91-275+400-112}{30}=-\frac{78}{30}=-\frac{13}{5},
$$

$$
\left[x\right]:\ \frac{7}{30}\times54+\frac{5}{6}\times34+\left(-\frac{4}{3}\right)\times27+\frac{7}{15}\times19=\frac{378+850-1080+266}{30}=\frac{414}{30}=\frac{69}{5},
$$

$$
\left[1\right]:\ \frac{7}{30}\times\left(-72\right)+\frac{5}{6}\times\left(-24\right)+\left(-\frac{4}{3}\right)\times\left(-18\right)+\frac{7}{15}\times\left(-12\right)=\frac{-504-600+720-168}{30}=-\frac{552}{30}=-\frac{92}{5}.
$$

故

$$
L_3\left(x\right)=\frac{1}{5}x^{3}-\frac{13}{5}x^{2}+\frac{69}{5}x-\frac{92}{5}=\frac{x^{3}-13x^{2}+69x-92}{5}.
$$

用插值条件复核:

$$
L_3\left(1\right)=\frac{1-13+69-92}{5}=\frac{-35}{5}=-7,\quad L_3\left(3\right)=\frac{27-117+207-92}{5}=\frac{25}{5}=5,
$$

$$
L_3\left(4\right)=\frac{64-208+276-92}{5}=\frac{40}{5}=8,\quad L_3\left(6\right)=\frac{216-468+414-92}{5}=\frac{70}{5}=14,
$$

四个条件全部满足, 与唯一性一致.

于是

$$
f\left(2\right)\approx L_3\left(2\right)=\frac{8-52+138-92}{5}=\frac{2}{5}=0.4.
$$

若改用基函数直接代入 $x=2$ 也可得到同一结果:

$$
-\frac{7}{-30}\times\left(-1\right)\left(-2\right)\left(-4\right)+\frac{5}{6}\times1\times\left(-2\right)\left(-4\right)-\frac{8}{6}\times1\times\left(-1\right)\left(-4\right)+\frac{14}{30}\times1\times\left(-1\right)\times\left(-2\right)
$$

$$
=-\frac{56}{30}+\frac{40}{6}-\frac{32}{6}+\frac{28}{30}=-\frac{56}{30}-5.3333+6.6667+0.9333=0.4.
$$

$\blacksquare$
