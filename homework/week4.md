# week4

> **定义 3.3 (谱半径)**
> 
> 设 $A$ 为 $n$ 阶方阵, $\lambda_i$ ($i=1,2,\ldots,n$) 为 $A$ 的特征值, 称特征值绝对值的最大值 $\rho\left(A\right)=\max_i\left|\lambda_i\right|$ 为 $A$ 的谱半径. (教材 $\S3.2$, p81)

> **定理 3.6 (迭代法收敛的充要条件)**
> 
> 对任意初始向量 $x^{\left(0\right)}$ 和右端项 $g$, 由迭代格式 $x^{\left(k+1\right)}=Mx^{\left(k\right)}+g$ 产生的向量序列 $\left\{x^{\left(k\right)}\right\}$ 收敛的充要条件是 $\rho\left(M\right)<1$. (教材 $\S3.2$, p82)

> **推论 3.1 (范数判别法)**
> 
> 设迭代格式 $x^{\left(k+1\right)}=Mx^{\left(k\right)}+g$, 若 $\left\|M\right\|<1$ (某种矩阵范数), 则向量序列 $\left\{x^{\left(k\right)}\right\}$ 收敛. (教材 $\S3.2$, p84)

> **定义 3.4 (严格对角占优矩阵)**
> 
> 若 $n$ 阶方阵 $A=\left(a_{ij}\right)$ 满足 $\left|a_{ii}\right|>\sum_{j\ne i}\left|a_{ij}\right|$ ($i=1,2,\ldots,n$), 则称 $A$ 为按行严格对角占优矩阵. (教材 $\S3.3$, p85)

## 习题 3-5 (Jacobi 迭代收敛性与参数 $a$ 的关系)

若用 Jacobi 迭代法求解方程组

$$
\begin{pmatrix}a&-1&-3\\-1&a&-2\\3&-2&a\end{pmatrix}\begin{pmatrix}x_1\\x_2\\x_3\end{pmatrix}=\begin{pmatrix}b_1\\b_2\\b_3\end{pmatrix},
$$

讨论实数 $a$ 与收敛性的关系.

### 解答 3-5

Jacobi 迭代要求对角元非零, 故先排除 $a=0$: 此时 $a_{11}=a_{22}=a_{33}=0$, 而

$$
\det A=\begin{vmatrix}a&-1&-3\\-1&a&-2\\3&-2&a\end{vmatrix}=a\left(a^{2}-4\right)+\left(-a+6\right)-3\left(2-3a\right)=a\left(a^{2}+4\right),
$$

在 $a=0$ 处 $\det A=0$, 方程组退化, 迭代格式也无定义.

设 $D=a I$, $L+U=A-D$, 则 Jacobi 迭代矩阵

$$
B_J=D^{-1}\left(L+U\right)=I-\frac{1}{a}A=\frac{1}{a}C,\qquad C=\begin{pmatrix}0&1&3\\1&0&2\\-3&2&0\end{pmatrix}.
$$

$B_J$ 与 $C$ 只差因子 $1/a$, 故 $\rho\left(B_J\right)=\rho\left(C\right)/\left|a\right|$. 求 $C$ 的特征多项式:

$$
\det\left(\lambda I-C\right)=\begin{vmatrix}\lambda&-1&-3\\-1&\lambda&-2\\3&-2&\lambda\end{vmatrix}
=\lambda\left(\lambda^{2}-4\right)-\left(-1\right)\left(-\lambda+6\right)+\left(-3\right)\left(2-3\lambda\right)
=\lambda^{3}+4\lambda.
$$

故 $C$ 的特征值为 $\lambda_1=0$, $\lambda_{2,3}=\pm2\mathrm{i}$, 由**定义 3.3 (谱半径)** 得 $\rho\left(C\right)=2$, 于是

$$
\rho\left(B_J\right)=\frac{2}{\left|a\right|}.
$$

