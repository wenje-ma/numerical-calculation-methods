# week2

> **定理 2.1 (Doolittle 分解的存在唯一性)**
> 
> 设 $A$ 为 $n$ 阶方阵, 若 $A$ 的顺序主子式 $\det{}A_i$ ($i=1,2,\ldots,n-1$) 均不为零, 则 $A$ 存在唯一的 Doolittle 分解 $A=LU$, 其中 $L$ 为单位下三角阵, $U$ 为上三角阵. (教材 $\S2.2$, p27)

> **定理 2.2 (列主元三角分解)**
> 
> 设矩阵 $A$ 非奇异, 则存在置换矩阵 $P$, 使得 $PA$ 有唯一的 Doolittle 分解 $PA=LU$. (教材 $\S2.3$, p33)

## 习题 1-12 (改造表达式以避免相近数相减)

试改变下列表达式, 使计算结果比较精确:

(1) $\dfrac{1}{1+2x}-\dfrac{1-x}{1+x}$, $\left|x\right|\ll1$;

(2) $\sqrt{x+\dfrac{1}{x}}-\sqrt{x-\dfrac{1}{x}}$, $\left|x\right|\gg1$;

(3) $\dfrac{\tan{}x-\sin{}x}{x^{2}}$, $\left|x\right|\ll1$ 且 $x\ne0$.

### 解答 1-12

(1) 两项都接近 $1$, 直接相减会发生严重抵消 (结果量级为 $x^{2}$, 有效数字几乎全失). 通分合并:

$$
\frac{1}{1+2x}-\frac{1-x}{1+x}=\frac{\left(1+x\right)-\left(1-x\right)\left(1+2x\right)}{\left(1+2x\right)\left(1+x\right)}=\frac{1+x-1-2x+x+2x^{2}}{\left(1+2x\right)\left(1+x\right)}=\frac{2x^{2}}{1+3x+2x^{2}}.
$$

分子与分母都不再是相近数之差, 当 $\left|x\right|\ll1$ 时结果精度好.

$\blacksquare$

(2) 两个根式都接近 $x$, 相减抵消. 用分子有理化:

$$
\sqrt{x+\frac{1}{x}}-\sqrt{x-\frac{1}{x}}=\frac{\left(x+\frac{1}{x}\right)-\left(x-\frac{1}{x}\right)}{\sqrt{x+\frac{1}{x}}+\sqrt{x-\frac{1}{x}}}=\frac{\frac{2}{x}}{\sqrt{x+\frac{1}{x}}+\sqrt{x-\frac{1}{x}}}.
$$

分母是两根式之和 (同号相加, 无抵消), 故对 $\left|x\right|\gg1$ 计算稳定.

$\blacksquare$

(3) 先析出 $\tan{}x$ 的公因子, 再把 $1-\cos{}x$ 换成只含正项的形式:

$$
\frac{\tan{}x-\sin{}x}{x^{2}}=\frac{\tan{}x\left(1-\cos{}x\right)}{x^{2}}=\frac{\sin{}x}{x}\cdot\frac{1-\cos{}x}{x}\cdot\frac{1}{\cos{}x}.
$$

三个因子 $\frac{\sin{}x}{x}$, $\frac{1-\cos{}x}{x}$ 与 $\frac{1}{\cos{}x}$ 当 $\left|x\right|\ll1$ 时都有良好定义 (前两者极限为 $1$ 与 $0$, 第三者为 $1$), 且各自按 Taylor 展开计算都不会出现相近数相减.

$\blacksquare$

## 习题 2-1 (三种直接法解两个三阶方程组)

分别用 Gauss 消去法, 列主元素法与全主元素法解下列方程组, 计算过程保留 $3$ 位小数:

$$
\left(\mathrm{A}\right)\,\begin{cases}2x_1+6x_2-4x_3=4,\\x_1+4x_2-5x_3=3,\\6x_1-x_2+18x_3=2;\end{cases}\quad\left(\mathrm{B}\right)\,\begin{cases}2x_1+x_2+2x_3=6,\\4x_1+3x_2+x_3=11,\\6x_1+x_2+5x_3=13.\end{cases}
$$

### 解答 2-1

