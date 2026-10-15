# 作业 3

> **雅可比迭代法** (式 (3.12)) <br>设方程组 $Ax=b$ 的系数矩阵 $A$ 分裂为 $A=D-L-U$, 其中 $D=\mathrm{diag}\left(a_{11},a_{22},\dots,a_{nn}\right)$, 则雅可比迭代格式为 $$x^{\left(k+1\right)}=Bx^{\left(k\right)}+g,\quad B=I-D^{-1}A,\quad g=D^{-1}b,$$ 分量形式为 $$x_i^{\left(k+1\right)}=\frac{1}{a_{ii}}\left(b_i-\sum_{j\ne i}a_{ij}x_j^{\left(k\right)}\right),\ i=1,2,\dots,n.$$

> **高斯-赛德尔迭代法** (式 (3.15)) <br>在雅可比迭代中, 一旦新分量 $x_i^{\left(k+1\right)}$ 算出即立即用于后续分量的计算, 便得高斯-赛德尔迭代法, 其矩阵形式为 $$x^{\left(k+1\right)}=\left(D-L\right)^{-1}Ux^{\left(k\right)}+\left(D-L\right)^{-1}b,$$ 迭代矩阵为 $M=\left(D-L\right)^{-1}U$.

> **松弛迭代法 (逐次超松弛法) ** (式 (3.17)) <br>在高斯-赛德尔迭代基础上引入松弛因子 $\omega$, 得 $$x^{\left(k+1\right)}=\left(D-\omega L\right)^{-1}\left[\left(1-\omega\right)D+\omega U\right]x^{\left(k\right)}+\omega\left(D-\omega L\right)^{-1}b,$$ 迭代矩阵为 $M_{\omega}=\left(D-\omega L\right)^{-1}\left[\left(1-\omega\right)D+\omega U\right]$; 当 $\omega=1$ 时即为高斯-赛德尔迭代法.

> **定义 3.3** (谱半径) <br>设 $A$ 为 $n$ 阶方阵, $\lambda_i\left(i=1,2,\dots,n\right)$ 为 $A$ 的特征值, 称特征值绝对值的最大值为矩阵 $A$ 的谱半径, 记为 $$\rho\left(A\right)=\max_{1\le i\le n}\left|\lambda_i\right|.$$

> **定理 3.6** (迭代法收敛的充要条件) <br>对任意初始向量 $x^{\left(0\right)}$ 和右端项 $g$, 由迭代格式 $x^{\left(k+1\right)}=Mx^{\left(k\right)}+g$ 产生的向量序列收敛的充要条件是 $$\rho\left(M\right)<1.$$

> **定义 3.4** (对角占优矩阵) <br>若 $n$ 阶方阵 $A=\left(a_{ij}\right)$ 满足 $$\left|a_{ii}\right|\ge\sum_{j\ne i}\left|a_{ij}\right|\quad\left(i=1,2,\dots,n\right),$$ 且至少有一个 $i$ 使严格不等式成立, 则称 $A$ 为弱对角占优矩阵; 若对所有 $i$ 均严格成立, 则称 $A$ 为严格对角占优矩阵.

> **几个常用的充分收敛条件** (判敛) <br>设方程组 $Ax=b$: (1) 若 $A$ 为严格对角占优矩阵 (或不可约弱对角占优矩阵) , 则雅可比迭代法与高斯-赛德尔迭代法均收敛; (2) 若 $A$ 为对称正定矩阵且 $0<\omega<2$, 则松弛法收敛 (此条件为充要条件) .

### 习题一 (习题 3-3)

用雅可比迭代法和高斯-赛德尔迭代法求解方程组

$$
\begin{cases}x_1+2x_2-2x_3=1,\\x_1+x_2+x_3=1,\\2x_1+2x_2+x_3=1,\end{cases}
$$

取初值 $x^{\left(0\right)}=\left(0,0,0\right)^{T}$, 迭代 4 次, 并比较它们的计算结果.

### 解答 习题一

系数矩阵 $A=\begin{bmatrix}1&2&-2\\1&1&1\\2&2&1\end{bmatrix}$, $b=\left(1,1,1\right)^{T}$.

