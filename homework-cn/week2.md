# week2

> **定义 1.1 (绝对误差与误差限)**
> 
> 设 $x^{*}$ 为准确值 $x$ 的一个近似值, 称 $e\left(x^{*}\right)=x-x^{*}$ 为近似值 $x^{*}$ 的绝对误差, 简称误差. 若存在正数 $\varepsilon$ 使得 $\left|e\left(x^{*}\right)\right|=\left|x-x^{*}\right|\le\varepsilon$, 则称 $\varepsilon$ 为近似值 $x^{*}$ 的绝对误差限, 简称误差限.

> **定理 1.1 (相对误差限与有效数字的关系)**
> 
> 若 $x$ 的近似值 $x^{*}=\pm0.a_1a_2\cdots{a}_n\times10^{m}\left(a_1\ne0\right)$ 有 $n$ 位有效数字, 则 $\frac{1}{2a_1}\times10^{-n+1}$ 为其相对误差限. 反之, 若 $x^{*}$ 的相对误差限 $\varepsilon_r$ 满足 $\varepsilon_r\le\frac{1}{2}\times10^{-n}$, 则 $x^{*}$ 至少具有 $n$ 位有效数字.

> **定义 1.2 (相对误差与相对误差限)**
> 
> 设 $x^{*}$ 为准确值 $x$ 的近似值, 称 $e_r\left(x^{*}\right)=\frac{e\left(x^{*}\right)}{x^{*}}$ 为近似值 $x^{*}$ 的相对误差. 若存在正数 $\varepsilon_r$ 使得 $\left|e_r\left(x^{*}\right)\right|\le\varepsilon_r$, 则称 $\varepsilon_r$ 为 $x^{*}$ 的相对误差限.

> **定义 1.3 (有效数字)**
> 
> 如果近似值 $x^{*}$ 的规格化形式为 $x^{*}=\pm0.a_1a_2\cdots{a}_n\cdots\times10^{m}$, 其中 $m$ 为整数, $a_1\ne0$, 且 $\left|x-x^{*}\right|\le\frac{1}{2}\times10^{m-n}$, 则称近似值 $x^{*}$ 有 $n$ 位有效数字.

## 1-7

正方形的边长约 $100$ 厘米, 问测量边长时误差应多大, 才能保证面积的误差不超过 $1$ 厘米$^{2}$?

### 解答 1-7

设正方形边长为 $a\approx100$ 厘米, 面积为 $S=a^{2}$. 由误差在基本运算中的传播, 面积的绝对误差满足

$$
\left|e\left(S\right)\right|\approx\left|S'\left(a\right)\right|\cdot\left|e\left(a\right)\right|=2a\left|e\left(a\right)\right|=200\left|e\left(a\right)\right|.
$$

要保证面积的误差不超过 $1$ 厘米$^{2}$, 即 $\left|e\left(S\right)\right|\le1$, 只需

$$
200\left|e\left(a\right)\right|\le1\,\Rightarrow\,\left|e\left(a\right)\right|\le\frac{1}{200}=0.005.
$$

故测量边长时, 边长误差的误差限应不超过 $0.005$ 厘米. $\blacksquare$

## 1-9

设 $s=\frac{1}{2}gt^{2}$, 假定 $g$ 是准确的, 而对 $t$ 的测量有 $\pm0.1$ 秒的误差, 试证当 $t$ 增大时, $s$ 的绝对误差增大而相对误差却减小.

### 解答 1-9

由误差在基本运算中的传播, $s=\frac{1}{2}gt^{2}$, 因 $g$ 准确即 $e\left(g\right)=0$, 故 $s$ 的绝对误差近似为

$$
\left|e\left(s\right)\right|\approx\left|\frac{\partial{s}}{\partial{t}}\right|\left|e\left(t\right)\right|=gt\left|e\left(t\right)\right|=0.1gt.
$$

当 $t$ 增大时, $0.1gt$ 增大, 故 $s$ 的绝对误差增大.

又由误差在基本运算中的传播, 对 $\ln{s}=\ln\frac{g}{2}+2\ln{t}$, 有

$$
\left|e_r\left(s\right)\right|\approx\left|2\frac{e\left(t\right)}{t}\right|=\frac{2\times0.1}{t}=\frac{0.2}{t}.
$$

当 $t$ 增大时, $\frac{0.2}{t}$ 减小, 故 $s$ 的相对误差减小. 综上, 当 $t$ 增大时, $s$ 的绝对误差增大而相对误差减小. $\blacksquare$
