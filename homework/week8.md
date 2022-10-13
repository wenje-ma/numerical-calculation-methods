# 作业 8

> **定义 8.1** (迭代法与不动点迭代法) <br>将方程 $f\left(x\right)=0$ 改写为等价形式 $x=\varphi\left(x\right)$, 取定初值 $x_0$, 由迭代公式 $$x_{n+1}=\varphi\left(x_n\right)\ \left(n=0,1,2,\dots\right)$$ 产生序列 $\left\{x_n\right\}$; 若 $x_n\to x^{*}$, 则 $x^{*}=\varphi\left(x^{*}\right)$ 称为 $\varphi\left(x\right)$ 的不动点, 上述方法称为迭代法 (不动点迭代法) .

> **定理 8.2** (不动点迭代法的收敛条件) <br>设函数 $\varphi\left(x\right)$ 在区间 $\left[a,b\right]$ 上满足条件: (1) 对任意 $x\in\left[a,b\right]$, 有 $\varphi\left(x\right)\in\left[a,b\right]$; (2) 存在常数 $0<L<1$, 使得对任意 $x\in\left[a,b\right]$, 都有 $\left|\varphi'\left(x\right)\right|\le L$. 则方程 $x=\varphi\left(x\right)$ 在 $\left[a,b\right]$ 上有唯一的根 $x^{*}$, 对任意初值 $x_0\in\left[a,b\right]$, 迭代序列 $x_{n+1}=\varphi\left(x_n\right)$ 收敛于 $x^{*}$, 并有事后误差估计 $$\left|x^{*}-x_n\right|\le\frac{L}{1-L}\left|x_n-x_{n-1}\right|.$$

> **定义 8.2** (迭代法的收敛阶) <br>设序列 $\left\{x_n\right\}$ 收敛于 $x^{*}$, 如果存在正数 $r$ 和 $a$, 使得 $$\lim_{n\to\infty}\frac{\left|x_{n+1}-x^{*}\right|}{\left|x_n-x^{*}\right|^{r}}=a$$ 成立 (当 $r=1$ 时要求 $a<1$) , 则称序列 $\left\{x_n\right\}$ 是 $r$ 阶收敛的; $r=1$ 称线性收敛, $r=2$ 称平方收敛.

> **定理 8.4** (迭代法收敛阶与迭代函数导数的关系) <br>设迭代函数 $\varphi\left(x\right)$ 在 $x^{*}$ 邻近有 $r$ 阶连续导数 $\left(r\ge2\right)$, 且 $x^{*}=\varphi\left(x^{*}\right)$, $\varphi'\left(x^{*}\right)=\varphi''\left(x^{*}\right)=\dots=\varphi^{\left(r-1\right)}\left(x^{*}\right)=0$, 而 $\varphi^{\left(r\right)}\left(x^{*}\right)\ne0$, 则迭代序列 $\left\{x_n\right\}$ 是 $r$ 阶收敛的; 若 $x^{*}=\varphi\left(x^{*}\right)$ 而 $0<\left|\varphi'\left(x^{*}\right)\right|<1$, 则 $\left\{x_n\right\}$ 是线性收敛的.

