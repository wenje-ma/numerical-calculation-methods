# 作业 6

> **线性最小二乘法的一般形式** (式(6.7)–(6.9)) <br>对数据组 $\left(x_i,y_i\right)\left(i=1,2,\dots,n\right)$, 取 $\left[a,b\right]$ 上一组线性无关的函数 $\varphi_k\left(x\right)\left(k=0,1,\dots,m\right)$, 求 $p\left(x\right)=\sum_{k=0}^m a_k\varphi_k\left(x\right)$ 使残差加权平方和 $\sum_{i=1}^n w_i\left[y_i-p\left(x_i\right)\right]^2$ 最小. 系数满足正则方程组 $$\sum_{k=0}^m a_k\left(\varphi_k,\varphi_j\right)=\left(y,\varphi_j\right)\qquad\left(j=0,1,\dots,m\right),\qquad\left(\varphi_k,\varphi_j\right)=\sum_{i=1}^n w_i\varphi_k\left(x_i\right)\varphi_j\left(x_i\right),\qquad\left(y,\varphi_j\right)=\sum_{i=1}^n w_i y_i\varphi_j\left(x_i\right).$$ 特别地, 取 $\varphi_k\left(x\right)=x^k$ 即多项式拟合; 一次拟合 $y=a_0+a_1x$ ($w_i=1$) 的正则方程组为 $$\begin{cases}n a_0+a_1\sum\limits_{i=1}^n x_i=\sum\limits_{i=1}^n y_i,\\a_0\sum\limits_{i=1}^n x_i+a_1\sum\limits_{i=1}^n x_i^2=\sum\limits_{i=1}^n x_i y_i.\end{cases}$$

> **非线性拟合的线性化** (6.1.2 指数拟合, 6.1.3 分式线性拟合) <br>对指数型 $y=ae^{bx}$, 两端取对数得 $\ln y=\ln a+bx$, 先对变换后的数据组 $\left(x_i,\ln y_i\right)$ 按**线性最小二乘法的一般形式**作一次线性拟合, 再取指数还原; 对可分离变量的分式型 $y=\dfrac{x}{ax+b}$, 两端取倒数得 $\dfrac{1}{y}=a+b\dfrac{1}{x}$, 先对数据组 $\left(\dfrac{1}{x_i},\dfrac{1}{y_i}\right)$ 作一次线性拟合, 再取倒数还原.

> **定义 6.2** (正交函数系) <br>若函数系 $\left\{\varphi_k\left(x\right)\right\}$ 在区间 $\left[a,b\right]$ 上满足 $\left(\varphi_j,\varphi_k\right)=\int_a^b w\left(x\right)\varphi_j\left(x\right)\varphi_k\left(x\right)\,\mathrm dx=0\ \left(j\ne k\right)$ 且 $\left(\varphi_k,\varphi_k\right)>0$, 则称其为 $\left[a,b\right]$ 上关于权函数 $w\left(x\right)$ 的正交函数系, 其中 $\left(\varphi,\psi\right)=\int_a^b w\left(x\right)\varphi\left(x\right)\psi\left(x\right)\,\mathrm dx$ 称为函数的内积.

> **定义 6.3** (最佳平方逼近函数) <br>设 $f\left(x\right)$ 在 $\left[a,b\right]$ 上连续, $H=\operatorname{Span}\left\{\varphi_0,\varphi_1,\dots,\varphi_m\right\}$, 若 $p\left(x\right)=\sum_{k=0}^m a_k\varphi_k\left(x\right)$ 使 $\int_a^b w\left(x\right)\left[f\left(x\right)-p\left(x\right)\right]^2\,\mathrm dx$ 为最小, 则称 $p\left(x\right)$ 为 $f\left(x\right)$ 在 $H$ 中关于权函数 $w\left(x\right)$ 的最佳平方逼近函数.

> **最佳平方逼近的正则方程组** (式(6.32), (6.35), (6.36)) <br>按**定义 6.3**, 系数 $a_k$ 满足正则方程组 $\sum_{k=0}^m a_k\left(\varphi_k,\varphi_j\right)=\left(f,\varphi_j\right)\ \left(j=0,1,\dots,m\right)$, 其中 $\left(f,\varphi_j\right)=\int_a^b w\left(x\right)f\left(x\right)\varphi_j\left(x\right)\,\mathrm dx$. 若 $\left\{\varphi_k\right\}$ 为正交函数系, 则方程组对角化, 解为 $a_k=\dfrac{\left(f,\varphi_k\right)}{\left(\varphi_k,\varphi_k\right)}$, 最佳平方逼近函数为 $p\left(x\right)=\sum_{k=0}^m\dfrac{\left(f,\varphi_k\right)}{\left(\varphi_k,\varphi_k\right)}\varphi_k\left(x\right)$.

