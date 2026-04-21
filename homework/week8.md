# week8

> **定义 6.1 (以给定权关于点集的正交函数族)**
> 
> 若函数族 $\left\{\varphi_0\left(x\right),\varphi_1\left(x\right),\ldots,\varphi_m\left(x\right)\right\}$ 满足 $\left(\varphi_k,\varphi_k\right)=\sum_{i=1}^{n}\omega_i\varphi_k^{2}\left(x_i\right)>0$ ($k=0,1,\ldots,m$) 且 $\left(\varphi_k,\varphi_j\right)=0$ ($k\ne j$), 其中 $\left(\varphi_k,\varphi_j\right)=\sum_{i=1}^{n}\omega_i\varphi_k\left(x_i\right)\varphi_j\left(x_i\right)$, 则称它为以 $\left\{\omega_i\right\}$ 为权关于点集 $\left\{x_1,x_2,\ldots,x_n\right\}$ 的正交函数族. (教材 $\S6.1$, p176)

> **定理 6.1 (正则方程组的解即最小二乘函数)**
> 
> 设 $\varphi_0\left(x\right),\ldots,\varphi_m\left(x\right)$ 线性无关, $a_0,a_1,\ldots,a_m$ 为正则方程组 $\sum_{k=0}^{m}\left(\varphi_k,\varphi_j\right)a_k=\left(y,\varphi_j\right)$ ($j=0,1,\ldots,m$) 的解, 则 $\varphi\left(x\right)=\sum_{k=0}^{m}a_k\varphi_k\left(x\right)$ 满足 $\sum_{i=1}^{n}\omega_i\left[y_i-\varphi\left(x_i\right)\right]^{2}=\min_{\psi\in H}\sum_{i=1}^{n}\omega_i\left[y_i-\psi\left(x_i\right)\right]^{2}$. (教材 $\S6.1$, p175)

> **定理 6.2 (正交函数系必定线性无关)**
> 
> 区间 $\left[a,b\right]$ 上关于权函数 $\omega\left(x\right)$ 的正交函数系 $\left\{\varphi_0\left(x\right),\varphi_1\left(x\right),\ldots,\varphi_n\left(x\right)\right\}$ 必定是线性无关的. (教材 $\S6.2$, p179)

> **定义 6.3 (最佳平方逼近多项式)**
> 
> 设 $f\left(x\right)$ 在 $\left[a,b\right]$ 上连续, $\varphi_i\left(x\right)$ ($i=0,1,\ldots,m$) 为 $\left[a,b\right]$ 上线性无关的连续函数, $H=\mathrm{Span}\left\{\varphi_0,\ldots,\varphi_m\right\}$. 若 $\varphi\left(x\right)=\sum_{k=0}^{m}a_k\varphi_k\left(x\right)$ 使 $F\left(a_0,\ldots,a_m\right)=\int_a^b\omega\left(x\right)\left[f\left(x\right)-\sum_{k=0}^{m}a_k\varphi_k\left(x\right)\right]^{2}\mathrm{d}x=\min_{\psi\in H}\int_a^b\omega\left(x\right)\left[f\left(x\right)-\psi\left(x\right)\right]^{2}\mathrm{d}x$, 则称 $\varphi$ 为 $f$ 在 $H$ 中关于权函数 $\omega\left(x\right)$ 的最佳平方逼近函数; 若 $\varphi_k$ 为 $k$ 次多项式, 则称 $\varphi$ 为 $m$ 次最佳平方逼近多项式. 未指明权函数时取 $\omega\left(x\right)\equiv1$. (教材 $\S6.3$, p184)

> **定理 6.5 (最佳平方逼近的充要条件)**
> 
> 设 $f$ 在 $\left[a,b\right]$ 上连续, $\varphi=\sum_{k=0}^{m}a_k\varphi_k$ 是 $f$ 在 $H$ 中关于权函数 $\omega$ 的最佳平方逼近函数的充要条件是 $\left(f-\varphi,\varphi_j\right)=0$ ($j=0,1,\ldots,m$), 其中 $\left(\varphi,\psi\right)=\int_a^b\omega\left(x\right)\varphi\left(x\right)\psi\left(x\right)\mathrm{d}x$. (教材 $\S6.3$, p184)

