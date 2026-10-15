# 作业 7

> **定义 7.1** (代数精确度) <br>若当 $f\left(x\right)$ 为任意次数不高于 $m$ 的多项式时, 求积公式 $\int_a^b f\left(x\right)dx\approx\sum_{k=0}^n A_k f\left(x_k\right)$ 均精确成立, 而对某个 $m+1$ 次多项式公式不精确成立, 则称该求积公式具有 $m$ 次代数精确度.

> **定理 7.2** (梯形公式的误差) <br>若 $f\left(x\right)\in C^{\left(2\right)}\left[a,b\right]$, 则梯形公式的截断误差为 $$R_1\left(f\right)=\int_a^b f\left(x\right)dx-\frac{b-a}{2}\left[f\left(a\right)+f\left(b\right)\right]=-\frac{\left(b-a\right)^3}{12}f''\left(\xi\right),\ \xi\in\left(a,b\right).$$

> **定理 7.3** (辛普森公式的误差) <br>若 $f\left(x\right)\in C^{\left(4\right)}\left[a,b\right]$, 则辛普森公式的截断误差为 $$R_2\left(f\right)=\int_a^b f\left(x\right)dx-\frac{b-a}{6}\left[f\left(a\right)+4f\left(\frac{a+b}{2}\right)+f\left(b\right)\right]=-\frac{\left(b-a\right)^5}{2880}f^{\left(4\right)}\left(\xi\right)=-\frac{h^5}{90}f^{\left(4\right)}\left(\xi\right),\ \xi\in\left(a,b\right),$$ 其中 $h=b-a$.

> **复化梯形公式** (式(7.29), 式(7.30)) <br>将 $\left[a,b\right]$ 分成 $n$ 等份, $h=\frac{b-a}{n}$, 分点 $x_k=a+kh$, 则 $$T_n=\frac{h}{2}\left[f\left(a\right)+f\left(b\right)+2\sum_{k=1}^{n-1}f\left(x_k\right)\right],$$ 截断误差为 $$R_T\left(f\right)=\int_a^b f\left(x\right)dx-T_n=-\frac{b-a}{12}h^2 f''\left(\xi\right),\ \xi\in\left(a,b\right).$$

> **复化辛普森公式** (式(7.31), 式(7.32)) <br>将 $\left[a,b\right]$ 分成 $n=2m$ 等份, 步长 $h=\frac{b-a}{n}$, 则 $$S_n=\frac{h}{3}\left[f\left(a\right)+f\left(b\right)+2\sum_{k=1}^{m-1}f\left(x_{2k}\right)+4\sum_{k=1}^{m}f\left(x_{2k-1}\right)\right],$$ 截断误差为 $$R_S\left(f\right)=\int_a^b f\left(x\right)dx-S_n=-\frac{b-a}{180}h^4 f^{\left(4\right)}\left(\xi\right),\ \xi\in\left(a,b\right).$$

> **二点与三点求导公式** (式(7.9) 至式(7.12)) <br>对步长 $h$ 的等距节点 $x_0,x_1=x_0+h$, 二点公式 $f'\left(x_0\right)\approx\frac{f\left(x_1\right)-f\left(x_0\right)}{h}$, 截断误差 $R_1\left(x_0\right)=-\frac{h}{2}f''\left(\xi\right)$; 对节点 $x_0,x_1,x_2=x_0+2h$, 三点中心公式 $$f'\left(x_1\right)\approx\frac{f\left(x_2\right)-f\left(x_0\right)}{2h},$$ 截断误差 $R_2\left(x_1\right)=-\frac{h^2}{6}f^{\left(3\right)}\left(\xi\right)$.

> **梯形公式的逐次分半算法** (式(7.34)) <br>记 $2^m$ 等分区间的梯形值为 $T_{2^m}$, 则逐次分半递推为 $$T_{2^m}=\frac{1}{2}T_{2^{m-1}}+\frac{b-a}{2^m}\sum_{k=1}^{2^{m-1}}f\left(a+\left(2k-1\right)\frac{b-a}{2^m}\right),$$ 且事后误差估计为 $\left|R\left(f,T_{2^m}\right)\right|\approx\frac{1}{3}\left|T_{2^m}-T_{2^{m-1}}\right|$, 当 $\left|T_{2^m}-T_{2^{m-1}}\right|<3\varepsilon$ 时停止计算.