由**定理 3.6 (迭代法收敛的充要条件)**, Jacobi 迭代对任意初值收敛当且仅当 $\rho\left(B_J\right)<1$, 即 $\left|a\right|>2$. 分三种情形:

- $\left|a\right|>2$: $\rho\left(B_J\right)<1$, 对任意初值收敛;
- $\left|a\right|=2$: $\rho\left(B_J\right)=1$, 不满足充要条件, 迭代不收敛 (特征值模为 $1$, 迭代值只作有界摆动而不趋于解);
- $0<\left|a\right|<2$: $\rho\left(B_J\right)>1$, 对任意初值发散.

注意 $C$ 的特征值是纯虚数, 这说明迭代矩阵非对称时谱半径可以完全由复特征值决定, 判断收敛必须算 $\rho$ 而不能只看对角占优.

$\blacksquare$

## 习题 3-7 (三种迭代法的公式与迭代矩阵与收敛性)

设有方程组

$$
\begin{cases}10x_1+4x_2+4x_3=13,\\ 4x_1+10x_2+8x_3=11,\\ 4x_1+8x_2+10x_3=25.\end{cases}
$$

(1) 分别写出 Jacobi 迭代法, Gauss-Seidel 迭代法及 SOR 法 ($\omega=1.35$) 的计算公式及迭代矩阵;

(2) 对任意初值, 各迭代法是否收敛? 说明理由.

### 解答 3-7

记 $A$ 为系数矩阵, $D=10I$, $L$, $U$ 分别为 $A$ 的严格下三角与上三角部分.

(1) Jacobi 迭代公式 (用旧值 $x^{\left(k\right)}$ 整体更新):

$$
x_1^{\left(k+1\right)}=\frac{13-4x_2^{\left(k\right)}-4x_3^{\left(k\right)}}{10},\quad x_2^{\left(k+1\right)}=\frac{11-4x_1^{\left(k\right)}-8x_3^{\left(k\right)}}{10},\quad x_3^{\left(k+1\right)}=\frac{25-4x_1^{\left(k\right)}-8x_2^{\left(k\right)}}{10}.
$$

迭代矩阵

$$
B_J=D^{-1}\left(L+U\right)=I-\frac{1}{10}A=\begin{pmatrix}0&-0.4&-0.4\\-0.4&0&-0.8\\-0.4&-0.8&0\end{pmatrix}.
$$

Gauss-Seidel 迭代公式 (算出的新分量立即投入使用):

$$
x_1^{\left(k+1\right)}=\frac{13-4x_2^{\left(k\right)}-4x_3^{\left(k\right)}}{10},\quad x_2^{\left(k+1\right)}=\frac{11-4x_1^{\left(k+1\right)}-8x_3^{\left(k\right)}}{10},\quad x_3^{\left(k+1\right)}=\frac{25-4x_1^{\left(k+1\right)}-8x_2^{\left(k+1\right)}}{10}.
$$

迭代矩阵 $B_{GS}=\left(D+L\right)^{-1}\left(-U\right)$, 逐列解 $\left(D+L\right)Y=-U$ 得

$$
B_{GS}=\begin{pmatrix}0&-0.4&-0.4\\0&0.16&-0.64\\0&0.032&0.672\end{pmatrix}.
$$

SOR 法 ($\omega=1.35$) 公式为 $x_i^{\left(k+1\right)}=\left(1-\omega\right)x_i^{\left(k\right)}+\omega\cdot\left(\text{Gauss-Seidel 的第 }i\text{ 个分量}\right)$, 即

$$
x_1^{\left(k+1\right)}=\left(1-\omega\right)x_1^{\left(k\right)}+1.35\times\frac{13-4x_2^{\left(k\right)}-4x_3^{\left(k\right)}}{10},
$$

$$
x_2^{\left(k+1\right)}=\left(1-\omega\right)x_2^{\left(k\right)}+1.35\times\frac{11-4x_1^{\left(k+1\right)}-8x_3^{\left(k\right)}}{10},
$$

