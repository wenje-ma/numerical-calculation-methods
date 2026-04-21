# week8

> **定义 6.2 (正交函数系)**
> 
> $\left(\varphi_j,\varphi_k\right)=0$ ($j\ne{k}$).

> **定义 6.3 (最佳平方逼近函数)**
> 
> 使 $\int{w}\left(f-p\right)^2\mathrm{d}x$ 最小.

> **定义 7.1 (代数精确度)**
> 
> 对所有 $m$ 次多项式精确, 对 $m+1$ 次不精确.

> **定义 7.2 (高斯点与高斯型求积公式)**
> 
> $2n-1$ 次代数精确度.

> **定理 7.2 (梯形公式的误差)**
> 
> $R_1=-\left(b-a\right)^3f''\left(\xi\right)/12$.

> **定理 7.3 (辛普森公式的误差)**
> 
> $R_2=-\left(b-a\right)^5f^{\left(4\right)}\left(\xi\right)/2880$.

> **定理 7.4 (高斯点与正交多项式的关系)**
> 
> $w_n$ 与 $\deg\le{n}-1$ 多项式正交.

## 习题 6-7

求 $y=t/\left(at+b\right)$ 型经验公式.

### 解答 习题 6-7

$y=t/\left(0.07891t+0.16486\right)$.

$\blacksquare$

## 习题 6-10

证明格拉姆行列式非零等价于线性无关.

### 解答 习题 6-10

利用二次型正定性.

$\blacksquare$

## 习题 6-13(2)

求 $e^x$ 在 $\left[0,1\right]$ 上一次最佳平方逼近.

### 解答 习题 6-13(2)

$p\left(x\right)=0.8731+1.6903x$.

$\blacksquare$

## 习题 6-15

用勒让德多项式求 $\sin{x}$ 在 $\left[-\pi/2,\pi/2\right]$ 上三次最佳平方逼近.

### 解答 习题 6-15

$P_3\left(x\right)\approx0.9888x-0.1451x^3$, 均方误差 $\approx2.42\times10^{-5}$.

$\blacksquare$

## 习题 7-3

用二点和三点公式计算 $f'\left(0.5\right)$.

### 解答 习题 7-3

二点 $-0.5382$, 三点 $-0.5979$.

$\blacksquare$