> **龙贝格求积公式** (式(7.41)) <br>由理查森外推法, $$T_m^{\left(k\right)}=\frac{4^m T_{m-1}^{\left(k+1\right)}-T_{m-1}^{\left(k\right)}}{4^m-1},\ m=1,2,\dots,$$ 第一列 $T_0^{\left(k\right)}$ 为复化梯形值序列, 以后各列依次为辛普森, 柯特斯, 龙贝格值, 精度逐列提高.

> **定义 7.2** (高斯点与高斯型求积公式) <br>若 $n$ 个节点 $x_1,\dots,x_n\in\left[a,b\right]$ 使带权求积公式 $\int_a^b \rho\left(x\right)f\left(x\right)dx\approx\sum_{k=1}^n A_k f\left(x_k\right)$ 具有 $2n-1$ 次代数精确度, 则称这组节点为高斯点, 公式称为带权 $\rho\left(x\right)$ 的高斯型求积公式.

> **定理 7.4** (高斯点与正交多项式的关系) <br>求积公式的节点是高斯点的充要条件是函数 $w_n\left(x\right)=\prod_{k=1}^n\left(x-x_k\right)$ 与任意次数不超过 $n-1$ 的多项式 $p\left(x\right)$ 在 $\left[a,b\right]$ 上关于权函数 $\rho\left(x\right)$ 正交, 即 $$\int_a^b \rho\left(x\right)p\left(x\right)w_n\left(x\right)dx=0.$$

> **高斯-勒让德求积公式** (式(7.57)) <br>区间 $\left[-1,1\right]$ 上以勒让德多项式零点为节点, 权函数 $\rho\left(x\right)=1$ 的高斯型求积公式. 对任意有限区间 $\left[a,b\right]$, 作变换 $x=\frac{b-a}{2}t+\frac{a+b}{2}$, 则 $$\int_a^b f\left(x\right)dx=\frac{b-a}{2}\int_{-1}^1 f\left(\frac{b-a}{2}t+\frac{a+b}{2}\right)dt.$$

> **二重积分的复化求积公式** (式(7.82), 式(7.83)) <br>矩形区域 $D=\left[a,b\right]\times\left[c,d\right]$ 上的二重积分, $x$ 方向 $n$ 等分, $y$ 方向 $m$ 等分, 步长 $h=\frac{b-a}{n}$, $k=\frac{d-c}{m}$, 其复化求积公式为两个方向一维公式的张量乘积. 梯形权重为 $\omega^{\left(t\right)}=\left[\frac12,1,\dots,1,\frac12\right]$, 辛普森权重为 $\omega^{\left(s\right)}=\left[1,4,2,\dots,2,4,1\right]$.

### 习题一 (习题 7-3)

设 $f\left(x\right)=\frac{1}{\left(1+x\right)^2}$, 取步长 $h=0.1$, 分别用二点和三点公式计算 $f'\left(0.5\right)$, 并估计误差.

### 解答 习题一

由**二点与三点求导公式** (式(7.9) 至式(7.12)) , 取节点 $x_0=0.5$, $x_1=0.6$, 先用二点公式求 $f'\left(0.5\right)$: $$
f'\left(0.5\right)\approx\frac{f\left(0.6\right)-f\left(0.5\right)}{0.1}=\frac{\frac{1}{1.6^2}-\frac{1}{1.5^2}}{0.1}=\frac{0.390625-0.444444}{0.1}=-0.538194.
$$

其截断误差为 $R_1\left(x_0\right)=-\frac{h}{2}f''\left(\xi\right)$. 由 $f''\left(x\right)=\frac{6}{\left(1+x\right)^4}$, 在 $\left[0.5,0.6\right]$ 上 $\max\left|f''\left(x\right)\right|=\frac{6}{1.5^4}=1.1852$, 故

$$
\left|R_1\left(0.5\right)\right|\le\frac{0.1}{2}\times1.1852=0.0593.
$$

再取节点 $x_0=0.4$, $x_1=0.5$, $x_2=0.6$, 用三点中心公式: $$
f'\left(0.5\right)\approx\frac{f\left(0.6\right)-f\left(0.4\right)}{2h}=\frac{0.390625-\frac{1}{1.4^2}}{0.2}=\frac{0.390625-0.510204}{0.2}=-0.597895.
$$

其截断误差为 $R_2\left(x_1\right)=-\frac{h^2}{6}f^{\left(3\right)}\left(\xi\right)$. 由 $f^{\left(3\right)}\left(x\right)=-\frac{24}{\left(1+x\right)^5}$, 在 $\left[0.4,0.6\right]$ 上 $\max\left|f^{\left(3\right)}\left(x\right)\right|=\frac{24}{1.4^5}=4.4631$, 故