> **勒让德多项式** (式(6.18), (6.19)) <br>前几项为 $P_0\left(x\right)=1$, $P_1\left(x\right)=x$, $P_2\left(x\right)=\dfrac{3x^2-1}{2}$, $P_3\left(x\right)=\dfrac{5x^3-3x}{2}$. 它是 $\left[-1,1\right]$ 上关于权 $w\left(x\right)\equiv1$ 的正交多项式系, 且 $\left(P_n,P_m\right)=0\ \left(n\ne m\right)$, $\left(P_n,P_n\right)=\dfrac{2}{2n+1}$. 在区间 $\left[a,b\right]$ 上使用时作变量替换 $t=\dfrac{2x-\left(b+a\right)}{b-a}$, 取 $\varphi_k\left(x\right)=P_k\left(t\right)$.

### 习题一 (习题 6-1)

已知数据表如下: $x_i=1.36,1.49,1.73,1.81,1.95,2.16,2.28,2.48$; $y_i=14.094,15.069,16.844,17.378,18.435,19.949,20.963,22.495$. 试求其最小二乘一次拟合多项式.

### 解答 习题一

设一次拟合多项式为 $y=a_0+a_1x$, 按**线性最小二乘法的一般形式** (一次拟合正则方程组) , 由 $n=8$ 计算各求和项: $$
\sum_{i=1}^8 x_i=15.26,\qquad\sum_{i=1}^8 y_i=145.227,\qquad\sum_{i=1}^8 x_i^2=30.1556,\qquad\sum_{i=1}^8 x_i y_i=284.83628.
$$

代入正则方程组: $$
\begin{cases}8a_0+15.26a_1=145.227,\\15.26a_0+30.1556a_1=284.83628.\end{cases}
$$

解得 $a_0\approx3.9161$, $a_1\approx7.4639$. 故所求最小二乘一次拟合多项式为

$$
P_1\left(x\right)=3.9161+7.4639x.
$$

$\blacksquare$

### 习题二 (习题 6-3)

某平炉的生产记录见下表: $i=1,2,3,4,5$; $x_i=165,123,150,121,141$ (钢液含碳量) ; $y_i=187,126,172,125,148$ (冶炼时间) . 求钢液含碳量与冶炼时间的函数关系.

### 解答 习题二

按散点分布近似直线, 设含碳量 $x$ 与冶炼时间 $y$ 的函数关系为 $y=a_0+a_1x$. 由**线性最小二乘法的一般形式** (一次拟合正则方程组) , $n=5$, 各求和项为

$$
\sum_{i=1}^5 x_i=700,\qquad\sum_{i=1}^5 y_i=758,\qquad\sum_{i=1}^5 x_i^2=99376,\qquad\sum_{i=1}^5 x_i y_i=108146.
$$

代入正则方程组: $$
\begin{cases}5a_0+700a_1=758,\\700a_0+99376a_1=108146.\end{cases}
$$

解得 $a_0\approx-54.534$, $a_1\approx1.4724$. 故钢液含碳量与冶炼时间的函数关系近似为

$$
y=-54.534+1.4724x.
$$

$\blacksquare$

### 习题三 (习题 6-4)

用最小二乘法求一形如 $y=a+bx^2$ ($a,b$ 为常数) 的经验公式拟合下列数据: $x_i=19,25,31,38,44$; $y_i=19.0,32.3,49.0,73.3,97.8$.

### 解答 习题三

令 $u=x^2$, 则拟合函数化为 $y=a+bu$, 它是关于基函数 $\varphi_0\left(x\right)=1$, $\varphi_1\left(x\right)=x^2$ 的线性最小二乘问题. 由**线性最小二乘法的一般形式**, 变换后数据为

$$
u_i=x_i^2=361,625,961,1444,1936\qquad\left(n=5\right),
$$

各求和项为

$$
\sum u_i=5327,\qquad\sum y_i=271.4,\qquad\sum u_i^2=7277699,\qquad\sum u_i y_i=369321.5.
$$