由**雅可比迭代法** (式 (3.12)) , 因 $a_{ii}=1$, 迭代公式为

$$
x_1^{\left(k+1\right)}=1-2x_2^{\left(k\right)}+2x_3^{\left(k\right)},
$$

$$
x_2^{\left(k+1\right)}=1-x_1^{\left(k\right)}-x_3^{\left(k\right)},
$$

$$
x_3^{\left(k+1\right)}=1-2x_1^{\left(k\right)}-2x_2^{\left(k\right)}.
$$

从 $x^{\left(0\right)}=\left(0,0,0\right)^{T}$ 出发, 得

$$
x^{\left(1\right)}=\left(1,1,1\right)^{T},\quad x^{\left(2\right)}=\left(1,-1,-3\right)^{T},
$$

$$
x^{\left(3\right)}=\left(-3,3,1\right)^{T},\quad x^{\left(4\right)}=\left(-3,3,1\right)^{T}.
$$

由**高斯-赛德尔迭代法** (式 (3.15)) , 迭代公式为

$$
x_1^{\left(k+1\right)}=1-2x_2^{\left(k\right)}+2x_3^{\left(k\right)},
$$

$$
x_2^{\left(k+1\right)}=1-x_1^{\left(k+1\right)}-x_3^{\left(k\right)},
$$

$$
x_3^{\left(k+1\right)}=1-2x_1^{\left(k+1\right)}-2x_2^{\left(k+1\right)}.
$$

从 $x^{\left(0\right)}=\left(0,0,0\right)^{T}$ 出发, 得

$$
x^{\left(1\right)}=\left(1,0,-1\right)^{T},\quad x^{\left(2\right)}=\left(-1,3,-3\right)^{T},
$$

$$
x^{\left(3\right)}=\left(-11,15,-7\right)^{T},\quad x^{\left(4\right)}=\left(-43,51,-15\right)^{T}.
$$

比较: 雅可比迭代在第 3 步即达到精确解 $x=\left(-3,3,1\right)^{T}$ (代入原方程组验证: $Ax=\left(1,1,1\right)^{T}=b$) , 第 4 步保持不变; 高斯-赛德尔迭代的各分量绝对值迅速增大, 呈发散趋势. 事实上, $D=I$, 雅可比迭代矩阵 $B=I-A$ 满足特征方程 $\det\left(\lambda I-B\right)=\lambda^{3}=0$, 故 $\rho\left(B\right)=0<1$; 而高斯-赛德尔迭代矩阵 $M=\left(D-L\right)^{-1}U$ 的特征方程为 $\det\left(\lambda I-M\right)=\lambda\left(\lambda-2\right)^{2}=0$, 特征值为 $0,2,2$, 故 $\rho\left(M\right)=2>1$. 由**定理 3.6** (迭代法收敛的充要条件) , 雅可比迭代收敛而高斯-赛德尔迭代发散. $\blacksquare$

### 习题二 (习题 3-5)

若用雅可比迭代法求解方程组

$$
\begin{bmatrix}a&-1&-3\\-1&a&-2\\3&-2&a\end{bmatrix}\begin{bmatrix}x_1\\x_2\\x_3\end{bmatrix}=\begin{bmatrix}b_1\\b_2\\b_3\end{bmatrix},
$$

讨论实数 $a$ 与收敛性的关系.

### 解答 习题二

由**雅可比迭代法** (式 (3.12)) , $D=\mathrm{diag}\left(a,a,a\right)$, 雅可比迭代矩阵为

$$
B=I-D^{-1}A=\begin{bmatrix}0&1/a&3/a\\1/a&0&2/a\\-3/a&2/a&0\end{bmatrix}=\frac{1}{a}C,\quad C=\begin{bmatrix}0&1&3\\1&0&2\\-3&2&0\end{bmatrix}.
$$

矩阵 $C$ 的特征方程为