$$
x_3^{\left(k+1\right)}=\left(1-\omega\right)x_3^{\left(k\right)}+1.35\times\frac{25-4x_1^{\left(k+1\right)}-8x_2^{\left(k+1\right)}}{10},
$$

其中 $1-\omega=1-1.35=-0.35$, 即松弛因子取 $1.35>1$ 属超松弛, 新算出的 Gauss-Seidel 分量被"过量"外推.

迭代矩阵 $B_{SOR}=\left(D+\omega L\right)^{-1}\left(\left(1-\omega\right)D-\omega U\right)$, 计算得

$$
B_{SOR}=\begin{pmatrix}-0.35&-0.54&-0.54\\0.189&-0.0584&-0.7884\\-0.01512&0.354672&0.793072\end{pmatrix}.
$$

$\blacksquare$

(2) 收敛性. 由**定理 3.6 (迭代法收敛的充要条件)**, 逐个算谱半径.

$A$ 对称, 其特征多项式为

$$
\det\left(\lambda I-A\right)=\lambda^{3}-30\lambda^{2}+204\lambda-296,
$$

特征值 $\lambda_1=20.9282$, $\lambda_2=7.0718$, $\lambda_3=2$. 因 $D=10I$, $B_J=I-A/10$ 的特征值为 $1-\lambda_i/10$, 即 $-1.0928$, $0.2928$, $0.8$, 故由**定义 3.3 (谱半径)**

$$
\rho\left(B_J\right)=1.0928>1,
$$

Jacobi 迭代对任意初值发散. 直观原因是 $\left|a_{11}\right|=10$ 虽大于 $4+4$, 但 $\left|a_{23}\right|=8$ 与 $10$ 相比过大, 迭代把误差放大.

$B_{GS}$ 的特征多项式为

$$
\det\left(\lambda I-B_{GS}\right)=\lambda\left(\lambda^{2}-0.832\lambda+0.128\right),
$$

特征值为 $0$, $0.6283$, $0.2037$, 故 $\rho\left(B_{GS}\right)=0.6283<1$, Gauss-Seidel 迭代对任意初值收敛.

$B_{SOR}$ 的谱半径为

$$
\rho\left(B_{SOR}\right)=0.4463<1,
$$

SOR 法 ($\omega=1.35$) 对任意初值收敛, 且收敛最快 ($0.4463<0.6283$).

三个方法的判别差别有结构上的原因: $A$ 的顺序主子式 $10$, $84$, $296$ 全正, 故 $A$ 对称正定, 对称正定矩阵上的 Gauss-Seidel 迭代必收敛; 而 Jacobi 迭代收敛还要求 $2D-A$ 正定, 这里 $2D-A=20I-A$ 的特征值为 $-0.9282$, $12.9282$, $18$, 出现负值, 故 Jacobi 反而发散. 这也说明"Gauss-Seidel 一定比 Jacobi 好"只对特定矩阵类成立.

$\blacksquare$

## 习题 3-8 (构造收敛的迭代式)

设有方程组

$$
\begin{pmatrix}1.2&-3.6&-12\\-10&9&0.5\\1&-4&2\end{pmatrix}\begin{pmatrix}x_1\\x_2\\x_3\end{pmatrix}=\begin{pmatrix}1\\2\\3\end{pmatrix},
$$

试写出收敛的迭代式, 并说明理由.

### 解答 3-8

原系数矩阵按行并非全部严格对角占优: 第 $1$ 行 $\left|1.2\right|<3.6+12$, 第 $3$ 行 $\left|2\right|<1+4$, 只有第 $2$ 行 $\left|-10\right|=10>9+0.5$ 占优. 但每行的最大系数落在不同的未知量上: 第 $1$ 行最大的是 $x_3$ 的系数 $-12$, 第 $2$ 行是 $x_1$ 的系数 $-10$, 第 $3$ 行是 $x_2$ 的系数 $-4$. 于是重排未知量次序, 令

$$
y_1=x_3,\qquad y_2=x_1,\qquad y_3=x_2,
$$