> **公式 (7.9) (两点公式)**
> 
> 过节点 $x_0$ 与 $x_1=x_0+h$ 作一次插值, 得 $f'\left(x_0\right)\approx\dfrac{f\left(x_1\right)-f\left(x_0\right)}{h}$, $f'\left(x_1\right)\approx\dfrac{f\left(x_1\right)-f\left(x_0\right)}{h}$. (教材 $\S7.1$, p197)

> **公式 (7.10) (两点公式的截断误差)**
> 
> $R_1'\left(x_0\right)=-\dfrac{h}{2}f''\left(\xi_0\right)$, $R_1'\left(x_1\right)=\dfrac{h}{2}f''\left(\xi_1\right)$, 其中 $\xi_0,\xi_1\in\left(x_0,x_1\right)$. (教材 $\S7.1$, p197)

> **公式 (7.11) (三点公式)**
> 
> 取等距节点 $x_i=x_0+ih$ ($i=0,1,2$), 则 $f'\left(x_0\right)\approx\dfrac{1}{2h}\left[-3f\left(x_0\right)+4f\left(x_1\right)-f\left(x_2\right)\right]$, $f'\left(x_1\right)\approx\dfrac{1}{2h}\left[-f\left(x_0\right)+f\left(x_2\right)\right]$, $f'\left(x_2\right)\approx\dfrac{1}{2h}\left[f\left(x_0\right)-4f\left(x_1\right)+3f\left(x_2\right)\right]$. (教材 $\S7.1$, p198)

> **公式 (7.12) (三点公式的截断误差)**
> 
> $R_2'\left(x_0\right)=\dfrac{h^{2}}{3}f^{\left(3\right)}\left(\xi_0\right)$, $R_2'\left(x_1\right)=-\dfrac{h^{2}}{6}f^{\left(3\right)}\left(\xi_1\right)$, $R_2'\left(x_2\right)=\dfrac{h^{2}}{3}f^{\left(3\right)}\left(\xi_2\right)$, 其中 $\xi_i\in\left(x_0,x_2\right)$. (教材 $\S7.1$, p198)

## 习题 6-7 (形如 $y=\dfrac{t}{at+b}$ 的经验公式)

某化学反应中测得生成物的质量浓度 $y$ 与时间 $t$ 的关系为

| $t_i$ | $1$ | $2$ | $3$ | $4$ | $6$ | $8$ | $10$ | $12$ | $14$ | $16$ |
|---|---|---|---|---|---|---|---|---|---|---|
| $y_i$ | $4.00$ | $6.41$ | $8.01$ | $8.79$ | $9.53$ | $9.86$ | $10.33$ | $10.42$ | $10.53$ | $10.61$ |

试用最小二乘法求形如 $y=\dfrac{t}{at+b}$ ($a,b$ 为常数) 的经验公式拟合以上数据.

### 解答 6-7

**线性化**. $y=\dfrac{t}{at+b}$ 且 $y>0$, 取倒数得

$$
\frac{1}{y}=\frac{at+b}{t}=a+b\,\frac{1}{t}.
$$

记 $u_i=\dfrac{1}{t_i}$, $v_i=\dfrac{1}{y_i}$, 则模型 $v=a+bu$ 对参数 $a,b$ 是线性的. 由**定义 6.3 (最佳平方逼近多项式)** 的离散对应, 取 $\varphi_0\left(u\right)=1$, $\varphi_1\left(u\right)=u$, $\omega_i=1$.

**数据**. 十个点上的值:

| $t_i$ | $1$ | $2$ | $3$ | $4$ | $6$ | $8$ | $10$ | $12$ | $14$ | $16$ |
|---|---|---|---|---|---|---|---|---|---|---|
| $u_i=1/t_i$ | $1.000000$ | $0.500000$ | $0.333333$ | $0.250000$ | $0.166667$ | $0.125000$ | $0.100000$ | $0.083333$ | $0.071429$ | $0.062500$ |
| $v_i=1/y_i$ | $0.250000$ | $0.156006$ | $0.124844$ | $0.113765$ | $0.104932$ | $0.101420$ | $0.096805$ | $0.095969$ | $0.094966$ | $0.094251$ |