$$
\det\left(\lambda I-C\right)=\det\begin{bmatrix}\lambda&-1&-3\\-1&\lambda&-2\\3&-2&\lambda\end{bmatrix}=\lambda^{3}+4\lambda=\lambda\left(\lambda^{2}+4\right)=0,
$$

故 $C$ 的特征值为 $0,\ 2i,\ -2i$, 从而 $B$ 的特征值为 $0,\ \frac{2i}{a},\ -\frac{2i}{a}$. 由**定义 3.3** (谱半径) , $$
\rho\left(B\right)=\left|\frac{2}{a}\right|.
$$

由**定理 3.6** (迭代法收敛的充要条件) , 雅可比迭代法收敛当且仅当 $\rho\left(B\right)<1$, 即 $\left|\frac{2}{a}\right|<1$, 亦即

$$
\left|a\right|>2\quad\left(a\ne0\right).
$$

故当且仅当实数 $a$ 满足 $\left|a\right|>2$ 时, 雅可比迭代法收敛. $\blacksquare$

### 习题三 (习题 3-7)

设有方程组

$$
\begin{cases}10x_1+4x_2+4x_3=13,\\4x_1+10x_2+8x_3=11,\\4x_1+8x_2+10x_3=25.\end{cases}
$$ (1) 分别写出雅可比迭代法, 高斯-赛德尔迭代法及逐次超松弛法 ($\omega=1.35$) 的计算公式及迭代矩阵; (2) 对任意初值, 各迭代法是否收敛? 说明理由.

### 解答 习题三

系数矩阵 $A=\begin{bmatrix}10&4&4\\4&10&8\\4&8&10\end{bmatrix}$, $b=\left(13,11,25\right)^{T}$, $D=\mathrm{diag}\left(10,10,10\right)$. (1) 由**雅可比迭代法** (式 (3.12)) , 计算公式为

$$
x_1^{\left(k+1\right)}=1.3-0.4x_2^{\left(k\right)}-0.4x_3^{\left(k\right)},
$$

$$
x_2^{\left(k+1\right)}=1.1-0.4x_1^{\left(k\right)}-0.8x_3^{\left(k\right)},
$$

$$
x_3^{\left(k+1\right)}=2.5-0.4x_1^{\left(k\right)}-0.8x_2^{\left(k\right)},
$$

迭代矩阵

$$
B=\begin{bmatrix}0&-0.4&-0.4\\-0.4&0&-0.8\\-0.4&-0.8&0\end{bmatrix}.
$$

由**高斯-赛德尔迭代法** (式 (3.15)) , 计算公式为

$$
x_1^{\left(k+1\right)}=1.3-0.4x_2^{\left(k\right)}-0.4x_3^{\left(k\right)},
$$

$$
x_2^{\left(k+1\right)}=1.1-0.4x_1^{\left(k+1\right)}-0.8x_3^{\left(k\right)},
$$

$$
x_3^{\left(k+1\right)}=2.5-0.4x_1^{\left(k+1\right)}-0.8x_2^{\left(k+1\right)},
$$

迭代矩阵 $M=\left(D-L\right)^{-1}U$.

由**松弛迭代法 (逐次超松弛法) ** (式 (3.17)) , $\omega=1.35$, 计算公式为

$$
x_1^{\left(k+1\right)}=-0.35x_1^{\left(k\right)}+1.35\left(1.3-0.4x_2^{\left(k\right)}-0.4x_3^{\left(k\right)}\right),
$$

$$
x_2^{\left(k+1\right)}=-0.35x_2^{\left(k\right)}+1.35\left(1.1-0.4x_1^{\left(k+1\right)}-0.8x_3^{\left(k\right)}\right),
$$

$$
x_3^{\left(k+1\right)}=-0.35x_3^{\left(k\right)}+1.35\left(2.5-0.4x_1^{\left(k+1\right)}-0.8x_2^{\left(k+1\right)}\right),
$$

迭代矩阵 $M_{\omega}=\left(D-\omega L\right)^{-1}\left[\left(1-\omega\right)D+\omega U\right]$. (2) 先判断 $A$ 的正定性: $A^{T}=A$ 为对称矩阵, 其各阶顺序主子式为