先记精确解供校核 (手算通分所得): $\left(\mathrm{A}\right)$ 的解为 $\left(4/3,0,-1/3\right)$; $\left(\mathrm{B}\right)$ 的解为 $\left(1,2,1\right)$.

(1) Gauss 消去法 (不选主元).

$\left(\mathrm{A}\right)$: 第一步 $m_{21}=1/2$, $m_{31}=3$, 消元后

$$
\begin{pmatrix}2&6&-4\\0&1&-3\\0&-19&30\end{pmatrix},\quad\left(4,1,-10\right)^{\mathrm{T}};
$$

第二步 $m_{32}=-19$, 消元得 $a_{33}^{\left(3\right)}=-27$, 第三个方程右端化为 $-10-\left(-19\right)\times1=9$, 即 $-27x_3=9$. 回代

$$
x_3=-1/3=-0.333,\quad{}x_2=1-3\times\left(-1/3\right)=0,\quad{}x_1=\frac{4-6x_2+4x_3}{2}=\frac{4-0-1.333}{2}=1.333.
$$

$\left(\mathrm{B}\right)$: $m_{21}=2$, $m_{31}=3$, 消元后

$$
\begin{pmatrix}2&1&2\\0&1&-3\\0&-2&-1\end{pmatrix},\quad\left(6,-1,-5\right)^{\mathrm{T}};
$$

第二步 $m_{32}=-2$, 得 $a_{33}^{\left(3\right)}=-7$, 右端 $-5-\left(-2\right)\times\left(-1\right)=-7$, 回代

$$
x_3=1,\quad{}x_2=-1+3=2,\quad{}x_1=\frac{6-2-2\times1}{2}=1.
$$

$\blacksquare$

(2) 列主元素法 (每步在该列中取绝对值最大者作主元). 过程保留 $3$ 位小数.

$\left(\mathrm{A}\right)$: 第 $1$ 列 $\left(2,1,6\right)^{\mathrm{T}}$ 中 $6$ 最大, 交换第 $1$ 行与第 $3$ 行, 得主元 $6.000$;

$$
m_{21}=1/6=0.167,\quad{}m_{31}=2/6=0.333,
$$

消元后(第 $2$ 行与第 $3$ 行)

$$
\left(-0.002,4.167,-8.006\,\middle|\,2.666\right),\quad\left(0.002,6.333,-9.994\,\middle|\,3.334\right);
$$

第 $2$ 列中 $\left|6.333\right|>\left|4.167\right|$, 交换第 $2$ 行与第 $3$ 行, 主元 $6.333$, $m_{32}=4.167/6.333=0.658$, 消元得

$$
\left(-0.002,-0.000,-1.430\,\middle|\,0.472\right).
$$

回代:

$$
x_3=\frac{0.472}{-1.430}=-0.330,\quad{}x_2=\frac{2.666-\left(-8.006\right)\left(-0.330\right)}{4.167}=0.006,\quad{}x_1=\frac{4-\left(-4\right)\left(-0.330\right)-6\times0.006}{2}=1.324.
$$

$\left(\mathrm{B}\right)$: 第 $1$ 列中 $6$ 最大, 交换第 $1$ 行与第 $3$ 行, 主元 $6.000$; $m_{21}=4/6=0.667$, $m_{31}=2/6=0.333$, 消元后

$$
\left(-0.002,2.333,-2.335\,\middle|\,2.329\right),\quad\left(0.002,0.667,0.335\,\middle|\,1.671\right);
$$

第 $2$ 步主元 $2.333$, $m_{32}=0.667/2.333=0.286$, 消元得

$$
\left(0.002,-0.000,1.003\,\middle|\,1.005\right).
$$

回代:

$$
x_3=\frac{1.005}{1.003}=1.002,\quad{}x_2=\frac{2.329-\left(-2.335\right)\times1.002}{2.333}=2.001,\quad{}x_1=\frac{6-1.002-2.001\times1}{2}=0.998.
$$

$\blacksquare$

(3) 全主元素法 (每步在剩余子阵中取绝对值最大者, 允许列交换, 解的分量需按列号还原).

$\left(\mathrm{A}\right)$: 剩余 $3\times3$ 子阵中 $\left|18\right|$ 最大 (位置 $\left(3,3\right)$), 交换第 $1$ 行与第 $3$ 行并交换第 $1$ 列与第 $3$ 列, 记列序 $1\to3$, $3\to1$, 故 $x_1$ 与 $x_3$ 互换位置. 主元 $18.000$,