五个和:

$$
n=10,\quad \sum u_i=2.692262,\quad \sum u_i^{2}=1.492967,\quad \sum v_i=1.232960,\quad \sum u_iv_i=0.458577.
$$

**解**. 由**定理 6.1 (正则方程组的解即最小二乘函数)**, 正则方程组为

$$
\begin{cases}10a+2.692262\,b=1.232960,\\ 2.692262\,a+1.492967\,b=0.458577,\end{cases}
$$

$\Delta=10\times1.492967-2.692262^{2}=14.929670-7.248275=7.681395$, 故

$$
b=\frac{10\times0.458577-2.692262\times1.232960}{7.681395}=\frac{4.585770-3.319454}{7.681395}\approx0.164856,
$$

$$
a=\frac{1.232960\times1.492967-0.458577\times2.692262}{7.681395}=\frac{1.840768-1.234591}{7.681395}\approx0.078912.
$$

于是经验公式为

$$
y=\frac{t}{0.078912\,t+0.164856}.
$$

$\blacksquare$

**残差与模型评价**. 拟合值在 $t=1,2,\ldots,16$ 处依次为 $4.102$, $6.198$, $7.470$, $8.325$, $9.400$, $10.048$, $10.482$, $10.793$, $11.027$, $11.209$, 残差平方和 $\sum\left(y_i-\varphi\right)^{2}=1.384$, 最大偏差 $0.599$ (在 $t=16$ 处). 残差随 $t$ 增大而单调偏负, 说明实测数据比该模型更快饱和: 模型的极限值是 $1/a\approx12.67$, 而数据在 $t=16$ 处只到 $10.61$ 且增速已明显变缓. 这是"先线性化再最小二乘"的通病: 变换把 $v$ 的相对误差当成了 $y$ 的绝对误差, 小 $y$ 处的点 (即大 $t$) 在 $y$ 尺度上被过度压低. 若改用非线性最小二乘可直接最小化 $\sum\left(y_i-\dfrac{t_i}{at_i+b}\right)^{2}$, 参数会略向"更快饱和"一侧移动.

$\blacksquare$

## 习题 6-10 (线性无关与 Gram 行列式)

证明函数系 $\left\{\varphi_0,\varphi_1,\ldots,\varphi_n\right\}$ 线性无关的充要条件是 Gram 行列式 $G\left(\varphi_0,\varphi_1,\ldots,\varphi_n\right)\ne0$.

### 解答 6-10

**先把"线性无关"定在哪一层**. 由**定义 6.1 (以给定权关于点集的正交函数族)**, 这里的内积是离散和 $\left(\varphi,\psi\right)=\sum_{i=1}^{n}\omega_i\varphi\left(x_i\right)\psi\left(x_i\right)$. 设节点 $x_1,\ldots,x_n$ 互异且权 $\omega_i>0$, 把 $\varphi_k$ 看成在节点上取值的向量 $\Phi_k=\left(\varphi_k\left(x_1\right),\ldots,\varphi_k\left(x_n\right)\right)\in\mathbb{R}^{n}$, 则 $\left(\varphi_k,\varphi_j\right)=\Phi_k^{\mathrm{T}}W\Phi_j$, 其中 $W=\mathrm{diag}\left(\omega_1,\ldots,\omega_n\right)$ 正定. 题目中的"线性无关"就指这组向量的无关性, 这也正是正则方程组系数矩阵非奇异所需要的. 记 $G=\left(\left(\varphi_i,\varphi_j\right)\right)_{i,j=0}^{n}$.

**必要性**. 若 $\left\{\varphi_k\right\}$ 线性相关, 则存在不全为零的 $c_0,\ldots,c_n$ 使 $\Phi c=0$, 其中 $\Phi=\left(\Phi_0,\ldots,\Phi_n\right)$, $c=\left(c_0,\ldots,c_n\right)^{\mathrm{T}}$. 两边左乘 $\Phi^{\mathrm{T}}W$ 得 $\Phi^{\mathrm{T}}W\Phi c=0$, 即 $Gc=0$. 因 $c\ne0$, $G$ 有非零向量被映为零, 故 $\det G=0$.

