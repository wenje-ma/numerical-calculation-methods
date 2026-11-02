# week5

> **定义 5.1 (插值问题)**
> 
> $P_n\left(x_i\right)=y_i$.

> **定理 5.1 (插值余项)**
> 
> $R_n=f^{\left(n+1\right)}\left(\xi\right)\omega_{n+1}\left(x\right)/\left(n+1\right)!$.

> **定理 5.2 (分段线性插值余项)**
> 
> $\left|R\right|\le h^2M/8$.

> **定义 5.3 (拉格朗日插值多项式)**
> 
> $l_i\left(x\right)=\prod_{j\ne i}\left(x-x_j\right)/\left(x_i-x_j\right)$.

> **定义 5.4 (差商与牛顿插值多项式)**
> 
> $N_n\left(x\right)=\sum f\left[x_0,\cdots,x_k\right]\prod\left(x-x_j\right)$.

> **定理 5.5 (埃尔米特插值余项)**
> 
> $R=f^{\left(n+m+2\right)}\left(\xi\right)\omega_{n+1}\prod\left(x-x_{i_k}\right)/\left(n+m+2\right)!$.

> **定义 5.9 (埃尔米特插值)**
> 
> 同时插值函数值与导数值.

> **定义 5.11 (三次样条插值)**
> 
> $C^2$ 分段三次多项式.
---

## 习题 5-3

求三阶拉格朗日插值多项式并计算 $f\left(2\right)$.

### 解答 习题 5-3

$f\left(2\right)\approx0.4$. $\blacksquare$

---

## 习题 5-7

证明拉格朗日基函数恒等式.

### 解答 习题 5-7

利用插值多项式唯一性. $\blacksquare$

---

## 习题 5-8

求三阶牛顿插值多项式并计算 $f\left(1.682\right)$.

### 解答 习题 5-8

$f\left(1.682\right)\approx2.59448$. $\blacksquare$

---

## 习题 5-10

用向前/向后差分计算 $f\left(1.5\right)$, $f\left(3.7\right)$.

### 解答 习题 5-10

$f\left(1.5\right)\approx3.75$, $f\left(3.7\right)\approx12.99$. $\blacksquare$

---

## 习题 5-12

求步长使截断误差不超过 $10^{-6}$.

### 解答 习题 5-12

线性 $h\le0.00283$, 二次 $h\le0.0250$. $\blacksquare$

---

## 习题 5-16

求四次埃尔米特插值多项式.

### 解答 习题 5-16

$H_4\left(x\right)=-x^2+2x+1+\frac12x\left(x-1\right)^2\left(x-2\right)$. $\blacksquare$

---

## 习题 5-17

求三次样条插值函数.

### 解答 习题 5-17

两种边界条件分别给出分段三次表达式. $\blacksquare$