$$
\left|R_2\left(0.5\right)\right|\le\frac{0.1^2}{6}\times4.4631=0.00744.
$$

准确值 $f'\left(0.5\right)=-\frac{2}{1.5^3}=-0.592593$, 二点公式误差约 $0.0544$, 三点公式误差约 $0.0053$, 与截断误差估计一致, 三点公式精度明显高于二点公式. $\blacksquare$

### 习题二 (习题 7-4)

分别用梯形公式和辛普森公式计算下列积分的近似值并估计误差: (1) $\int_0^1 e^{-x}dx$; (2) $\int_{0.1}^{0.5} e^{\frac{1}{x}}dx$. (仅要求第 (2) 小题) ### 解答 习题二

这里 $a=0.1$, $b=0.5$, $f\left(x\right)=e^{1/x}$. 由**定理 7.2** (梯形公式的误差) , 梯形公式为

$$
\int_{0.1}^{0.5} e^{1/x}dx\approx\frac{0.5-0.1}{2}\left[e^{10}+e^2\right]=0.2\left[22026.4658+7.3891\right]=4406.77.
$$

由**定理 7.3** (辛普森公式的误差) , 中点为 $\frac{0.1+0.5}{2}=0.3$, $e^{1/0.3}=28.0317$, 故

$$
\int_{0.1}^{0.5} e^{1/x}dx\approx\frac{0.4}{6}\left[e^{10}+4e^{1/0.3}+e^2\right]=\frac{0.4}{6}\left[22026.4658+112.1268+7.3891\right]=1476.40.
$$

估计截断误差. 对 $f\left(x\right)=e^{1/x}$, 求得

$$
f''\left(x\right)=e^{1/x}\left(\frac{1}{x^4}+\frac{2}{x^3}\right),\quad f^{\left(4\right)}\left(x\right)=e^{1/x}\left(\frac{1}{x^8}+\frac{12}{x^7}+\frac{36}{x^6}+\frac{24}{x^5}\right).
$$

二者在 $\left[0.1,0.5\right]$ 上均在 $x=0.1$ 处取最大值, $\max\left|f''\left(x\right)\right|=2.643\times10^8$, $\max\left|f^{\left(4\right)}\left(x\right)\right|=5.692\times10^{12}$. 由**定理 7.2**, **定理 7.3**, $$
\left|R_T\right|\le\frac{\left(0.4\right)^3}{12}\times2.643\times10^8=1.41\times10^6,
$$

$$
\left|R_S\right|\le\frac{\left(0.4\right)^5}{2880}\times5.692\times10^{12}=2.02\times10^7.
$$

由于被积函数在 $x=0.1$ 附近变化极为剧烈, 低阶梯形公式与辛普森公式的截断误差都很大, 近似值与积分准确值 (约 $288.3$) 相差甚远, 这说明对剧烈变化的函数不宜直接使用低阶求积公式. $\blacksquare$

### 习题三 (习题 7-8)

求近似公式

$$
\int_0^1 f\left(x\right)dx\approx\frac{1}{3}\left[2f\left(\frac14\right)-f\left(\frac12\right)+2f\left(\frac34\right)\right]
$$

的代数精确度.

### 解答 习题三

由**定义 7.1** (代数精确度) , 依次用 $f\left(x\right)=1,x,x^2,x^3,x^4$ 检验.

当 $f\left(x\right)=1$ 时, 左端 $=1$, 右端 $=\frac13\left(2-1+2\right)=1$, 精确成立; 当 $f\left(x\right)=x$ 时, 左端 $=\frac12$, 右端 $=\frac13\left(2\cdot\frac14-\frac12+2\cdot\frac34\right)=\frac13\cdot\frac32=\frac12$, 精确成立; 当 $f\left(x\right)=x^2$ 时, 左端 $=\frac13$, 右端 $=\frac13\left(2\cdot\frac1{16}-\frac14+2\cdot\frac9{16}\right)=\frac13\cdot1=\frac13$, 精确成立; 当 $f\left(x\right)=x^3$ 时, 左端 $=\frac14$, 右端 $=\frac13\left(2\cdot\frac1{64}-\frac18+2\cdot\frac{27}{64}\right)=\frac13\cdot\frac34=\frac14$, 精确成立; 当 $f\left(x\right)=x^4$ 时, 左端 $=\frac15=0.2$, 右端 $=\frac13\left(2\cdot\frac1{256}-\frac1{16}+2\cdot\frac{81}{256}\right)=\frac{37}{192}\approx0.19271$, 不精确成立.