$\blacksquare$

**充分性**. 若 $\det G=0$, 则 $G$ 奇异, 存在 $c\ne0$ 使 $Gc=0$. 两边左乘 $c^{\mathrm{T}}$ 得

$$
c^{\mathrm{T}}Gc=\sum_{i=0}^{n}\sum_{j=0}^{n}c_ic_j\left(\varphi_i,\varphi_j\right)=\left(\sum_{i=0}^{n}c_i\varphi_i,\ \sum_{j=0}^{n}c_j\varphi_j\right)=\left(\Phi c\right)^{\mathrm{T}}W\left(\Phi c\right)=0.
$$

$W$ 正定, 故 $\left(\Phi c\right)^{\mathrm{T}}W\left(\Phi c\right)=0$ 当且仅当 $\Phi c=0$. 于是存在不全为零的系数使 $\sum_{k}c_k\Phi_k=0$, 即 $\left\{\Phi_k\right\}$ 线性相关, 与假设矛盾.

$\blacksquare$

**两点附注**. 其一, 若 $\det G\ne0$, 则 $\left\{\varphi_k\right\}$ 作为函数也线性无关: 恒等于零的函数在每个节点取零, 故函数相关必导致向量相关. 其二, 反向不成立, 因为两个不同的函数可以在给定节点上取相同的值; 所以题目把"线性无关"与节点上的 Gram 行列式对应起来, 本质上是在说 $\Phi$ 的列无关性, 而 Gram 矩阵只是 $\Phi$ 的加权 Gram 矩阵, 由 $\Phi^{\mathrm{T}}W\Phi$ 与 $\Phi$ 的列空间维数相同 (因 $W$ 正定) 即可看出.

$\blacksquare$

## 习题 6-13(2) (一次最佳平方逼近: $f\left(x\right)=e^{x}$ 在 $\left[0,1\right]$ 上)

求 $f\left(x\right)=e^{x}$ 在 $\left[0,1\right]$ 上关于权函数 $\omega\left(x\right)\equiv1$ 的一次最佳平方逼近多项式.

### 解答 6-13(2)

取 $\varphi_0\left(x\right)=1$, $\varphi_1\left(x\right)=x$, $\omega\equiv1$, 待求 $\varphi\left(x\right)=a_0+a_1x$. 由**定义 6.3 (最佳平方逼近多项式)**, 一次最佳平方逼近即 $H=\mathrm{Span}\left\{1,x\right\}$ 中的最佳平方逼近函数.

计算内积: $\left(\varphi_0,\varphi_0\right)=\int_0^11\,\mathrm{d}x=1$, $\left(\varphi_0,\varphi_1\right)=\int_0^1x\,\mathrm{d}x=\dfrac{1}{2}$, $\left(\varphi_1,\varphi_1\right)=\int_0^1x^{2}\,\mathrm{d}x=\dfrac{1}{3}$, $\left(f,\varphi_0\right)=\int_0^1e^{x}\,\mathrm{d}x=e-1$, $\left(f,\varphi_1\right)=\int_0^1xe^{x}\,\mathrm{d}x=\left[e^{x}\left(x-1\right)\right]_0^1=1$.

由**定理 6.5 (最佳平方逼近的充要条件)** 的等价形式 (投影条件 $\left(f-\varphi,\varphi_j\right)=0$), 正则方程组为

$$
\begin{cases}a_0+\dfrac{1}{2}a_1=e-1,\\ \dfrac{1}{2}a_0+\dfrac{1}{3}a_1=1.\end{cases}
$$

由第一式 $a_0=e-1-\dfrac{a_1}{2}$, 代入第二式:

$$
\frac{e-1}{2}-\frac{a_1}{4}+\frac{a_1}{3}=1\quad\Longrightarrow\quad\frac{e-1}{2}+\frac{a_1}{12}=1\quad\Longrightarrow\quad a_1=12\left(1-\frac{e-1}{2}\right)=18-6e,
$$

$$
a_0=e-1-\frac{18-6e}{2}=4e-10.
$$

数值上 $4e-10=0.873127$, $18-6e=1.690309$, 于是