$$
m_{21}=-5/18=-0.278,\quad{}m_{31}=-4/18=-0.222,
$$

消元后

$$
\left(0.004,3.722,2.668\,\middle|\,3.556\right),\quad\left(-0.004,5.778,3.332\,\middle|\,4.444\right).
$$

第 $2$ 步子阵中 $\left|5.778\right|$ 最大, 交换第 $2$ 行与第 $3$ 行, 主元 $5.778$, $m_{32}=3.722/5.778=0.644$, 消元得

$$
\left(0.004,0.001,0.522\,\middle|\,0.694\right).
$$

回代(按置换后的未知量次序 $x_3,x_2,x_1$ 依次求 $z_3,z_2,z_1$):

$$
z_3=x_1=\frac{0.694}{0.522}=1.330,\quad{}z_2=x_2=\frac{3.556-2.668\times1.330}{3.722}=0.003,
$$

$$
z_1=x_3=\frac{2+0.003-6\times1.330}{18}=\frac{2.003-7.980}{18}=-0.332,
$$

其中第一条方程已按列交换后的次序读作 $18z_1-z_2+6z_3=2$.

$\left(\mathrm{B}\right)$: 剩余子阵中 $\left|6\right|$ 最大, 交换第 $1$ 行与第 $3$ 行, 主元 $6.000$, $m_{21}=0.667$, $m_{31}=0.333$, 消元后

$$
\left(-0.002,2.333,-2.335\,\middle|\,2.329\right),\quad\left(0.002,0.667,0.335\,\middle|\,1.671\right).
$$

第 $2$ 步子阵中 $\left|-2.335\right|>\left|2.333\right|$, 交换第 $2$ 列与第 $3$ 列 (即 $x_2$ 与 $x_3$ 互换), 主元 $-2.335$, $m_{32}=0.667/\left(-2.335\right)=-0.143$, 消元得

$$
\left(0.002,0.001,1.001\,\middle|\,2.004\right).
$$

回代(未知量次序 $x_1,x_3,x_2$, 依次求 $z_3,z_2,z_1$):

$$
z_3=x_2=\frac{2.004}{1.001}=2.002,\quad{}z_2=x_3=\frac{2.329-2.333\times2.002}{-2.335}=\frac{-2.338}{-2.335}=1.001,
$$

$$
z_1=x_1=\frac{13-1\times1.001-5\times2.002}{6}=\frac{13-1.001-10.010}{6}=0.999.
$$

$\blacksquare$

(4) 比较. 三种方法的解在 $3$ 位小数下彼此相差不超过 $0.01$, 与精确解 $\left(1.333,0,-0.333\right)$, $\left(1,2,1\right)$ 一致; 差别只来自每步舍入. $\left(\mathrm{A}\right)$ 的 $a_{11}=2$ 并非该列最大元, 不选主元时第 $2$ 步出现 $m_{32}=-19$, 放大倍数很大, 这正是列主元要交换第 $2$ 行与第 $3$ 行的原因.

$\blacksquare$

## 习题 2-2 (用三角分解法解习题 2-1 的两个方程组)

用三角分解法求解题 1 中的方程组.

### 解答 2-2

$\left(\mathrm{A}\right)$ 的系数矩阵顺序主子式为 $\det{}A_1=2\ne0$, $\det{}A_2=2\times4-6\times1=2\ne0$, 由**定理 2.1 (Doolittle 分解的存在唯一性)**, $A$ 有唯一的 Doolittle 分解. 按紧凑格式逐个算出

$$
A=\begin{pmatrix}2&6&-4\\1&4&-5\\6&-1&18\end{pmatrix}=LU,\quad{}L=\begin{pmatrix}1&0&0\\\frac{1}{2}&1&0\\3&-19&1\end{pmatrix},\quad{}U=\begin{pmatrix}2&6&-4\\0&1&-3\\0&0&-27\end{pmatrix}.
$$

校验: 第二行 $\frac{1}{2}\left(2,6,-4\right)+\left(0,1,-3\right)=\left(1,4,-5\right)$; 第三行 $3\left(2,6,-4\right)-19\left(0,1,-3\right)+\left(0,0,-27\right)=\left(6,-1,18\right)$, 均与 $A$ 相合.