故该求积公式对 $f\left(x\right)=1,x,x^2,x^3$ 均精确成立, 而对 $x^4$ 不精确成立, 由**定义 7.1**, 它具有 $3$ 次代数精确度. $\blacksquare$

### 习题四 (习题 7-10)

分别用复化梯形公式和复化辛普森公式计算下列积分的近似值: (1) $\int_0^1 \frac{x}{1+x^2}dx,\ n=8$; (2) $\int_0^1 \frac{\ln\left(1+x\right)}{\left(1+x\right)^2}dx,\ n=4$. (仅要求第 (1) 小题) ### 解答 习题四

这里 $a=0$, $b=1$, $n=8$, 步长 $h=\frac18=0.125$, 分点 $x_k=0.125k\ \left(k=0,1,\dots,8\right)$, 被积函数 $f\left(x\right)=\frac{x}{1+x^2}$.

由**复化梯形公式** (式(7.29)) , $$
T_8=\frac{0.125}{2}\left[f\left(0\right)+f\left(1\right)+2\sum_{k=1}^{7}f\left(0.125k\right)\right]=0.34527.
$$

由**复化辛普森公式** (式(7.31)) , $$
S_8=\frac{0.125}{3}\left[f\left(0\right)+f\left(1\right)+2\sum_{k=1}^{3}f\left(0.25k\right)+4\sum_{k=1}^{4}f\left(0.125\left(2k-1\right)\right)\right]=0.34658.
$$

积分准确值为 $\int_0^1\frac{x}{1+x^2}dx=\frac12\ln 2=0.34657$, 复化辛普森公式 $S_8=0.34658$ 比复化梯形公式 $T_8=0.34527$ 更接近准确值. $\blacksquare$

### 习题五 (习题 7-11)

若用复化梯形公式计算积分 $\int_0^1 e^{-x^2}dx$, 问积分区间要等分为多少份才能保证计算结果有四位有效数字 (假定计算过程无舍入误差) ? 若用复化辛普森公式计算, 积分区间应等分为多少份? ### 解答 习题五

积分值 $I=\int_0^1 e^{-x^2}dx\approx0.7468$, $0<I<1$, 四位有效数字要求截断误差不超过 $\frac12\times10^{-4}$.

先求各阶导数的界. $f\left(x\right)=e^{-x^2}$, $$
f''\left(x\right)=\left(4x^2-2\right)e^{-x^2},\quad f^{\left(4\right)}\left(x\right)=\left(12-48x^2+16x^4\right)e^{-x^2}.
$$

在 $\left[0,1\right]$ 上 $\max\left|f''\left(x\right)\right|=2$ (在 $x=0$ 处) , $\max\left|f^{\left(4\right)}\left(x\right)\right|=12$ (在 $x=0$ 处) .

用复化梯形公式时, 由**复化梯形公式** (式(7.30)) 的误差, $$
\left|R_T\right|=\frac{1}{12}h^2\cdot2=\frac{h^2}{6}\le\frac12\times10^{-4},
$$

解得 $h^2\le3\times10^{-4}$, $h\le0.01732$, 故 $n=\frac{1}{h}\ge57.7$, 即应等分为 $n=58$ 份.

用复化辛普森公式时, 由**复化辛普森公式** (式(7.32)) 的误差, $$
\left|R_S\right|=\frac{1}{180}h^4\cdot12=\frac{h^4}{15}\le\frac12\times10^{-4},
$$

解得 $h^4\le7.5\times10^{-4}$, $h\le0.1655$, 故 $n=\frac{1}{h}\ge6.04$. 因辛普森公式要求 $n$ 为偶数, 应取 $n=8$.

可见达到同样精度, 复化辛普森公式所需等分数远少于复化梯形公式. $\blacksquare$

### 习题六 (习题 7-12)

根据函数表

| $i$ | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
|---|---|---|---|---|---|---|---|---|---|
| $x_i$ | 0 | 0.125 | 0.25 | 0.375 | 0.5 | 0.625 | 0.75 | 0.875 | 1 |
| $f\left(x_i\right)$ | 1 | 0.997398 | 0.989616 | 0.976727 | 0.958851 | 0.936156 | 0.908852 | 0.877193 | 0.841471 |

计算积分 $I=\int_0^1 f\left(x\right)dx$ 的近似值, 并估计误差.