方程组等价地写成

$$
\begin{pmatrix}-12&1.2&-3.6\\0.5&-10&9\\2&1&-4\end{pmatrix}\begin{pmatrix}y_1\\y_2\\y_3\end{pmatrix}=\begin{pmatrix}1\\2\\3\end{pmatrix}.
$$

记此系数矩阵为 $B$. 按**定义 3.4 (严格对角占优矩阵)** 逐行检查:

$$
\left|-12\right|=12>1.2+3.6=4.8,\qquad \left|-10\right|=10>0.5+9=9.5,\qquad \left|-4\right|=4>2+1=3,
$$

$B$ 按行严格对角占优.

(1) 收敛的迭代式. Jacobi 迭代 (整体更新 $y^{\left(k\right)}$):

$$
y_1^{\left(k+1\right)}=\frac{1-1.2y_2^{\left(k\right)}+3.6y_3^{\left(k\right)}}{-12},\quad y_2^{\left(k+1\right)}=\frac{2-0.5y_1^{\left(k\right)}-9y_3^{\left(k\right)}}{-10},\quad y_3^{\left(k+1\right)}=\frac{3-2y_1^{\left(k\right)}-y_2^{\left(k\right)}}{-4},
$$

即

$$
y^{\left(k+1\right)}=B_Jy^{\left(k\right)}+g,\qquad B_J=\begin{pmatrix}0&0.1&-0.3\\0.05&0&0.9\\0.5&0.25&0\end{pmatrix},\qquad g=\begin{pmatrix}-0.08333\\-0.2\\-0.75\end{pmatrix},
$$

其中 $g=D^{-1}b$ 的分量为 $\left(1/\left(-12\right),\ 2/\left(-10\right),\ 3/\left(-4\right)\right)^{\mathrm{T}}$. 回到原变量即 $x_1=y_2$, $x_2=y_3$, $x_3=y_1$.

(2) Gauss-Seidel 迭代 (新分量立即代入):

$$
y_1^{\left(k+1\right)}=\frac{1-1.2y_2^{\left(k\right)}+3.6y_3^{\left(k\right)}}{-12},\quad y_2^{\left(k+1\right)}=\frac{2-0.5y_1^{\left(k+1\right)}-9y_3^{\left(k\right)}}{-10},\quad y_3^{\left(k+1\right)}=\frac{3-2y_1^{\left(k+1\right)}-y_2^{\left(k+1\right)}}{-4}.
$$

对应迭代矩阵

$$
B_{GS}=\begin{pmatrix}0&0.1&-0.3\\0&0.005&0.885\\0&0.05125&0.07125\end{pmatrix}.
$$

$\blacksquare$

(3) 收敛理由. 严格对角占优恰好给出迭代矩阵的行范数上界. 对 Jacobi 迭代, $B_J$ 的第 $i$ 行绝对值之和为 $\sum_{j\ne i}\left|b_{ij}\right|/\left|b_{ii}\right|$, 故

$$
\left\|B_J\right\|_{\infty}=\max\left\{\frac{4.8}{12},\ \frac{9.5}{10},\ \frac{3}{4}\right\}=\max\left\{0.4,\ 0.95,\ 0.75\right\}=0.95<1,
$$

由**推论 3.1 (范数判别法)**, Jacobi 迭代对任意初值收敛. 对 Gauss-Seidel 迭代, 三行的绝对值之和分别为 $0.4$, $0.89$, $0.1225$, 故

$$
\left\|B_{GS}\right\|_{\infty}=0.89<1,
$$

同样由**推论 3.1 (范数判别法)** 知 Gauss-Seidel 迭代对任意初值收敛. 并且 $\rho\left(B_J\right)=0.4217$, $\rho\left(B_{GS}\right)=0.2537$, 两者都小于 $1$, 与范数判别给出的结论一致, 且 Gauss-Seidel 收敛更快.

$\blacksquare$

## 习题 4-1(2) (幂法求按模最大特征值)