$$
\Delta_1=10>0,\quad\Delta_2=\det\begin{bmatrix}10&4\\4&10\end{bmatrix}=84>0,
$$

$$
\Delta_3=\det A=10\left(100-64\right)-4\left(40-32\right)+4\left(32-40\right)=296>0,
$$

故 $A$ 为对称正定矩阵. 由**几个常用的充分收敛条件** (判敛) 之 (2) , 因 $0<\omega=1.35<2$, 逐次超松弛法收敛; 高斯-赛德尔迭代法对应 $\omega=1$, 亦收敛.

对雅可比迭代法, $B$ 的特征方程为

$$
\det\left(\lambda I-B\right)=\det\begin{bmatrix}\lambda&0.4&0.4\\0.4&\lambda&0.8\\0.4&0.8&\lambda\end{bmatrix}=\lambda^{3}-0.96\lambda+0.256=0.
$$

分解得 $\left(\lambda-0.8\right)\left(\lambda^{2}+0.8\lambda-0.32\right)=0$, 三个特征值为 $0.8,\ 0.293,\ -1.093$, 故 $\rho\left(B\right)\approx1.093>1$. 由**定理 3.6** (迭代法收敛的充要条件) , 雅可比迭代法发散.

综上, 对任意初值, 高斯-赛德尔迭代法与逐次超松弛法 ($\omega=1.35$) 收敛, 雅可比迭代法发散. $\blacksquare$

### 习题四 (习题 3-8)

设有方程组

$$
\begin{bmatrix}1.2&-3.6&-12\\-10&9&0.5\\1&-4&2\end{bmatrix}\begin{bmatrix}x_1\\x_2\\x_3\end{bmatrix}=\begin{bmatrix}1\\2\\3\end{bmatrix},
$$

试写出收敛的迭代式, 并说明理由.

### 解答 习题四

原系数矩阵 $A=\begin{bmatrix}1.2&-3.6&-12\\-10&9&0.5\\1&-4&2\end{bmatrix}$ 不是对角占优矩阵 (第一行 $\left|1.2\right|<3.6+12$, 第二行 $\left|9\right|<10+0.5$, 第三行 $\left|2\right|<1+4$) . 交换方程组的方程次序 (即对系数矩阵作行交换, 不改变方程组的解) , 取新方程次序为原第二, 三, 一行, 得同解方程组

$$
\begin{bmatrix}-10&9&0.5\\1&-4&2\\1.2&-3.6&-12\end{bmatrix}\begin{bmatrix}x_1\\x_2\\x_3\end{bmatrix}=\begin{bmatrix}2\\3\\1\end{bmatrix}.
$$

逐行验证对角占优: $$
\left|-10\right|=10>9+0.5=9.5,\quad\left|-4\right|=4>1+2=3,\quad\left|-12\right|=12>1.2+3.6=4.8.
$$

由**定义 3.4** (对角占优矩阵) , 重排后的系数矩阵为**严格对角占优矩阵**. 由**几个常用的充分收敛条件** (判敛) 之 (1) , 雅可比迭代法与高斯-赛德尔迭代法均收敛.

写出收敛的雅可比迭代式 (对重排后的方程组) : $$
x_1^{\left(k+1\right)}=\frac{2-9x_2^{\left(k\right)}-0.5x_3^{\left(k\right)}}{-10}=-0.2+0.9x_2^{\left(k\right)}+0.05x_3^{\left(k\right)},
$$

$$
x_2^{\left(k+1\right)}=\frac{3-x_1^{\left(k\right)}-2x_3^{\left(k\right)}}{-4}=-0.75+0.25x_1^{\left(k\right)}+0.5x_3^{\left(k\right)},
$$

$$
x_3^{\left(k+1\right)}=\frac{1-1.2x_1^{\left(k\right)}+3.6x_2^{\left(k\right)}}{-12}=-\frac{1}{12}+0.1x_1^{\left(k\right)}-0.3x_2^{\left(k\right)}.
$$

由**定理 3.6** (迭代法收敛的充要条件) , 该迭代格式对任意初值均收敛. $\blacksquare$
