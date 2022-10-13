# 作业 5

> **定义 5.1** (插值问题) <br>已知函数 $f\left(x\right)$ 在区间 $\left[a,b\right]$ 上 $n+1$ 个互异节点 $x_0,x_1,\dots,x_n$ 处的函数值 $y_i=f\left(x_i\right)$, 求一个至多 $n$ 次的多项式 $P_n\left(x\right)$, 使其在给定点处满足插值条件 $P_n\left(x_i\right)=f\left(x_i\right)=y_i\ \left(i=0,1,\dots,n\right)$, $P_n\left(x\right)$ 即称为插值多项式.

> **定理 5.1** (插值余项) <br>设 $x_0,x_1,\dots,x_n$ 是 $\left[a,b\right]$ 上的互异节点, $P_n\left(x\right)$ 是过这组节点的 $n$ 次插值多项式. 如果 $f\left(x\right)$ 在 $\left[a,b\right]$ 上 $n+1$ 次连续可导, 则对 $\left[a,b\right]$ 内任意点 $x$, 插值余项为 $$R_n\left(x\right)=f\left(x\right)-P_n\left(x\right)=\frac{f^{\left(n+1\right)}\left(\xi\right)}{\left(n+1\right)!}\omega_{n+1}\left(x\right),\qquad \xi\in\left(a,b\right),$$ 其中 $\omega_{n+1}\left(x\right)=\prod_{j=0}^{n}\left(x-x_j\right)$.

> **定义 5.3** (拉格朗日插值多项式) <br>称满足 $l_i\left(x_j\right)=\delta_{ij}$ ($i=j$ 时为 $1$, 否则为 $0$) 的 $n$ 次多项式 $$l_i\left(x\right)=\prod_{\substack{j=0\\j\ne i}}^{n}\frac{x-x_j}{x_i-x_j}\qquad\left(i=0,1,\dots,n\right)$$ 为拉格朗日插值基函数, 而 $L_n\left(x\right)=\sum_{i=0}^{n}y_i l_i\left(x\right)$ 称为 $n$ 次拉格朗日插值多项式.

> **定义 5.4** (差商与牛顿插值多项式) <br>称 $f\left[x_i,x_j\right]=\frac{f\left(x_i\right)-f\left(x_j\right)}{x_i-x_j}$ 为 $f\left(x\right)$ 关于点 $x_i,x_j$ 的一阶差商, 并递推地称 $f\left[x_0,x_1,\dots,x_k\right]=\frac{f\left[x_1,\dots,x_k\right]-f\left[x_0,\dots,x_{k-1}\right]}{x_k-x_0}$ 为 $k$ 阶差商. 由此得牛顿插值多项式 $$N_n\left(x\right)=f\left[x_0\right]+\left(x-x_0\right)f\left[x_0,x_1\right]+\left(x-x_0\right)\left(x-x_1\right)f\left[x_0,x_1,x_2\right]+\cdots+\left(x-x_0\right)\cdots\left(x-x_{n-1}\right)f\left[x_0,\dots,x_n\right].$$

> **定义 5.6, 定义 5.7** (向前差分与向后差分) <br>对等距节点 $x_k=x_0+kh$ ($h$ 为步长) , 称 $\Delta f_k=f_{k+1}-f_k$ 为一阶向前差分, 称 $\nabla f_k=f_k-f_{k-1}$ 为一阶向后差分, 高阶差分递推定义. 令 $x=x_0+th$ 得牛顿向前插值公式 $$N_n\left(x_0+th\right)=f_0+t\Delta f_0+\frac{t\left(t-1\right)}{2!}\Delta^2f_0+\cdots+\frac{t\left(t-1\right)\cdots\left(t-n+1\right)}{n!}\Delta^nf_0;$$ 令 $x=x_n+th$ 得牛顿向后插值公式 $$N_n\left(x_n+th\right)=f_n+t\nabla f_n+\frac{t\left(t+1\right)}{2!}\nabla^2f_n+\cdots+\frac{t\left(t+1\right)\cdots\left(t+n-1\right)}{n!}\nabla^nf_n.$$