代入关于 $a,b$ 的正则方程组: $$
\begin{cases}5a+5327b=271.4,\\5327a+7277699b=369321.5.\end{cases}
$$

解得 $a\approx0.9726$, $b\approx0.05004$. 故所求经验公式为

$$
y=0.9726+0.05004x^2.
$$

$\blacksquare$

### 习题四 (习题 6-6)

用最小二乘法求一形如 $y=ae^{bx}$ ($a,b$ 为常数) 的经验公式拟合下列数据: $x_i=1,2,3,4,5,6,7,8$; $y_i=15.3,20.5,27.4,36.6,49.1,65.6,87.87,117.6$.

### 解答 习题四

按**非线性拟合的线性化** (指数拟合) , 令 $Y=\ln y$, 则 $Y=\left(\ln a\right)+bx$. 对数据组 $\left(x_i,\ln y_i\right)$ 作一次线性最小二乘拟合, $n=8$, $$
Y_i=\ln y_i=2.7279,3.0204,3.3105,3.6001,3.8939,4.1836,4.4759,4.7673,
$$

各求和项为

$$
\sum x_i=36,\qquad\sum Y_i=29.9795,\qquad\sum x_i^2=204,\qquad\sum x_iY_i=147.1406.
$$

代入正则方程组: $$
\begin{cases}8\left(\ln a\right)+36b=29.9795,\\36\left(\ln a\right)+204b=147.1406.\end{cases}
$$

解得 $\ln a\approx2.4367$, $b\approx0.2913$, 从而 $a=e^{2.4367}\approx11.436$. 故所求经验公式为

$$
y=11.436\,e^{0.2913x}.
$$

$\blacksquare$

### 习题五 (习题 6-7)

某化学反应中, 测得生成物的质量浓度 $y$ 与时间 $t$ 的关系见下表 (单位略) : $t_i=1,2,3,4,6,8,10,12,14,16$; $y_i=4.00,6.41,8.01,8.79,9.53,9.86,10.33,10.42,10.53,10.61$. 试用最小二乘法求一形如 $y=\dfrac{t}{at+b}$ ($a,b$ 为常数) 的经验公式拟合以上数据.

### 解答 习题五

按**非线性拟合的线性化** (分式线性拟合) , 对 $y=\dfrac{t}{at+b}$ 两端取倒数, 得

$$
\frac{1}{y}=a+b\frac{1}{t}.
$$

令 $u=\dfrac{1}{t}$, $z=\dfrac{1}{y}$, 则 $z=a+bu$, 对数据组 $\left(u_i,z_i\right)=\left(\dfrac{1}{t_i},\dfrac{1}{y_i}\right)$ 作一次线性最小二乘拟合. 由 $n=10$, 计算得

$$
\sum u_i=2.6923,\qquad\sum z_i=1.2330,\qquad\sum u_i^2=1.4930,\qquad\sum u_i z_i=0.45858.
$$

代入正则方程组: $$
\begin{cases}10a+2.6923b=1.2330,\\2.6923a+1.4930b=0.45858.\end{cases}
$$

解得 $a\approx0.07891$, $b\approx0.16486$. 故所求经验公式为

$$
y=\frac{t}{0.07891\,t+0.16486}.
$$

$\blacksquare$

### 习题六 (习题 6-10)

证明函数系 $\left\{\varphi_0,\varphi_1,\dots,\varphi_n\right\}$ 线性无关的充要条件是格拉姆行列式 $G\left(\varphi_0,\varphi_1,\dots,\varphi_n\right)\ne0$.

### 解答 习题六

记格拉姆矩阵 $\boldsymbol G=\left[\left(\varphi_i,\varphi_j\right)\right]_{i,j=0}^n$, 其中内积按**定义 6.2** 为 $\left(\varphi_i,\varphi_j\right)=\int_a^b w\left(x\right)\varphi_i\left(x\right)\varphi_j\left(x\right)\,\mathrm dx$, 格拉姆行列式 $G=\det\boldsymbol G$.

对任意向量 $\boldsymbol c=\left(c_0,c_1,\dots,c_n\right)^{T}$, 有