### 解答 习题六

这里 $n=8$, 步长 $h=0.125$. 由**复化梯形公式** (式(7.29)) , $$
T_8=\frac{0.125}{2}\left[f\left(x_0\right)+f\left(x_8\right)+2\sum_{k=1}^{7}f\left(x_k\right)\right]=0.945691.
$$

由**复化辛普森公式** (式(7.31)) , $$
S_8=\frac{0.125}{3}\left[f\left(x_0\right)+f\left(x_8\right)+2\sum_{k=1}^{3}f\left(x_{2k}\right)+4\sum_{k=1}^{4}f\left(x_{2k-1}\right)\right]=0.946084.
$$

该表对应 $f\left(x\right)=\frac{\sin x}{x}$, 积分准确值 $I=0.9460831$. 比较可知 $S_8=0.946084$ 已有约 $6$ 位有效数字, 而 $T_8=0.945691$ 误差约 $4\times10^{-4}$. 由**复化梯形公式** (式(7.30)) 与**复化辛普森公式** (式(7.32)) , 复化辛普森误差为 $O\left(h^4\right)$, 复化梯形误差为 $O\left(h^2\right)$, 故辛普森公式精度较高. $\blacksquare$

### 习题七 (习题 7-13)

试用梯形公式的逐次分半算法计算下列积分: (1) $\int_0^\pi \frac{dx}{x+\cos x}$; (2) $\int_0^1 \frac{dx}{1+x^3}$.

要求误差不超过 $\varepsilon=3\times10^{-4}$. (仅要求第 (1) 小题) ### 解答 习题七

这里 $a=0$, $b=\pi$, $f\left(x\right)=\frac{1}{x+\cos x}$. 由**梯形公式的逐次分半算法** (式(7.34)) , 首值 $T_1=\frac{\pi}{2}\left[f\left(0\right)+f\left(\pi\right)\right]=2.3043$, 逐次分半计算梯形值序列, 并用事后误差估计 $\left|R\right|\approx\frac13\left|T_{2^m}-T_{2^{m-1}}\right|$ 控制精度, 结果如下: | $2^m$ | $T_{2^m}$ | $\lvert T_{2^m}-T_{2^{m-1}}\rvert$ |
|---|---|---|
| 1 | 2.3043 | -- |
| 2 | 2.1521 | 0.1521 |
| 4 | 2.0786 | 0.0736 |
| 8 | 2.0527 | 0.0258 |
| 16 | 2.0456 | 0.00720 |
| 32 | 2.0437 | 0.00186 |
| 64 | 2.0432 | 0.000470 |

当 $2^m=64$ 时, $\lvert T_{64}-T_{32}\rvert=0.000470<3\varepsilon=9\times10^{-4}$, 由**梯形公式的逐次分半算法**的停步准则, 此时 $\left|R\right|\approx\frac13\times0.000470=1.6\times10^{-4}<3\times10^{-4}$, 满足精度. 故

$$
\int_0^\pi \frac{dx}{x+\cos x}\approx T_{64}=2.0432.
$$

$\blacksquare$

### 习题八 (习题 7-15)

用龙贝格方法计算积分 $I=\int_0^1 e^{-x^2}dx$ 的近似值, 要求误差不超过 $10^{-4}$.

### 解答 习题八

这里 $a=0$, $b=1$, $f\left(x\right)=e^{-x^2}$. 由**龙贝格求积公式** (式(7.41)) , 首列梯形值 $T_1=\frac12\left[f\left(0\right)+f\left(1\right)\right]=0.683940$, 逐次分半并按 $T_m^{\left(k\right)}=\frac{4^m T_{m-1}^{\left(k+1\right)}-T_{m-1}^{\left(k\right)}}{4^m-1}$ 外推, 得计算表: | $k$ | 梯形值 $T_0^{\left(k\right)}$ | 辛普森值 $T_1^{\left(k\right)}$ | 柯特斯值 $T_2^{\left(k\right)}$ | 龙贝格值 $T_3^{\left(k\right)}$ |
|---|---|---|---|---|
| 0 | 0.683940 | | | |
| 1 | 0.731370 | 0.747180 | | |
| 2 | 0.742984 | 0.746855 | 0.746834 | |
| 3 | 0.745866 | 0.746826 | 0.746824 | 0.746824 |

当外推至 $k=3$ 时, 龙贝格值 $T_3^{\left(3\right)}=0.746824$ 与上一行对应值之差已小于 $10^{-4}$, 由**龙贝格求积公式**的停步准则, 满足精度. 故