> **定理 5.2** (分段线性插值余项) <br>如果 $f\left(x\right)$ 在 $\left[a,b\right]$ 上二阶连续可微, 则分段线性插值函数 $p\left(x\right)$ 的余项有估计 $$\left|R\left(x\right)\right|=\left|f\left(x\right)-p\left(x\right)\right|\le\frac{h^2}{8}M,$$ 其中 $h=\max\limits_{i}\left(x_{i+1}-x_i\right)$, $M=\max\limits_{\left[a,b\right]}\left|f''\left(x\right)\right|$.

> **定义 5.9** (埃尔米特插值) <br>给定函数 $f\left(x\right)$ 在互异节点上的函数值 $y_i=f\left(x_i\right)$, 并指定在若干节点 $x_{i_k}$ 上的导数值 $y'_{i_k}=f'\left(x_{i_k}\right)$, 要求一个多项式 $H\left(x\right)$ 同时满足 $H\left(x_i\right)=y_i$ 与 $H'\left(x_{i_k}\right)=y'_{i_k}$, 称为埃尔米特插值多项式.

> **定理 5.5** (埃尔米特插值余项) <br>设共有 $n+1$ 个函数值节点与 $m+1$ 个导数条件 (在节点 $x_{i_0},\dots,x_{i_m}$ 上) , 若 $f\left(x\right)\in C^{n+m+2}\left[a,b\right]$, 则对任意 $x\in\left[a,b\right]$, 有 $$R\left(x\right)=f\left(x\right)-H\left(x\right)=\frac{f^{\left(n+m+2\right)}\left(\xi\right)}{\left(n+m+2\right)!}\omega_{n+1}\left(x\right)\prod_{k=0}^{m}\left(x-x_{i_k}\right),\qquad \xi\in\left(a,b\right).$$

> **定义 5.11** (三次样条插值) <br>已知 $f\left(x\right)$ 在节点 $a=x_0<x_1<\cdots<x_n=b$ 上的值 $y_i=f\left(x_i\right)$, 若 $S\left(x\right)$ 满足 $S\left(x_i\right)=y_i$, 在每个小区间 $\left[x_i,x_{i+1}\right]$ 上是三次多项式, 在 $\left[a,b\right]$ 上二阶连续可微, 则称 $S\left(x\right)$ 为三次样条插值函数. 以 $M_i=S''\left(x_i\right)$ 为参数得三弯矩方程 $$\alpha_j M_{j-1}+2M_j+\beta_j M_{j+1}=C_j\qquad\left(j=1,\dots,n-1\right),$$ 其中 $\alpha_j=\frac{h_{j-1}}{h_{j-1}+h_j}$, $\beta_j=1-\alpha_j$, $C_j=\frac{1}{h_{j-1}+h_j}\left(\frac{y_{j+1}-y_j}{h_j}-\frac{y_j-y_{j-1}}{h_{j-1}}\right)$; 端点边界条件可取给定导数值 $S'\left(a\right)=m_0,\ S'\left(b\right)=m_n$ 或给定二阶导数值 $S''\left(a\right)=M_0,\ S''\left(b\right)=M_n$.

### 习题一 (习题 5-3)

已知函数表如下: $x_i=1,\,3,\,4,\,6$; $f\left(x_i\right)=-7,\,5,\,8,\,14$. 试求其三阶拉格朗日插值多项式, 并以此计算 $f\left(2\right)$ 的近似值.

### 解答 习题一

由**定义 5.3** (拉格朗日插值多项式) , 节点 $x_0=1,\,x_1=3,\,x_2=4,\,x_3=6$ 上的四个拉格朗日插值基函数分别为

$$
l_0\left(x\right)=\frac{\left(x-3\right)\left(x-4\right)\left(x-6\right)}{\left(1-3\right)\left(1-4\right)\left(1-6\right)}=-\frac{\left(x-3\right)\left(x-4\right)\left(x-6\right)}{30},
$$

$$
l_1\left(x\right)=\frac{\left(x-1\right)\left(x-4\right)\left(x-6\right)}{\left(3-1\right)\left(3-4\right)\left(3-6\right)}=\frac{\left(x-1\right)\left(x-4\right)\left(x-6\right)}{6},
$$

$$
l_2\left(x\right)=\frac{\left(x-1\right)\left(x-3\right)\left(x-6\right)}{\left(4-1\right)\left(4-3\right)\left(4-6\right)}=-\frac{\left(x-1\right)\left(x-3\right)\left(x-6\right)}{6},
$$