$$
P_1\left(x\right)=0.873127+1.690309\,x.
$$

$\blacksquare$

**最小平方误差**. 由 $\left(f-P_1,P_1\right)=\left(f,P_1\right)-\left(P_1,P_1\right)=0$ 得 $\left(f-P_1,f-P_1\right)=\left(f,f\right)-\left(P_1,P_1\right)=\left(f,f\right)-\sum_{k=0}^{1}a_k\left(f,\varphi_k\right)$, 即

$$
\left\|f-P_1\right\|^{2}=\frac{e^{2}-1}{2}-a_0\left(e-1\right)-a_1\cdot1=3.194528-1.500278-1.690309=0.003941,
$$

故 $\left\|f-P_1\right\|\approx0.06278$. 与最朴素的 $x=0$ 处 Taylor 一次式 $1+x$ 相比: $\left\|f-\left(1+x\right)\right\|^{2}=0.091298$, 是前者的 $23$ 倍. 差别在于 Taylor 式只保证在 $x=0$ 附近精确, 而最佳平方逼近把 $\int_0^1\left(e^{x}-1-x\right)^{2}\mathrm{d}x$ 摊平, 必然把误差从 $x=1$ 一侧挪向内部, 端点误差最大且两侧反号, 这正是平方逼近中的等振荡现象.

$\blacksquare$

## 习题 6-15 (用 Legendre 多项式求 $f\left(x\right)=\sin x$ 的三次最佳平方逼近)

利用 Legendre 多项式, 求 $f\left(x\right)=\sin x$ 在 $\left[-\dfrac{\pi}{2},\dfrac{\pi}{2}\right]$ 上的三次最佳平方逼近多项式 $P_3\left(x\right)$, 并计算均方误差 $\int_{-\pi/2}^{\pi/2}\left[\sin x-P_3\left(x\right)\right]^{2}\mathrm{d}x$.

### 解答 6-15

**变到 $\left[-1,1\right]$**. 令 $x=\dfrac{\pi}{2}t$, 则 $f\left(t\right)=\sin\dfrac{\pi t}{2}$, $t\in\left[-1,1\right]$, 权函数为 $1$. 由**定义 6.3 (最佳平方逼近多项式)**, 三次最佳平方逼近多项式即 $H=\mathrm{Span}\left\{1,t,t^{2},t^{3}\right\}$ 中的最佳平方逼近函数; 取正交基为 Legendre 多项式

$$
P_0\left(t\right)=1,\qquad P_1\left(t\right)=t,\qquad P_2\left(t\right)=\frac{3t^{2}-1}{2},\qquad P_3\left(t\right)=\frac{5t^{3}-3t}{2}.
$$

由**定理 6.2 (正交函数系必定线性无关)**, 这组基线性无关; 它们还是 $\left[-1,1\right]$ 上关于权 $1$ 的正交系, 即 $\left(P_k,P_j\right)=0$ ($k\ne j$), $\left(P_k,P_k\right)=\dfrac{2}{2k+1}$. 于是投影条件 $\left(f-P_3,P_k\right)=0$ 给出

$$
a_k=\frac{\left(f,P_k\right)}{\left(P_k,P_k\right)},\qquad k=0,1,2,3.
$$

**奇偶性化简**. $f\left(t\right)=\sin\dfrac{\pi t}{2}$ 是奇函数, $P_0$ 与 $P_2$ 是偶函数, $P_1$ 与 $P_3$ 是奇函数, 在对称区间上奇偶函数之积积分为零, 故 $a_0=a_2=0$, 只需算 $a_1,a_3$.

$\blacksquare$

**系数**. 分部积分两次得

$$
\left(f,P_1\right)=\int_{-1}^{1}t\sin\frac{\pi t}{2}\,\mathrm{d}t=2\int_0^1t\sin\frac{\pi t}{2}\,\mathrm{d}t=2\left[-\frac{2}{\pi}t\cos\frac{\pi t}{2}+\frac{4}{\pi^{2}}\sin\frac{\pi t}{2}\right]_0^1=\frac{8}{\pi^{2}},
$$