> **牛顿迭代法** (切线法, 式(8.16)) <br>将非线性方程在根邻近线性化, 得迭代公式 $$x_{n+1}=x_n-\frac{f\left(x_n\right)}{f'\left(x_n\right)}.$$ **定理 8.5** (牛顿法的局部收敛性) 指出: 当 $f'\left(x^{*}\right)\ne0$ (即 $x^{*}$ 为单根) 时, 牛顿法在 $x^{*}$ 邻近至少二阶收敛; 当 $x^{*}$ 为 $r$ 重根时牛顿法退化为线性收敛, 其改进格式为 $$x_{n+1}=x_n-r\frac{f\left(x_n\right)}{f'\left(x_n\right)}\qquad\left(n=0,1,2,\dots\right)$$ (式(8.17)) , 至少二阶收敛.

> **弦截法** (割线法, 式(8.19)) <br>用差商代替导数, 得两步迭代公式 $$x_{n+1}=x_n-\frac{f\left(x_n\right)\left(x_n-x_{n-1}\right)}{f\left(x_n\right)-f\left(x_{n-1}\right)}\qquad\left(n=1,2,\dots\right).$$

### 习题一 (习题 8-3)

用简单迭代法求下列方程的根, 要求 $\left|x_{n+1}-x_n\right|<10^{-5}$: (1) $x-\cos x=0$; (2) $4x-e^{-x}=0$; (3) $x^{3}-2x-5=0$.

### 解答 习题一 (1) 将方程改写为等价形式 $x=\cos x$, 取迭代函数 $\varphi\left(x\right)=\cos x$. 当 $x\in\left[0,1\right]$ 时, $\varphi\left(x\right)=\cos x\in\left[\cos1,1\right]\subset\left[0,1\right]$, 且 $\left|\varphi'\left(x\right)\right|=\left|-\sin x\right|\le\sin1\approx0.841<1$. 由**定理 8.2** (不动点迭代法的收敛条件) , 迭代 $x_{n+1}=\cos x_n$ 收敛. 取 $x_0=0.5$, 迭代得

$$
x_1=0.87758,\ x_2=0.63901,\ x_3=0.80269,\ \dots,\ x_{27}=0.73909,\ x_{28}=0.73908,
$$

此时 $\left|x_{28}-x_{27}\right|=8.25\times10^{-6}<10^{-5}$, 故 $x^{*}\approx0.73908$. (2) 将方程改写为 $x=\frac{1}{4}e^{-x}$, 取迭代函数 $\varphi\left(x\right)=\frac{1}{4}e^{-x}$. 在 $\left[0,1\right]$ 上 $\varphi\left(x\right)\in\left[\frac{e^{-1}}{4},\frac{1}{4}\right]\subset\left[0,1\right]$, 且 $\left|\varphi'\left(x\right)\right|=\frac{1}{4}e^{-x}\le\frac{1}{4}=0.25<1$. 由**定理 8.2**, 迭代收敛. 取 $x_0=0.25$, 迭代得

$$
x_1=0.19470,\ x_2=0.20577,\ x_3=0.20350,\ x_4=0.20397,\ x_5=0.20387,\ x_6=0.20389,\ x_7=0.20389,
$$

此时 $\left|x_7-x_6\right|=3.91\times10^{-6}<10^{-5}$, 故 $x^{*}\approx0.20389$. (3) 将方程改写为 $x=\sqrt\left[3\right]{2x+5}$, 取迭代函数 $\varphi\left(x\right)=\left(2x+5\right)^{1/3}$. 因 $f\left(2\right)=-1<0$, $f\left(2.5\right)>0$, 取有根区间 $\left[2,2.5\right]$; 其上 $\varphi\left(x\right)\in\left[\sqrt\left[3\right]{9},\sqrt\left[3\right]{10}\right]\subset\left[2,2.5\right]$, 且

$$
\left|\varphi'\left(x\right)\right|=\frac{2}{3\left(2x+5\right)^{2/3}}\le\frac{2}{3\cdot9^{2/3}}\approx0.154<1.
$$

由**定理 8.2**, 迭代收敛. 取 $x_0=2$, 迭代得

$$
x_1=2.08008,\ x_2=2.09235,\ x_3=2.09422,\ x_4=2.09450,\ x_5=2.09454,\ x_6=2.09455,
$$

此时 $\left|x_6-x_5\right|=6.55\times10^{-6}<10^{-5}$, 故 $x^{*}\approx2.09455$. $\blacksquare$

### 习题二 (习题 8-7)

设有解方程 $12-3x+2\cos x=0$ 的迭代法

$$
x_{n+1}=4+\frac{2}{3}\cos x_n.
$$ (1) 证明对 $\forall x_0\in\mathbf{R}$, 此迭代法均收敛到方程的根; (2) 取 $x_0=4$, 用此迭代法求方程根的近似值, 使其误差不超过 $\frac{1}{2}\times10^{-5}$; (3) 此迭代法的收敛阶是多少? 说明理由.

### 解答 习题二

迭代函数为 $\varphi\left(x\right)=4+\frac{2}{3}\cos x$. (1) 对任意 $x\in\mathbf{R}$, $\cos x\in\left[-1,1\right]$, 故 $\varphi\left(x\right)\in\left[4-\frac{2}{3},4+\frac{2}{3}\right]=\left[\frac{10}{3},\frac{14}{3}\right]$, 即 $\varphi$ 把 $\mathbf{R}$ 映入闭区间 $\left[\frac{10}{3},\frac{14}{3}\right]$, 且 $\varphi\left(\left[\frac{10}{3},\frac{14}{3}\right]\right)\subset\left[\frac{10}{3},\frac{14}{3}\right]$. 又 $\varphi'\left(x\right)=-\frac{2}{3}\sin x$, 故对一切 $x$ 都有 $\left|\varphi'\left(x\right)\right|\le\frac{2}{3}<1$. 由**定理 8.2** (不动点迭代法的收敛条件) , 迭代 $x_{n+1}=\varphi\left(x_n\right)$ 在 $\left[\frac{10}{3},\frac{14}{3}\right]$ 上有唯一不动点 $x^{*}$ 且收敛. 对任意 $x_0\in\mathbf{R}$, $x_1=\varphi\left(x_0\right)\in\left[\frac{10}{3},\frac{14}{3}\right]$, 其后各项均收敛于 $x^{*}$. 而 $x^{*}=\varphi\left(x^{*}\right)$ 即 $x^{*}=4+\frac{2}{3}\cos x^{*}$, 亦即 $12-3x^{*}+2\cos x^{*}=0$, 故 $x^{*}$ 就是原方程的根. (2) 由**定理 8.2** 的事后误差估计, $\left|x^{*}-x_n\right|\le\frac{L}{1-L}\left|x_n-x_{n-1}\right|$. 这里压缩率 $L=\frac{2}{3}$, 故

$$
\left|x^{*}-x_n\right|\le\frac{2/3}{1-2/3}\left|x_n-x_{n-1}\right|=2\left|x_n-x_{n-1}\right|.
$$

要使误差不超过 $\frac{1}{2}\times10^{-5}$, 只需 $2\left|x_n-x_{n-1}\right|\le\frac{1}{2}\times10^{-5}$, 即 $\left|x_n-x_{n-1}\right|\le\frac{1}{4}\times10^{-5}$. 取 $x_0=4$, 迭代得

$$
x_1=3.56424,\ x_2=3.39200,\ x_3=3.35412,\ x_4=3.34833,\ x_5=3.34753,\ x_6=3.34742,\ x_7=3.34741,\ x_8=3.34740,
$$

此时 $\left|x_8-x_7\right|=2.04\times10^{-6}$, $2\left|x_8-x_7\right|=4.08\times10^{-6}\le\frac{1}{2}\times10^{-5}$, 故 $x^{*}\approx3.34740$. (3) $\varphi'\left(x\right)=-\frac{2}{3}\sin x$. 由 (2) 知不动点 $x^{*}\approx3.3474$, 此时 $\sin x^{*}\approx-0.2044$, 故

$$
\varphi'\left(x^{*}\right)=-\frac{2}{3}\sin x^{*}\approx0.136\ne0,\qquad 0<\left|\varphi'\left(x^{*}\right)\right|<1.
$$

由**定理 8.4** (迭代法收敛阶与迭代函数导数的关系) , 当 $x^{*}=\varphi\left(x^{*}\right)$ 而 $0<\left|\varphi'\left(x^{*}\right)\right|<1$ 时, 迭代序列是线性收敛的. 故此迭代法为线性 (一阶) 收敛. $\blacksquare$

### 习题三 (习题 8-8)

证明由迭代格式

$$
x_{n+1}=\frac{x_n}{2}+\frac{1}{x_n}\qquad\left(n=0,1,2,\dots\right)
$$

产生的迭代序列 $\left\{x_n\right\}$, 对任意 $x_0>1$ 均收敛到 $\sqrt{2}$, 且是二阶收敛的.

### 解答 习题三

迭代函数为 $\varphi\left(x\right)=\frac{x}{2}+\frac{1}{x}\ \left(x>0\right)$.

先求不动点. 令 $x=\varphi\left(x\right)$, 即 $x=\frac{x}{2}+\frac{1}{x}$, 化简得 $\frac{x}{2}=\frac{1}{x}$, 即 $x^{2}=2$; 正不动点为 $x^{*}=\sqrt{2}$.

再证收敛. 对任意 $x>0$, 由均值不等式

$$
\varphi\left(x\right)=\frac{x}{2}+\frac{1}{x}\ge2\sqrt{\frac{x}{2}\cdot\frac{1}{x}}=\sqrt{2},
$$

等号当且仅当 $\frac{x}{2}=\frac{1}{x}$ 即 $x=\sqrt{2}$ 时成立. 故从任意 $x_0>1$ 出发, $x_1=\varphi\left(x_0\right)\ge\sqrt{2}$. 当 $x_n\ge\sqrt{2}$ 时, $$
\varphi\left(x\right)-x=\frac{x}{2}+\frac{1}{x}-x=\frac{2-x^{2}}{2x}\le0\qquad\left(x\ge\sqrt{2}\right),
$$

即 $x_{n+1}=\varphi\left(x_n\right)\le x_n$. 于是自 $x_1$ 起 $\left\{x_n\right\}$ 单调递减且有下界 $\sqrt{2}$, 由单调有界原理, $\left\{x_n\right\}$ 收敛于某极限 $L\ge\sqrt{2}$. 对 $x_{n+1}=\varphi\left(x_n\right)$ 两边取极限 ($\varphi$ 连续) , 得 $L=\frac{L}{2}+\frac{1}{L}$, 即 $L^{2}=2$, 结合 $L\ge\sqrt{2}$ 得 $L=\sqrt{2}$. 故对任意 $x_0>1$, $x_n\to\sqrt{2}$.

最后考察收敛阶. $\varphi'\left(x\right)=\frac{1}{2}-\frac{1}{x^{2}}$, $\varphi''\left(x\right)=\frac{2}{x^{3}}$, 于是

$$
\varphi'\left(\sqrt{2}\right)=\frac{1}{2}-\frac{1}{2}=0,\qquad \varphi''\left(\sqrt{2}\right)=\frac{2}{\left(\sqrt{2}\right)^{3}}=\frac{1}{\sqrt{2}}\ne0.
$$

由**定理 8.4** (迭代法收敛阶与迭代函数导数的关系) , 因 $\varphi\left(\sqrt{2}\right)=\sqrt{2}$, $\varphi'\left(\sqrt{2}\right)=0$ 而 $\varphi''\left(\sqrt{2}\right)\ne0$, 故迭代序列 $\left\{x_n\right\}$ 在 $\sqrt{2}$ 邻近是二阶 (平方) 收敛的. $\blacksquare$

### 习题四 (习题 8-10)

用牛顿法求解下列方程, 要求 $\left|x_{n+1}-x_n\right|<10^{-6}$: (1) $x-\ln x=2$; (2) $xe^{x}-1=0$; (3) $x+\sin x=1$.

### 解答 习题四

按**牛顿迭代法** (式(8.16)) , $x_{n+1}=x_n-\frac{f\left(x_n\right)}{f'\left(x_n\right)}$. (1) $f\left(x\right)=x-\ln x-2$, $f'\left(x\right)=1-\frac{1}{x}=\frac{x-1}{x}$. 有根区间为 $\left[2,4\right]$ ($f\left(3\right)<0$, $f\left(4\right)>0$) . 牛顿格式为

$$
x_{n+1}=x_n-\frac{x_n-\ln x_n-2}{1-\frac{1}{x_n}}.
$$

取 $x_0=3$, 迭代得 $x_1=3.14792$, $x_2=3.14619$, $x_3=3.14619$, 此时 $\left|x_3-x_2\right|\approx2.2\times10^{-7}<10^{-6}$, 故 $x^{*}\approx3.14619$. (2) $f\left(x\right)=xe^{x}-1$, $f'\left(x\right)=e^{x}\left(1+x\right)$. 牛顿格式为

$$
x_{n+1}=x_n-\frac{x_ne^{x_n}-1}{e^{x_n}\left(1+x_n\right)}.
$$

取 $x_0=0.5$, 迭代得 $x_1=0.57102$, $x_2=0.56716$, $x_3=0.56714$, $x_4=0.56714$, 此时 $\left|x_4-x_3\right|\approx1.2\times10^{-10}<10^{-6}$, 故 $x^{*}\approx0.56714$. (3) $f\left(x\right)=x+\sin x-1$, $f'\left(x\right)=1+\cos x$. 牛顿格式为

$$
x_{n+1}=x_n-\frac{x_n+\sin x_n-1}{1+\cos x_n}.
$$

取 $x_0=0.5$, 迭代得 $x_1=0.51096$, $x_2=0.51097$, $x_3=0.51097$, 此时 $\left|x_3-x_2\right|\approx3.1\times10^{-11}<10^{-6}$, 故 $x^{*}\approx0.51097$. $\blacksquare$

### 习题五 (习题 8-12)

证明方程 $f\left(x\right)=x^{3}-x-1=0$ 在区间 $\left[1,2\right]$ 内仅有一个根. 取 $x_0=1.5$, 用牛顿法求此根, 要求精确到 5 位有效数字, 并说明其收敛阶数为 2.

### 解答 习题五

先证存在唯一性. $f\left(1\right)=1-1-1=-1<0$, $f\left(2\right)=8-2-1=5>0$, 由连续函数介值定理, $f\left(x\right)=0$ 在 $\left(1,2\right)$ 内有根. 又 $f'\left(x\right)=3x^{2}-1$, 在 $\left[1,2\right]$ 上 $f'\left(x\right)\ge3\cdot1^{2}-1=2>0$, 故 $f\left(x\right)$ 在 $\left[1,2\right]$ 上严格单调递增, 因而在 $\left[1,2\right]$ 内仅有一个根.

按**牛顿迭代法** (式(8.16)) , $$
x_{n+1}=x_n-\frac{x_n^{3}-x_n-1}{3x_n^{2}-1}.
$$

取 $x_0=1.5$, 迭代得 $x_1=1.34783$, $x_2=1.32520$, $x_3=1.32472$, $x_4=1.32472$, 此时 $\left|x_4-x_3\right|\approx2.2\times10^{-7}$, 故根 $x^{*}\approx1.3247$ (5 位有效数字) .

再说明收敛阶. 根处 $f'\left(x^{*}\right)=3\left(1.3247\right)^{2}-1\approx4.265\ne0$, 故 $x^{*}$ 是单根. 由**定理 8.5** (牛顿法的局部收敛性) , 当 $f'\left(x^{*}\right)\ne0$ 时牛顿法所产生的序列至少二阶收敛于 $x^{*}$, 故此牛顿迭代的收敛阶数为 2. $\blacksquare$

### 习题六 (习题 8-13)

若 $x^{*}$ 是方程 $f\left(x\right)=0$ 的 $r$ 重根, 即 $f\left(x\right)=\left(x-x^{*}\right)^{r}\varphi\left(x\right)$, 其中 $\varphi\left(x^{*}\right)\ne0$, 试证明: (1) 牛顿法在 $x^{*}$ 邻近是线性收敛的; (2) 改进的牛顿法

$$
x_{n+1}=x_n-r\frac{f\left(x_n\right)}{f'\left(x_n\right)}\qquad\left(n=0,1,2,\dots\right)
$$

是二阶收敛的.

### 解答 习题六

由 $f\left(x\right)=\left(x-x^{*}\right)^{r}\varphi\left(x\right)$, $\varphi\left(x^{*}\right)\ne0$, 求导得

$$
f'\left(x\right)=r\left(x-x^{*}\right)^{r-1}\varphi\left(x\right)+\left(x-x^{*}\right)^{r}\varphi'\left(x\right)
=\left(x-x^{*}\right)^{r-1}\left[r\varphi\left(x\right)+\left(x-x^{*}\right)\varphi'\left(x\right)\right].
$$ (1) 牛顿法迭代函数为 $g\left(x\right)=x-\frac{f\left(x\right)}{f'\left(x\right)}$. 代入上式, $$
g\left(x\right)-x^{*}=\left(x-x^{*}\right)-\frac{\left(x-x^{*}\right)\varphi\left(x\right)}{r\varphi\left(x\right)+\left(x-x^{*}\right)\varphi'\left(x\right)}
=\left(x-x^{*}\right)\cdot\frac{\left(r-1\right)\varphi\left(x\right)+\left(x-x^{*}\right)\varphi'\left(x\right)}{r\varphi\left(x\right)+\left(x-x^{*}\right)\varphi'\left(x\right)}.
$$

于是

$$
\lim_{x\to x^{*}}\frac{g\left(x\right)-x^{*}}{x-x^{*}}
=\frac{\left(r-1\right)\varphi\left(x^{*}\right)}{r\varphi\left(x^{*}\right)}=\frac{r-1}{r}.
$$

对 $r$ 重根 $\left(r\ge2\right)$, $0<\frac{r-1}{r}<1$. 由**定义 8.2** (迭代法的收敛阶) 及**定理 8.4** (迭代法收敛阶与迭代函数导数的关系) , 牛顿法产生的序列在 $x^{*}$ 邻近以比率 $\frac{r-1}{r}$ 线性收敛于 $x^{*}$, 即牛顿法对重根是线性收敛的. (2) 改进牛顿法迭代函数为 $g\left(x\right)=x-r\frac{f\left(x\right)}{f'\left(x\right)}$, 于是

$$
g\left(x\right)-x^{*}=\left(x-x^{*}\right)-\frac{r\left(x-x^{*}\right)\varphi\left(x\right)}{r\varphi\left(x\right)+\left(x-x^{*}\right)\varphi'\left(x\right)}
=\frac{\left(x-x^{*}\right)^{2}\varphi'\left(x\right)}{r\varphi\left(x\right)+\left(x-x^{*}\right)\varphi'\left(x\right)}.
$$

从而

$$
\lim_{x\to x^{*}}\frac{g\left(x\right)-x^{*}}{\left(x-x^{*}\right)^{2}}
=\frac{\varphi'\left(x^{*}\right)}{r\varphi\left(x^{*}\right)}.
$$

该极限为有限常数 (当 $\varphi'\left(x^{*}\right)\ne0$ 时为非零常数) . 由**定义 8.2** (迭代法的收敛阶) , 改进牛顿法产生的序列在 $x^{*}$ 邻近至少二阶收敛于 $x^{*}$. $\blacksquare$

### 习题七 (习题 8-16)

试用割线法求解下列方程, 要求 $\left|x_{n+1}-x_n\right|<10^{-5}$: (1) $x-\ln x=2$; (2) $5x-\cos x-1=0$; (3) $x=3-2^{x}$. (仅做第 (1) 小题) ### 解答 习题七

按**弦截法** (割线法, 式(8.19)) , 迭代格式为

$$
x_{n+1}=x_n-\frac{f\left(x_n\right)\left(x_n-x_{n-1}\right)}{f\left(x_n\right)-f\left(x_{n-1}\right)}.
$$ (仅做 (1)) 取 $f\left(x\right)=x-\ln x-2$. 在有根区间 $\left[3,4\right]$ 上取初值 $x_0=3$, $x_1=4$ ($f\left(3\right)<0$, $f\left(4\right)>0$) , 迭代得

$$
x_2=3.13844,\ x_3=3.14580,\ x_4=3.14619,\ x_5=3.14619,
$$

此时 $\left|x_5-x_4\right|\approx2.3\times10^{-7}<10^{-5}$, 故 $x^{*}\approx3.14619$. $\blacksquare$