$$
l_3\left(x\right)=\frac{\left(x-1\right)\left(x-3\right)\left(x-4\right)}{\left(6-1\right)\left(6-3\right)\left(6-4\right)}=\frac{\left(x-1\right)\left(x-3\right)\left(x-4\right)}{30}.
$$

故所求三阶拉格朗日插值多项式为

$$
L_3\left(x\right)=-7l_0\left(x\right)+5l_1\left(x\right)+8l_2\left(x\right)+14l_3\left(x\right).
$$

代入 $x=2$, 各基函数取值为

$$
l_0\left(2\right)=\frac{4}{15},\qquad l_1\left(2\right)=\frac{4}{3},\qquad l_2\left(2\right)=-\frac{2}{3},\qquad l_3\left(2\right)=\frac{1}{15},
$$

于是

$$
L_3\left(2\right)=-7\times\frac{4}{15}+5\times\frac{4}{3}+8\times\left(-\frac{2}{3}\right)+14\times\frac{1}{15}=\frac{2}{5}=0.4.
$$

故 $f\left(2\right)\approx 0.4$. $\blacksquare$

### 习题二 (习题 5-7)

设 $x_0,x_1,\dots,x_n$ 为 $n+1$ 个互异节点, $l_j\left(x\right)\ \left(j=0,1,\dots,n\right)$ 为这组节点上的 $n$ 次拉格朗日插值基函数, 试证: (1) $\sum\limits_{j=0}^{n}\left(x_j-x\right)^k l_j\left(x\right)\equiv 0\ \left(k=1,2,\dots,n\right)$; (2) 设 $P\left(x\right)$ 是任意一个最高次项系数为 $1$ 的 $n+1$ 次多项式, 则 $P\left(x\right)-\sum\limits_{j=0}^{n}P\left(x_j\right)l_j\left(x\right)=\omega_{n+1}\left(x\right)=\prod\limits_{j=0}^{n}\left(x-x_j\right)$.

### 解答 习题二

先说明一个基本事实: 对任意次数不超过 $n$ 的多项式 $q\left(t\right)$, 其在节点 $x_0,\dots,x_n$ 上的拉格朗日插值多项式就是它本身, 即 $q\left(t\right)=\sum_{j=0}^{n}q\left(x_j\right)l_j\left(t\right)$. 这是因为等式两边都是次数不超过 $n$ 的多项式, 且在 $n+1$ 个互异节点 $t=x_i$ 处同值, 由**定义 5.1** (插值问题) 插值多项式的存在唯一性可知二者恒等. (1) 把 $\left(t-x\right)^k$ 看作关于 $t$ 的多项式, 其次数为 $k$. 当 $k=1,2,\dots,n$ 时它不超过 $n$ 次, 由上述基本事实, $$
\left(t-x\right)^k=\sum_{j=0}^{n}\left(x_j-x\right)^k l_j\left(t\right).
$$

两边令 $t=x$, 左端为 $\left(x-x\right)^k=0$ ($k\ge1$) , 故

$$
\sum_{j=0}^{n}\left(x_j-x\right)^k l_j\left(x\right)\equiv 0.
$$ (2) 记 $L\left(x\right)=\sum_{j=0}^{n}P\left(x_j\right)l_j\left(x\right)$, 它是次数不超过 $n$ 的多项式, 且 $L\left(x_i\right)=P\left(x_i\right)$ ($i=0,1,\dots,n$) . 于是 $P\left(x\right)-L\left(x\right)$ 是次数为 $n+1$ (首项系数为 $1$) 的多项式, 且以 $x_0,x_1,\dots,x_n$ 为全部根, 因此

$$
P\left(x\right)-L\left(x\right)=C\prod_{j=0}^{n}\left(x-x_j\right).
$$

比较两边最高次项系数, 左端首项系数为 $1$, 故 $C=1$, 即

$$
P\left(x\right)-\sum_{j=0}^{n}P\left(x_j\right)l_j\left(x\right)=\prod_{j=0}^{n}\left(x-x_j\right)=\omega_{n+1}\left(x\right).\ \blacksquare
$$

### 习题三 (习题 5-8)

已知函数表如下: $x_i=1.615,\,1.634,\,1.702,\,1.828$; $f\left(x_i\right)=2.414\,50,\,2.462\,59,\,2.652\,71,\,3.030\,35$. 试求其三阶牛顿插值多项式, 并以此计算 $f\left(1.682\right)$ 的近似值.

