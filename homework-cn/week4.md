# week4

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

## 1-12

试改变下列表达式, 使计算结果比较精确: (1) $\frac{1}{1+2x}-\frac{1-x}{1+x}$, $\left|x\right|\ll1$; (2) $\sqrt{x+\frac{1}{x}}-\sqrt{x-\frac{1}{x}}$, $\left|x\right|\gg1$; (3) $\frac{\tan{x}-\sin{x}}{x^{2}}$, $\left|x\right|\ll1$ 且 $x\ne0$. (仅要求第 (1) 小题)

### 解答 1-12

由避免两个相近的数相减, 当 $\left|x\right|\ll1$ 时, $\frac{1}{1+2x}$ 与 $\frac{1-x}{1+x}$ 都接近 $1$, 直接相减会严重丢失有效数字. 对表达式通分合并:

$$
\frac{1}{1+2x}-\frac{1-x}{1+x}=\frac{\left(1+x\right)-\left(1-x\right)\left(1+2x\right)}{\left(1+2x\right)\left(1+x\right)}.
$$

而

$$
\left(1-x\right)\left(1+2x\right)=1+2x-x-2x^{2}=1+x-2x^{2},
$$

$$
\left(1+x\right)-\left(1-x\right)\left(1+2x\right)=\left(1+x\right)-\left(1+x-2x^{2}\right)=2x^{2},
$$

故

$$
\frac{1}{1+2x}-\frac{1-x}{1+x}=\frac{2x^{2}}{\left(1+2x\right)\left(1+x\right)}.
$$

当 $\left|x\right|\ll1$ 时, $\left(1+2x\right)\left(1+x\right)$ 接近 $1$, 改写后的分母不涉及相近数相减, 分子 $2x^{2}$ 很小, 从而避免了有效数字的丢失. 故应改用 $\frac{2x^{2}}{\left(1+2x\right)\left(1+x\right)}$ 计算. $\blacksquare$