$$
\left(f,P_3\right)=\int_{-1}^{1}\frac{5t^{3}-3t}{2}\sin\frac{\pi t}{2}\,\mathrm{d}t=\frac{1}{2}\left[5\int_{-1}^{1}t^{3}\sin\frac{\pi t}{2}\,\mathrm{d}t-3\left(f,P_1\right)\right].
$$

其中 $\int_0^1t^{3}\sin\dfrac{\pi t}{2}\,\mathrm{d}t=\left[-\dfrac{2}{\pi}t^{3}\cos\dfrac{\pi t}{2}+\dfrac{12}{\pi^{2}}t^{2}\sin\dfrac{\pi t}{2}+\dfrac{48}{\pi^{3}}t\cos\dfrac{\pi t}{2}-\dfrac{96}{\pi^{4}}\sin\dfrac{\pi t}{2}\right]_0^1=\dfrac{12}{\pi^{2}}-\dfrac{96}{\pi^{4}}$, 由奇偶性

$$
\int_{-1}^{1}t^{3}\sin\frac{\pi t}{2}\,\mathrm{d}t=\frac{24}{\pi^{2}}-\frac{192}{\pi^{4}},
$$

$$
\left(f,P_3\right)=\frac{1}{2}\left[5\left(\frac{24}{\pi^{2}}-\frac{192}{\pi^{4}}\right)-3\cdot\frac{8}{\pi^{2}}\right]=\frac{48}{\pi^{2}}-\frac{480}{\pi^{4}}.
$$

于是

$$
a_1=\frac{8/\pi^{2}}{2/3}=\frac{12}{\pi^{2}}\approx1.215854,\qquad a_3=\frac{48/\pi^{2}-480/\pi^{4}}{2/7}=\frac{168}{\pi^{2}}-\frac{1680}{\pi^{4}}\approx-0.224891.
$$

$\blacksquare$

**回代**. $P_3\left(t\right)=a_1P_1\left(t\right)+a_3P_3\left(t\right)=1.215854\,t-0.224891\cdot\dfrac{5t^{3}-3t}{2}$. 以 $t=\dfrac{2x}{\pi}$ 代回:

$$
P_3\left(x\right)=0.988792\,x-0.145062\,x^{3}.
$$

校验: $P_3\left(0\right)=0=\sin0$; 在 $x=\dfrac{\pi}{4}$ 处 $P_3=0.706317$, $\sin\dfrac{\pi}{4}=0.707107$, 差 $7.9\times10^{-4}$; 在 $x=\dfrac{\pi}{2}$ 处 $P_3=0.990963$, 与 $\sin\dfrac{\pi}{2}=1$ 差 $9.0\times10^{-3}$, 这也是整区间上的最大偏差 (平方逼近的最大误差出现在端点, 因权函数为 $1$ 而端点的"权重"与内部相同, 平方尺度下内点误差被分摊得更小).

$\blacksquare$

**均方误差**. 先算 $t$ 区间上的误差, 再由 $\mathrm{d}x=\dfrac{\pi}{2}\mathrm{d}t$ 换算. 因 $\left\{P_k\right\}$ 正交,

$$
\left\|f-P_3\right\|_{t}^{2}=\left(f,f\right)-\sum_{k=0}^{3}a_k^{2}\left(P_k,P_k\right),\qquad \left(f,f\right)=\int_{-1}^{1}\sin^{2}\frac{\pi t}{2}\,\mathrm{d}t=1,
$$

$$
\sum_{k}a_k^{2}\left(P_k,P_k\right)=a_1^{2}\cdot\frac{2}{3}+a_3^{2}\cdot\frac{2}{7}=1.4783\times\frac{2}{3}+0.050576\times\frac{2}{7}=0.985534+0.014450=0.999984,
$$

故 $\left\|f-P_3\right\|_{t}^{2}=1.5386\times10^{-5}$, 于是

$$
\int_{-\pi/2}^{\pi/2}\left[\sin x-P_3\left(x\right)\right]^{2}\mathrm{d}x=\frac{\pi}{2}\cdot1.5386\times10^{-5}\approx2.417\times10^{-5},
$$

即均方根误差约 $4.9\times10^{-3}$.

$\blacksquare$