$$
\boldsymbol c^{T}\boldsymbol G\boldsymbol c=\sum_{i=0}^n\sum_{j=0}^n c_i c_j\left(\varphi_i,\varphi_j\right)=\left(\sum_{i=0}^n c_i\varphi_i,\sum_{j=0}^n c_j\varphi_j\right)=\int_a^b w\left(x\right)\left[\sum_{i=0}^n c_i\varphi_i\left(x\right)\right]^2\,\mathrm dx\ge0.
$$

充分性. 设 $G\ne0$, 反设 $\left\{\varphi_i\right\}$ 线性相关, 则存在不全为零的 $\boldsymbol c$ 使 $\sum_{i=0}^n c_i\varphi_i\left(x\right)\equiv0$, 从而 $\boldsymbol c^{T}\boldsymbol G\boldsymbol c=0$. 但 $G\ne0$ 时 $\boldsymbol G$ 可逆 (正定) , $\boldsymbol c\ne0$ 必有 $\boldsymbol c^{T}\boldsymbol G\boldsymbol c>0$, 矛盾. 故 $\left\{\varphi_i\right\}$ 线性无关.

必要性. 设 $\left\{\varphi_i\right\}$ 线性无关, 反设 $G=0$, 则 $\boldsymbol G$ 奇异, 存在非零 $\boldsymbol c$ 使 $\boldsymbol G\boldsymbol c=\boldsymbol0$, 于是 $\boldsymbol c^{T}\boldsymbol G\boldsymbol c=0$, 即

$$
\int_a^b w\left(x\right)\left[\sum_{i=0}^n c_i\varphi_i\left(x\right)\right]^2\,\mathrm dx=0.
$$

因 $w\left(x\right)>0$, 被积函数非负, 故 $\sum_{i=0}^n c_i\varphi_i\left(x\right)\equiv0$, 与 $\left\{\varphi_i\right\}$ 线性无关矛盾. 故 $G\ne0$.

综上, 函数系 $\left\{\varphi_0,\varphi_1,\dots,\varphi_n\right\}$ 线性无关当且仅当格拉姆行列式 $G\ne0$.$\blacksquare$

### 习题七 (习题 6-13)

求下列函数在指定区间上关于 $f\left(x\right)$ 的一次最佳平方逼近多项式: (1) $f\left(x\right)=\sqrt{x}$, $\left[0,1\right]$; (2) $f\left(x\right)=e^x$, $\left[0,1\right]$; (3) $f\left(x\right)=\sin\dfrac{\pi}{2}x$, $\left[0,1\right]$. (仅要求第 (2) 小题) ### 解答 习题七

对 $f\left(x\right)=e^x$, $\left[0,1\right]$, 取权 $w\left(x\right)\equiv1$, 基函数 $\varphi_0\left(x\right)=1$, $\varphi_1\left(x\right)=x$, 即 $H=\operatorname{Span}\left\{1,x\right\}$. 由**定义 6.3** 与**最佳平方逼近的正则方程组** (式(6.32)) , 先计算各内积: $$
\left(\varphi_0,\varphi_0\right)=\int_0^1\mathrm dx=1,\qquad\left(\varphi_0,\varphi_1\right)=\left(\varphi_1,\varphi_0\right)=\int_0^1x\,\mathrm dx=\frac12,\qquad\left(\varphi_1,\varphi_1\right)=\int_0^1x^2\,\mathrm dx=\frac13,
$$

$$
\left(f,\varphi_0\right)=\int_0^1 e^x\,\mathrm dx=e-1,\qquad\left(f,\varphi_1\right)=\int_0^1x e^x\,\mathrm dx=\left[x e^x-e^x\right]_0^1=1.
$$

代入正则方程组: $$
\begin{cases}a_0+\dfrac12 a_1=e-1,\\\dfrac12 a_0+\dfrac13 a_1=1.\end{cases}
$$

解得 $a_0\approx0.8731$, $a_1\approx1.6903$. 故 $f\left(x\right)=e^x$ 在 $\left[0,1\right]$ 上的一次最佳平方逼近多项式为

$$
p\left(x\right)=0.8731+1.6903x.
$$

$\blacksquare$

### 习题八 (习题 6-15)

利用勒让德多项式, 求 $f\left(x\right)=\sin x$ 在 $\left[-\dfrac{\pi}{2},\dfrac{\pi}{2}\right]$ 上的三次最佳平方逼近多项式 $P_3\left(x\right)$, 并计算均方误差 $\int_{-\pi/2}^{\pi/2}\left[\sin x-P_3\left(x\right)\right]^2\,\mathrm dx$.