$$
\int_0^1 e^{-x^2}dx\approx0.7468,
$$

其准确值为 $0.7468241\cdots$. $\blacksquare$

### 习题九 (习题 7-16)

确定下列公式中的节点及求积系数, 使其具有尽可能高的代数精确度: (1) $\int_{-h}^{h}f\left(x\right)dx\approx A_1 f\left(-\frac h2\right)+A_2 f\left(0\right)+A_3 f\left(\frac h2\right)$; (2) $\int_0^2 f\left(x\right)dx\approx f\left(x_1\right)+f\left(x_2\right)$; (3) $\int_{-1}^{1}f\left(x\right)dx\approx A_1 f\left(x_1\right)+A_2 f\left(0\right)+f\left(1\right)$. (仅要求第 (2) 小题) ### 解答 习题九

公式为 $\int_0^2 f\left(x\right)dx\approx f\left(x_1\right)+f\left(x_2\right)$, 两个求积系数已固定为 $1$, 待定节点 $x_1,x_2$. 由**定义 7.1** (代数精确度) , 令公式对 $f\left(x\right)=1,x,x^2$ 精确成立.

当 $f\left(x\right)=1$ 时, 左端 $\int_0^2 1dx=2$, 右端 $=1+1=2$, 自动满足; 当 $f\left(x\right)=x$ 时, 左端 $\int_0^2 xdx=2$, 右端 $=x_1+x_2$, 故

$$
x_1+x_2=2.
$$

当 $f\left(x\right)=x^2$ 时, 左端 $\int_0^2 x^2dx=\frac83$, 右端 $=x_1^2+x_2^2$, 利用 $x_1^2+x_2^2=\left(x_1+x_2\right)^2-2x_1x_2$, 得

$$
4-2x_1x_2=\frac83\ \Rightarrow\ x_1x_2=\frac23.
$$

于是 $x_1,x_2$ 为方程 $t^2-2t+\frac23=0$ 的两根, 解得

$$
x_{1,2}=1\pm\frac{1}{\sqrt3}.
$$

检验 $f\left(x\right)=x^3$: 左端 $\int_0^2 x^3dx=4$, 右端 $=x_1^3+x_2^3=\left(x_1+x_2\right)^3-3x_1x_2\left(x_1+x_2\right)=8-3\cdot\frac23\cdot2=4$, 精确成立; 再检验 $f\left(x\right)=x^4$: 左端 $\int_0^2 x^4dx=\frac{32}{5}=6.4$, 右端 $=x_1^4+x_2^4=\frac{56}{9}\approx6.222$, 不精确成立.

故取 $x_1=1-\frac{1}{\sqrt3}$, $x_2=1+\frac{1}{\sqrt3}$ 时, 公式具有 $3$ 次代数精确度, 达到两节点公式的最高精度 $2n-1=3$. $\blacksquare$

### 习题十 (习题 7-16, 续)

(仅要求第 (3) 小题) $$
\int_{-1}^{1}f\left(x\right)dx\approx A_1 f\left(x_1\right)+A_2 f\left(0\right)+f\left(1\right).
$$

### 解答 习题十

待定 $x_1,A_1,A_2$ 三个量. 由**定义 7.1** (代数精确度) , 令公式对 $f\left(x\right)=1,x,x^2$ 精确成立.

当 $f\left(x\right)=1$ 时, 左端 $\int_{-1}^1 1dx=2$, 故

$$
A_1+A_2+1=2\ \Rightarrow\ A_1+A_2=1.
$$

当 $f\left(x\right)=x$ 时, 左端 $\int_{-1}^1 xdx=0$, 故

$$
A_1 x_1+A_2\cdot0+1\cdot1=0\ \Rightarrow\ A_1 x_1=-1.
$$

当 $f\left(x\right)=x^2$ 时, 左端 $\int_{-1}^1 x^2dx=\frac23$, 故

$$
A_1 x_1^2+A_2\cdot0+1\cdot1=\frac23\ \Rightarrow\ A_1 x_1^2=-\frac13.
$$

联立 $A_1 x_1=-1$ 与 $A_1 x_1^2=-\frac13$, 两式相除得 $x_1=\frac13$, 代回得 $A_1=-3$, 再由 $A_1+A_2=1$ 得 $A_2=4$.

检验 $f\left(x\right)=x^3$: 左端 $\int_{-1}^1 x^3dx=0$, 右端 $=A_1 x_1^3+A_2\cdot0+1=\left(-3\right)\cdot\frac1{27}+1=\frac89\ne0$, 不精确成立.