### 解答 习题三

由**定义 5.4** (差商与牛顿插值多项式) , 按差商递推构造差商表. 一阶差商: $$
f\left[x_0,x_1\right]=\frac{2.462\,59-2.414\,50}{1.634-1.615}=2.531\,05,
$$

$$
f\left[x_1,x_2\right]=\frac{2.652\,71-2.462\,59}{1.702-1.634}=2.795\,88,\qquad
f\left[x_2,x_3\right]=\frac{3.030\,35-2.652\,71}{1.828-1.702}=2.997\,14.
$$

二阶差商: $$
f\left[x_0,x_1,x_2\right]=\frac{2.795\,88-2.531\,05}{1.702-1.615}=3.044\,02,
$$

$$
f\left[x_1,x_2,x_3\right]=\frac{2.997\,14-2.795\,88}{1.828-1.634}=1.037\,43.
$$

三阶差商: $$
f\left[x_0,x_1,x_2,x_3\right]=\frac{1.037\,43-3.044\,02}{1.828-1.615}=-9.420\,63.
$$

故三阶牛顿插值多项式为

$$
N_3\left(x\right)=2.414\,50+2.531\,05\left(x-1.615\right)+3.044\,02\left(x-1.615\right)\left(x-1.634\right)-9.420\,63\left(x-1.615\right)\left(x-1.634\right)\left(x-1.702\right).
$$

代入 $x=1.682$, 此时 $x-1.615=0.067$, $x-1.634=0.048$, $x-1.702=-0.020$, 得

$$
\begin{aligned}
N_3\left(1.682\right)&=2.414\,50+2.531\,05\times0.067+3.044\,02\times0.067\times0.048-9.420\,63\times0.067\times0.048\times\left(-0.020\right)\\
&=2.414\,50+0.169\,58+0.009\,79+0.000\,61\\
&=2.594\,48.
\end{aligned}
$$

故 $f\left(1.682\right)\approx 2.594\,48$. $\blacksquare$

### 习题四 (习题 5-10)

已知函数表如下: $x_i=1,\,2,\,3,\,4$; $f\left(x_i\right)=3,\,5,\,9,\,15$. 分别用牛顿向前, 向后插值公式计算 $f\left(1.5\right)$, $f\left(3.7\right)$ 的近似值.

### 解答 习题四

节点等距, 步长 $h=1$. 由**定义 5.6, 定义 5.7** (向前差分与向后差分) , 作差分表: 向前差分 $\Delta f_0=5-3=2$, $\Delta f_1=9-5=4$, $\Delta f_2=15-9=6$, $\Delta^2f_0=4-2=2$, $\Delta^2f_1=6-4=2$, $\Delta^3f_0=0$; 向后差分 $\nabla f_3=6$, $\nabla^2f_3=2$, $\nabla^3f_3=0$.

计算 $f\left(1.5\right)$, 它靠近表头 $x_0=1$, 用牛顿向前插值公式. 令 $x=1.5=x_0+th$, 则 $t=\frac{1.5-1}{1}=0.5$, 故

$$
N_3\left(1.5\right)=f_0+t\Delta f_0+\frac{t\left(t-1\right)}{2!}\Delta^2f_0=3+0.5\times2+\frac{0.5\times\left(-0.5\right)}{2}\times2=3+1-0.25=3.75.
$$

计算 $f\left(3.7\right)$, 它靠近表尾 $x_3=4$, 用牛顿向后插值公式. 令 $x=3.7=x_3+th$, 则 $t=\frac{3.7-4}{1}=-0.3$, 故

$$
N_3\left(3.7\right)=f_3+t\nabla f_3+\frac{t\left(t+1\right)}{2!}\nabla^2f_3=15+\left(-0.3\right)\times6+\frac{\left(-0.3\right)\times0.7}{2}\times2=15-1.8-0.21=12.99.
$$

故 $f\left(1.5\right)\approx 3.75$, $f\left(3.7\right)\approx 12.99$. $\blacksquare$

### 习题五 (习题 5-12)

在 $\left[0,\pi/2\right]$ 上给出 $f\left(x\right)=\sin x$ 的等距节点函数表, 为保证用分段线性插值求非节点处的正弦值时, 其截断误差不超过 $10^{-6}$, 函数表的步长至少应取多大? 若改用分段二次插值求非节点处的正弦值, 步长应取多大? ### 解答 习题五