解 $Ly=b$: $y_1=4$, $y_2=3-\frac{1}{2}\times4=1$, $y_3=2-3\times4+19\times1=9$. 解 $Ux=y$:

$$
-27x_3=9\Rightarrow{}x_3=-\frac{1}{3},\quad{}x_2-3x_3=1\Rightarrow{}x_2=0,\quad2x_1+6x_2-4x_3=4\Rightarrow{}x_1=\frac{4}{3}.
$$

$\blacksquare$

$\left(\mathrm{B}\right)$: $\det{}A_1=2\ne0$, $\det{}A_2=2\times3-1\times4=2\ne0$, 分解唯一:

$$
L=\begin{pmatrix}1&0&0\\2&1&0\\3&-2&1\end{pmatrix},\quad{}U=\begin{pmatrix}2&1&2\\0&1&-3\\0&0&-7\end{pmatrix}.
$$

解 $Ly=b$: $y_1=6$, $y_2=11-2\times6=-1$, $y_3=13-3\times6+2\times1=-3$ 即 $y_3=13-18-\left(-2\right)\left(-1\right)=-7$. 解 $Ux=y$:

$$
-7x_3=-7\Rightarrow{}x_3=1,\quad{}x_2-3x_3=-1\Rightarrow{}x_2=2,\quad2x_1+x_2+2x_3=6\Rightarrow{}x_1=1.
$$

$\blacksquare$

## 习题 2-3 (紧凑格式求 $L$ 与 $U$ 并解四阶方程组)

用紧凑格式解下列方程组, 并写出 $L$ 与 $U$ 矩阵:

$$
\begin{pmatrix}1&2&3&4\\1&4&9&16\\1&8&27&64\\1&16&81&256\end{pmatrix}\begin{pmatrix}x_1\\x_2\\x_3\\x_4\end{pmatrix}=\begin{pmatrix}2\\10\\44\\190\end{pmatrix}.
$$

### 解答 2-3

系数矩阵的顺序主子式都不为零 ($\det{}A_1=1$, $\det{}A_2=2$, $\det{}A_3=12$, $\det{}A_4=288$), 由**定理 2.1 (Doolittle 分解的存在唯一性)**, 分解存在且唯一. 按紧凑格式 $l_{ik}=\left(a_{ik}-\sum_{s<{}k}l_{is}u_{sk}\right)/u_{kk}$, $u_{kj}=a_{kj}-\sum_{s<{}k}l_{ks}u_{sj}$ 逐行计算:

$$
L=\begin{pmatrix}1&0&0&0\\1&1&0&0\\1&3&1&0\\1&7&6&1\end{pmatrix},\quad{}U=\begin{pmatrix}1&2&3&4\\0&2&6&12\\0&0&6&24\\0&0&0&24\end{pmatrix}.
$$

校验第二行: $\left(1,2,3,4\right)+\left(0,2,6,12\right)=\left(1,4,9,16\right)$; 第三行: $\left(1,2,3,4\right)+3\left(0,2,6,12\right)+\left(0,0,6,24\right)=\left(1,8,27,64\right)$; 第四行: $\left(1,2,3,4\right)+7\left(0,2,6,12\right)+6\left(0,0,6,24\right)+\left(0,0,0,24\right)=\left(1,16,81,256\right)$, 均与 $A$ 相合.

解 $Ly=b$ (前代):

$$
y_1=2,\quad{}y_2=10-2=8,\quad{}y_3=44-2-3\times8=18,\quad{}y_4=190-2-7\times8-6\times18=24.
$$

解 $Ux=y$ (回代):

$$
x_4=\frac{24}{24}=1,\quad{}x_3=\frac{18-24\times1}{6}=-1,
$$

$$
x_2=\frac{8-6\times\left(-1\right)-12\times1}{2}=\frac{8+6-12}{2}=1,\quad{}x_1=2-2x_2-3x_3-4x_4=2-2+3-4=-1.
$$

故解为 $x=\left(-1,1,-1,1\right)^{\mathrm{T}}$. 代回第一个方程校验: $1\times\left(-1\right)+2\times1+3\times\left(-1\right)+4\times1=2$, 与右端一致.

$\blacksquare$