故取 $x_1=\frac13$, $A_1=-3$, $A_2=4$ 时, 公式具有 $2$ 次代数精确度. $\blacksquare$

### 习题十一 (习题 7-18)

试确定 $x_1,x_2,A_1,A_2$, 使求积公式

$$
\int_0^1 \sqrt{x}\,f\left(x\right)dx\approx A_1 f\left(x_1\right)+A_2 f\left(x_2\right)
$$

为高斯型求积公式.

### 解答 习题十一

由**定义 7.2** (高斯点与高斯型求积公式) , 两节点高斯公式应具有 $2n-1=3$ 次代数精确度. 由**定理 7.4** (高斯点与正交多项式的关系) , 节点多项式 $w_2\left(x\right)=\left(x-x_1\right)\left(x-x_2\right)=x^2+px+q$ 应与 $1,x$ 关于权函数 $\rho\left(x\right)=\sqrt{x}$ 在 $\left[0,1\right]$ 上正交, 即

$$
\int_0^1 \sqrt{x}\left(x^2+px+q\right)dx=0,\quad \int_0^1 x\sqrt{x}\left(x^2+px+q\right)dx=0.
$$

计算得

$$
\frac{2}{7}+\frac{2p}{5}+\frac{2q}{3}=0,\quad \frac{2}{9}+\frac{2p}{7}+\frac{2q}{5}=0.
$$

化简为

$$
\frac17+\frac p5+\frac q3=0,\quad \frac19+\frac p7+\frac q5=0,
$$

解得 $p=-\frac{10}{9}$, $q=\frac{5}{21}$. 于是

$$
w_2\left(x\right)=x^2-\frac{10}{9}x+\frac{5}{21},
$$

其两根为

$$
x_1=\frac{\frac{10}{9}-\sqrt{\left(\frac{10}{9}\right)^2-\frac{20}{21}}}{2}\approx0.28995,\quad x_2\approx0.82116.
$$

再由**定义 7.1**, 令公式对 $f\left(x\right)=1,x$ 精确成立以确定系数: $$
A_1+A_2=\int_0^1\sqrt{x}dx=\frac23,\quad A_1 x_1+A_2 x_2=\int_0^1 x\sqrt{x}dx=\frac25,
$$

解得 $A_1\approx0.27756$, $A_2\approx0.38911$. 此时公式对 $f\left(x\right)=x^2$ 亦精确成立, 具有 $3$ 次代数精确度, 确为高斯型求积公式. $\blacksquare$

### 习题十二 (习题 7-21)

用三点高斯-勒让德求积公式计算积分

$$
I=\int_0^1 \frac{2\sin\left(2x-1\right)}{3-2x}dx.
$$

### 解答 习题十二

由**高斯-勒让德求积公式** (式(7.57)) , 先作区间变换 $x=\frac{t+1}{2}$, 则 $dx=\frac12 dt$, 且 $2x-1=t$, $3-2x=2-t$, 于是

$$
I=\int_{-1}^1 \frac{2\sin t}{2-t}\cdot\frac12 dt=\int_{-1}^1 \frac{\sin t}{2-t}dt.
$$

三点高斯-勒让德节点为 $t=0,\ \pm\sqrt{\frac35}=\pm0.77459667$, 对应求积系数为 $\frac89,\ \frac59,\ \frac59$. 代入得

$$
I\approx\frac59\cdot\frac{\sin\left(-0.7746\right)}{2+0.7746}+\frac89\cdot\frac{\sin0}{2}+\frac59\cdot\frac{\sin\left(0.7746\right)}{2-0.7746}.
$$

计算各项: $\sin\left(\pm0.7746\right)=\pm0.6993$, 故

$$
I\approx\frac59\left[-\frac{0.6993}{2.7746}+\frac{0.6993}{1.2254}\right]=\frac59\left[-0.2520+0.5707\right]=0.17705.
$$

积分准确值约为 $0.17758$, 三点高斯-勒让德公式误差约 $5\times10^{-4}$. $\blacksquare$

### 习题十三 (习题 7-26)

设 $n=m=4$, 试分别用复化梯形公式和复化辛普森计算二重积分, 并将计算结果与精确值作比较: (1) $I=\int_{1.0}^{1.5}dx\int_{1.2}^{1.6}\ln\left(x+2y\right)dy$; (2) $I=\int_0^{0.5}dx\int_1^{1.6}\frac{1}{1+xy}dy$. (仅要求第 (1) 小题) ### 解答 习题十三