### 解答 习题八

按**最佳平方逼近的正则方程组** (正交情形, 式(6.35), (6.36)) , 在区间 $\left[-\dfrac{\pi}{2},\dfrac{\pi}{2}\right]$ 上取**勒让德多项式**作基. 令变量替换 $t=\dfrac{2x}{\pi}$, 则 $x=\dfrac{\pi}{2}t$, $\mathrm dx=\dfrac{\pi}{2}\mathrm dt$, $t\in\left[-1,1\right]$, 取 $\varphi_k\left(x\right)=P_k\left(t\right)=P_k\!\left(\dfrac{2x}{\pi}\right)$.

由勒让德多项式的正交性 $\left(P_n,P_m\right)=\dfrac{2}{2n+1}\delta_{nm}$, 得

$$
\left(\varphi_k,\varphi_k\right)=\frac{\pi}{2}\int_{-1}^1P_k^2\left(t\right)\,\mathrm dt=\frac{\pi}{2}\cdot\frac{2}{2k+1}=\frac{\pi}{2k+1},
$$

$$
\left(f,\varphi_k\right)=\frac{\pi}{2}\int_{-1}^1\sin\!\left(\frac{\pi t}{2}\right)P_k\left(t\right)\,\mathrm dt.
$$

因 $\sin\!\left(\dfrac{\pi t}{2}\right)$ 为奇函数, $P_0\left(t\right)=1$, $P_2\left(t\right)=\dfrac{3t^2-1}{2}$ 为偶函数, 故 $\left(f,\varphi_0\right)=\left(f,\varphi_2\right)=0$, 只需计算 $a_1,a_3$. 计算积分: $$
\int_{-1}^1 t\sin\!\left(\frac{\pi t}{2}\right)\mathrm dt=\frac{8}{\pi^2},\qquad\int_{-1}^1 t^3\sin\!\left(\frac{\pi t}{2}\right)\mathrm dt=\frac{24}{\pi^2}-\frac{192}{\pi^4},
$$

于是

$$
\left(f,\varphi_1\right)=\frac{\pi}{2}\cdot\frac{8}{\pi^2}=\frac{4}{\pi},\qquad\left(f,\varphi_3\right)=\frac{\pi}{2}\left[\frac52\left(\frac{24}{\pi^2}-\frac{192}{\pi^4}\right)-\frac32\cdot\frac{8}{\pi^2}\right]=\frac{24}{\pi}-\frac{240}{\pi^3}.
$$

由式(6.35): $$
a_1=\frac{\left(f,\varphi_1\right)}{\left(\varphi_1,\varphi_1\right)}=\frac{4/\pi}{\pi/3}=\frac{12}{\pi^2}\approx1.2159,
$$

$$
a_3=\frac{\left(f,\varphi_3\right)}{\left(\varphi_3,\varphi_3\right)}=\frac{24/\pi-240/\pi^3}{\pi/7}=\frac{168}{\pi^2}-\frac{1680}{\pi^4}\approx-0.2249.
$$

故三次最佳平方逼近多项式为

$$
P_3\left(x\right)=a_1P_1\!\left(\frac{2x}{\pi}\right)+a_3P_3\!\left(\frac{2x}{\pi}\right)=1.2159\cdot\frac{2x}{\pi}-0.2249\cdot\frac{5\left(2x/\pi\right)^3-3\left(2x/\pi\right)}{2}\approx0.9888x-0.1451x^3.
$$

再由正交性, 均方误差为

$$
\int_{-\pi/2}^{\pi/2}\left[\sin x-P_3\left(x\right)\right]^2\mathrm dx=\left(f,f\right)-a_1^2\left(\varphi_1,\varphi_1\right)-a_3^2\left(\varphi_3,\varphi_3\right),
$$

其中 $\left(f,f\right)=\int_{-\pi/2}^{\pi/2}\sin^2x\,\mathrm dx=\dfrac{\pi}{2}$, 代入得

$$
\int_{-\pi/2}^{\pi/2}\left[\sin x-P_3\left(x\right)\right]^2\mathrm dx=\frac{\pi}{2}-\frac{12^2}{\pi^4}\cdot\frac{\pi}{3}-\left(\frac{168}{\pi^2}-\frac{1680}{\pi^4}\right)^2\frac{\pi}{7}\approx2.42\times10^{-5}.
$$

$\blacksquare$