对 $f\left(x\right)=\sin x$, $f''\left(x\right)=-\sin x$, 在 $\left[0,\pi/2\right]$ 上 $\max\left|f''\left(x\right)\right|=1$.

先看分段线性插值. 由**定理 5.2** (分段线性插值余项) , 截断误差满足

$$
\left|R\left(x\right)\right|\le\frac{h^2}{8}\max\left|f''\left(x\right)\right|=\frac{h^2}{8}.
$$

要求 $\frac{h^2}{8}\le10^{-6}$, 解得

$$
h\le\sqrt{8\times10^{-6}}=2\sqrt{2}\times10^{-3}\approx0.00283.
$$

再看分段二次插值. 此时 $f'''\left(x\right)=-\cos x$, 在 $\left[0,\pi/2\right]$ 上 $\max\left|f'''\left(x\right)\right|=1$. 在相邻三个等距节点 $x_{i-1},x_i,x_{i+1}$ (间距为 $h$) 上作二次插值, 由**定理 5.1** (插值余项) , $$
R\left(x\right)=\frac{f'''\left(\xi\right)}{3!}\left(x-x_{i-1}\right)\left(x-x_i\right)\left(x-x_{i+1}\right).
$$

令 $x=x_i+sh$ ($s\in\left[-1,1\right]$) , 则 $\left(x-x_{i-1}\right)\left(x-x_i\right)\left(x-x_{i+1}\right)=h^3 s\left(s^2-1\right)$, 其在 $\left[-1,1\right]$ 上的最大绝对值为 $\frac{2}{3\sqrt{3}}$ (在 $s=\pm\frac{1}{\sqrt{3}}$ 处取得) . 故

$$
\left|R\left(x\right)\right|\le\frac{1}{6}\times\frac{2}{3\sqrt{3}}h^3=\frac{h^3}{9\sqrt{3}}.
$$

要求 $\frac{h^3}{9\sqrt{3}}\le10^{-6}$, 解得

$$
h\le\sqrt\left[3\right]{9\sqrt{3}\times10^{-6}}\approx0.0250.
$$

因此, 分段线性插值时步长应取 $h\le0.00283$; 分段二次插值时步长应取 $h\le0.0250$. $\blacksquare$

### 习题六 (习题 5-16)

给定函数表: $x_i=0,\,1,\,2$; $f\left(x_i\right)=1,\,2,\,1$; $f'\left(x_i\right)$ 在 $x=0$ 处未给定, 在 $x=1,\,2$ 处分别为 $0,\,-1$. 且已知 $f\left(x\right)$ 在 $\left[0,2\right]$ 上五阶连续可导, 求 $f\left(x\right)$ 的四次埃尔米特插值多项式 $H_4\left(x\right)$, 并写出余项 $f\left(x\right)-H_4\left(x\right)$ 的表示式.

### 解答 习题六

插值条件为 $H\left(0\right)=1$, $H\left(1\right)=2$, $H\left(2\right)=1$, $H'\left(1\right)=0$, $H'\left(2\right)=-1$, 共 $5$ 个条件, 可唯一确定四次多项式. 由**定义 5.9** (埃尔米特插值) , 先用拉格朗日插值求出满足三个函数值条件的二次插值多项式 $P_2\left(x\right)$: $$
P_2\left(x\right)=-x^2+2x+1.
$$

设所求四次埃尔米特插值多项式为

$$
H_4\left(x\right)=P_2\left(x\right)+\left(ax+b\right)\,x\left(x-1\right)\left(x-2\right),
$$

其中后一项在节点 $0,1,2$ 处均为零, 不影响函数值条件. 求导得

$$
H_4'\left(x\right)=-2x+2+a\left(x^3-3x^2+2x\right)+\left(ax+b\right)\left(3x^2-6x+2\right).
$$

代入 $H_4'\left(1\right)=0$: 此时 $x^3-3x^2+2x=0$, $3x^2-6x+2=-1$, 故 $H_4'\left(1\right)=-\left(a+b\right)=0$, 即 $a+b=0$. 代入 $H_4'\left(2\right)=-1$: 此时 $x^3-3x^2+2x=0$, $3x^2-6x+2=2$, 故 $H_4'\left(2\right)=-2+2\left(2a+b\right)=-1$, 即 $2a+b=\frac12$. 联立解得 $a=\frac12$, $b=-\frac12$. 故

$$
H_4\left(x\right)=-x^2+2x+1+\frac12 x\left(x-1\right)^2\left(x-2\right).
$$

这里函数值节点为 $0,1,2$ ($n=2$) , 导数条件加在节点 $1,2$ 上 (共 $m+1=2$ 个, $m=1$) , 由**定理 5.5** (埃尔米特插值余项) , 且 $f\left(x\right)\in C^5\left[0,2\right]$, 余项为

$$
f\left(x\right)-H_4\left(x\right)=\frac{f^{\left(5\right)}\left(\xi\right)}{5!}\,x\left(x-1\right)\left(x-2\right)\,\left(x-1\right)\left(x-2\right)=\frac{f^{\left(5\right)}\left(\xi\right)}{120}\,x\left(x-1\right)^2\left(x-2\right)^2,\qquad \xi\in\left(0,2\right).\ \blacksquare
$$

### 习题七 (习题 5-17)

已知函数表如下: $x_i=0,\,1,\,2,\,3$; $y_i=0,\,0,\,0,\,0$. 边界条件为 (1) $m_0=1,\ m_3=0$; (2) $M_0=1,\ M_3=0$. 分别求三次样条插值函数.

### 解答 习题七

节点等距 $h=1$, 且所有 $y_i=0$. 由**定义 5.11** (三次样条插值) , 三弯矩方程中

$$
\alpha_j=\beta_j=\frac{1}{2},\qquad C_j=\frac{1}{h_{j-1}+h_j}\left(\frac{y_{j+1}-y_j}{h_j}-\frac{y_j-y_{j-1}}{h_{j-1}}\right)=0.
$$

**(1) 边界条件 $m_0=S'\left(0\right)=1$, $m_3=S'\left(3\right)=0$** (给定两端导数值) . 由端点导数条件得补充方程

$$
2M_0+M_1=6\left(\frac{y_1-y_0}{h_0}-m_0\right)=-6,\qquad M_2+2M_3=6\left(m_3-\frac{y_3-y_2}{h_2}\right)=0.
$$

与内部方程

$$
\frac12 M_0+2M_1+\frac12 M_2=0,\qquad \frac12 M_1+2M_2+\frac12 M_3=0
$$

联立, 解得 $M_0=-\frac{52}{15}$, $M_1=\frac{14}{15}$, $M_2=-\frac{4}{15}$, $M_3=\frac{2}{15}$. 由三次样条的分段表达式 (取 $h=1$, $y_i=0$) $$
S_j\left(x\right)=\frac{M_j}{6}\left(x_{j+1}-x\right)^3+\frac{M_{j+1}}{6}\left(x-x_j\right)^3-\frac{M_j}{6}\left(x_{j+1}-x\right)-\frac{M_{j+1}}{6}\left(x-x_j\right),
$$

化简得

$$
S_0\left(x\right)=\frac{x\left(1-x\right)\left(15-11x\right)}{15},\qquad x\in\left[0,1\right],
$$

$$
S_1\left(x\right)=\frac{\left(x-1\right)\left(2-x\right)\left(3x-7\right)}{15},\qquad x\in\left[1,2\right],
$$

$$
S_2\left(x\right)=\frac{\left(x-2\right)\left(3-x\right)^2}{15},\qquad x\in\left[2,3\right].
$$

**(2) 边界条件 $M_0=S''\left(0\right)=1$, $M_3=S''\left(3\right)=0$** (给定两端二阶导数值) . 代入内部方程

$$
\frac12 M_0+2M_1+\frac12 M_2=0,\qquad \frac12 M_1+2M_2+\frac12 M_3=0,
$$

解得 $M_1=-\frac{4}{15}$, $M_2=\frac{1}{15}$. 同理化简得分段表达式

$$
S_0\left(x\right)=\frac{x\left(1-x\right)\left(19x-26\right)}{90},\qquad x\in\left[0,1\right],
$$

$$
S_1\left(x\right)=\frac{\left(x-1\right)\left(2-x\right)\left(12-5x\right)}{90},\qquad x\in\left[1,2\right],
$$

$$
S_2\left(x\right)=\frac{\left(x-2\right)\left(3-x\right)\left(x-4\right)}{90},\qquad x\in\left[2,3\right].\ \blacksquare
$$