积分区域为矩形 $D=\left[1.0,1.5\right]\times\left[1.2,1.6\right]$, $x$ 方向步长 $h_x=\frac{0.5}{4}=0.125$, 节点 $x_i=1.0+0.125i$; $y$ 方向步长 $h_y=\frac{0.4}{4}=0.1$, 节点 $y_j=1.2+0.1j$, 被积函数 $f\left(x,y\right)=\ln\left(x+2y\right)$.

由**二重积分的复化求积公式** (式(7.82)) , 复化梯形公式为两个方向一维梯形公式的张量乘积: $$
T_{4,4}=h_xh_y\sum_{i=0}^4\sum_{j=0}^4\omega_i^{\left(t\right)}\omega_j^{\left(t\right)}f\left(x_i,y_j\right)=0.27923,
$$

其中 $\omega^{\left(t\right)}=\left[\frac12,1,1,1,\frac12\right]$.

由**二重积分的复化求积公式** (式(7.83)) , 复化辛普森公式为

$$
S_{4,4}=\frac{h_xh_y}{9}\sum_{i=0}^4\sum_{j=0}^4\omega_i^{\left(s\right)}\omega_j^{\left(s\right)}f\left(x_i,y_j\right)=0.27929,
$$

其中 $\omega^{\left(s\right)}=\left[1,4,2,4,1\right]$.

积分精确值可先积内层: $\int_{1.2}^{1.6}\ln\left(x+2y\right)dy=\frac12\left.\left(u\ln u-u\right)\right|_{u=x+2.4}^{u=x+3.2}$, 再对 $x$ 积分, 得 $I=0.27929$. 可见复化辛普森结果 $S_{4,4}=0.27929$ 与精确值几乎一致, 复化梯形结果 $T_{4,4}=0.27923$ 误差约 $6\times10^{-5}$. $\blacksquare$

### 习题十四 (习题 7-27)

设 $n=m=4$, 试推导在 $x$ 方向用复化梯形公式, 在 $y$ 方向用复化辛普森公式的计算矩形区域上二重积分的近似求积公式, 并计算 26 题中的积分.

### 解答 习题十四

设矩形区域 $D=\left[a,b\right]\times\left[c,d\right]$, $x$ 方向 $n$ 等分 (步长 $h_x=\frac{b-a}{n}$, 节点 $x_i=a+ih_x$) , $y$ 方向 $m$ 等分 (步长 $h_y=\frac{d-c}{m}$, 节点 $y_j=c+jh_y$) . 由**二重积分的复化求积公式** (式(7.82), 式(7.83)) , 二重积分为两个方向一维求积公式的张量乘积. 若在 $x$ 方向用复化梯形公式 (权重 $\omega^{\left(t\right)}=\left[\frac12,1,\dots,1,\frac12\right]$) , 在 $y$ 方向用复化辛普森公式 (权重 $\omega^{\left(s\right)}=\left[1,4,2,\dots,2,4,1\right]$) , 则混合求积公式为

$$
M_{n,m}=\frac{h_xh_y}{2\cdot3}\sum_{i=0}^n\sum_{j=0}^m\omega_i^{\left(t\right)}\omega_j^{\left(s\right)}f\left(x_i,y_j\right)
=\frac{h_xh_y}{6}\sum_{i=0}^n\sum_{j=0}^m\omega_i^{\left(t\right)}\omega_j^{\left(s\right)}f\left(x_i,y_j\right).
$$

现计算 26 题 (1) 的积分 $I=\int_{1.0}^{1.5}dx\int_{1.2}^{1.6}\ln\left(x+2y\right)dy$, $n=m=4$, $h_x=0.125$, $h_y=0.1$, $\omega^{\left(t\right)}=\left[\frac12,1,1,1,\frac12\right]$, $\omega^{\left(s\right)}=\left[1,4,2,4,1\right]$, 代入得

$$
M_{4,4}=\frac{0.125\times0.1}{6}\sum_{i=0}^4\sum_{j=0}^4\omega_i^{\left(t\right)}\omega_j^{\left(s\right)}\ln\left(x_i+2y_j\right)=0.27927.
$$

该结果介于复化梯形 $T_{4,4}=0.27923$ 与复化辛普森 $S_{4,4}=0.27929$ 之间, 与精确值 $0.27929$ 误差约 $2\times10^{-5}$. $\blacksquare$