用幂法计算矩阵

$$
A=\begin{pmatrix}4&-1&1\\-1&3&-2\\1&-2&3\end{pmatrix}
$$

的按模最大的特征值及相应的特征向量, 取 $x^{\left(0\right)}=\left(1,0,0\right)^{\mathrm{T}}$.

### 解答 4-1(2)

先算 $A$ 的全部特征值, 以确认主特征值唯一且模最大:

$$
\det\left(\lambda I-A\right)=\begin{vmatrix}\lambda-4&1&-1\\1&\lambda-3&2\\-1&2&\lambda-3\end{vmatrix}=\lambda^{3}-10\lambda^{2}+27\lambda-18=\left(\lambda-1\right)\left(\lambda-3\right)\left(\lambda-6\right),
$$

故 $\lambda_1=6$, $\lambda_2=3$, $\lambda_3=1$, 主特征值为 $6$, 且 $\left|\lambda_1\right|>\left|\lambda_2\right|$.

幂法迭代: 取 $y^{\left(k\right)}=Ax^{\left(k-1\right)}$, 令 $\mu_k$ 为 $y^{\left(k\right)}$ 中绝对值最大的分量, $x^{\left(k\right)}=y^{\left(k\right)}/\mu_k$. 从 $x^{\left(0\right)}=\left(1,0,0\right)^{\mathrm{T}}$ 出发:

$$
y^{\left(1\right)}=\left(4,-1,1\right)^{\mathrm{T}},\quad \mu_1=4,\quad x^{\left(1\right)}=\left(1,-0.25,0.25\right)^{\mathrm{T}};
$$

$$
y^{\left(2\right)}=\left(4.5,-2.25,2.25\right)^{\mathrm{T}},\quad \mu_2=4.5,\quad x^{\left(2\right)}=\left(1,-0.5,0.5\right)^{\mathrm{T}};
$$

$$
y^{\left(3\right)}=A x^{\left(2\right)}=\left(5,-3.5,3.5\right)^{\mathrm{T}},\quad \mu_3=5,\quad x^{\left(3\right)}=\left(1,-0.7,0.7\right)^{\mathrm{T}}.
$$

继续迭代, 结果列表 ($x^{\left(k\right)}$ 的第一分量按定义恒为 $1$):

| $k$ | $\mu_k$ | $x^{\left(k\right)}$ 的第 $2$ 与第 $3$ 分量 |
|---|---|---|
| $4$ | $5.400$ | $-0.8333$ , $0.8333$ |
| $5$ | $5.667$ | $-0.9118$ , $0.9118$ |
| $6$ | $5.824$ | $-0.9545$ , $0.9545$ |
| $7$ | $5.909$ | $-0.9769$ , $0.9769$ |
| $8$ | $5.954$ | $-0.9884$ , $0.9884$ |

$\mu_k$ 单调上升趋于 $6$, 特征向量趋于 $\left(1,-1,1\right)^{\mathrm{T}}$. 校验: 

$$
A\begin{pmatrix}1\\-1\\1\end{pmatrix}=\begin{pmatrix}4+1+1\\-1-3-2\\1+2+3\end{pmatrix}=\begin{pmatrix}6\\-6\\6\end{pmatrix}=6\begin{pmatrix}1\\-1\\1\end{pmatrix},
$$

故按模最大的特征值为 $\lambda_1=6$, 相应特征向量为 $\left(1,-1,1\right)^{\mathrm{T}}$ (任意非零倍数).

收敛速度由 $\left|\lambda_2/\lambda_1\right|=3/6=1/2$ 决定, 这与表中相邻两次 $\mu_k$ 的误差比 $0.6\to0.55\to0.53\to0.52$ 趋于 $0.5$ 相符. 另外 $x^{\left(0\right)}$ 在 $\lambda_3=1$ 的特征子空间上分量为零, 这不影响幂法收敛, 只使误差中少了一个衰减最慢的分量.

$\blacksquare$