**说明**. 三次逼近只用了一个奇基函数之外的两个奇分量, 误差已到 $10^{-5}$ 量级; 若用 Taylor 三次式 $x-\dfrac{x^{3}}{6}$ 在端点处误差达 $0.075$, 可见"最佳平方"与"局部展开"是两种不同的最优性, 前者把误差在整个区间上摊平. 又因 $\left(f,P_2\right)=0$, 若硬取 $\mathrm{Span}\left\{1,x,x^{2},x^{3}\right\}$ 的一般基做正则方程组, 会得到一个 Hilbert 型病态方程组, 用正交基则只需两次内积, 这就是**定理 6.2 (正交函数系必定线性无关)** 之后引入正交多项式的实际理由.

$\blacksquare$

## 习题 7-3 (两点公式与三点公式的精度)

设 $f\left(x\right)=\dfrac{1}{\left(1+x\right)^{2}}$, 取步长 $h=0.1$, 分别用二点公式和三点公式计算 $f'\left(0.5\right)$, 并估计误差.

### 解答 7-3

**真值与导数**. $f'\left(x\right)=-\dfrac{2}{\left(1+x\right)^{3}}$, 故 $f'\left(0.5\right)=-\dfrac{2}{1.5^{3}}=-\dfrac{16}{27}\approx-0.592593$. 又

$$
f''\left(x\right)=\frac{6}{\left(1+x\right)^{4}},\qquad f'''\left(x\right)=-\frac{24}{\left(1+x\right)^{5}}.
$$

**二点公式**. 取 $x_0=0.5$, $x_1=0.6$, 由**公式 (7.9) (两点公式)**,

$$
f'\left(0.5\right)\approx\frac{f\left(0.6\right)-f\left(0.5\right)}{0.1}=\frac{0.3906250-0.4444444}{0.1}=-0.538194,
$$

其中 $f\left(0.5\right)=\dfrac{1}{1.5^{2}}=0.4444444$, $f\left(0.6\right)=\dfrac{1}{1.6^{2}}=0.3906250$.

由**公式 (7.10) (两点公式的截断误差)**, 误差为 $-\dfrac{h}{2}f''\left(\xi\right)$; $f''$ 在 $\left[0.5,0.6\right]$ 上单调减, 故 $\max\left|f''\right|=f''\left(0.5\right)=\dfrac{6}{1.5^{4}}=1.185185$, 于是

$$
\left|R\right|\le\frac{0.1}{2}\times1.185185=0.059259.
$$

$\blacksquare$

**三点公式**. 取 $x_0=0.4$, $x_1=0.5$, $x_2=0.6$ (中点求导), 由**公式 (7.11) (三点公式)**,

$$
f'\left(0.5\right)\approx\frac{f\left(0.6\right)-f\left(0.4\right)}{2\times0.1}=\frac{0.3906250-0.5102041}{0.2}=-0.597895,
$$

其中 $f\left(0.4\right)=\dfrac{1}{1.4^{2}}=0.5102041$.

由**公式 (7.12) (三点公式的截断误差)**, 中点公式的误差为 $-\dfrac{h^{2}}{6}f'''\left(\xi\right)$; $\left|f'''\right|$ 在 $\left[0.4,0.6\right]$ 上单调减, 故 $\max\left|f'''\right|=\left|f'''\left(0.4\right)\right|=\dfrac{24}{1.4^{5}}=\dfrac{24}{5.37824}=4.46243$, 于是

$$
\left|R\right|\le\frac{0.01}{6}\times4.46243=0.007437.
$$

$\blacksquare$

**比较与解释**. 两点公式给出的近似为 $-0.538194$, 实际误差 $0.054398$; 三点公式给出 $-0.597895$, 实际误差 $-0.005303$. 两者都在上面估计的范围之内: $0.054398<0.059259$, $\left|-0.005303\right|<0.007437$. 三点公式比两点公式精确约一个数量级, 与截断误差的阶数 $O\left(h\right)$ 对 $O\left(h^{2}\right)$ 相符. 顺带说明, 三点公式的三个形式中, 中点形式的误差系数是 $1/6$, 端点形式是 $1/3$, 所以同一个 $h$ 下应优先用中点形式.

$\blacksquare$
