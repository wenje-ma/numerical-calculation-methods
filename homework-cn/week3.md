# week3

> **定义 3.3 (谱半径)**
> 
> $\rho\left(A\right)=\max\left|\lambda_i\right|$.

> **定义 3.4 (对角占优矩阵)**
> 
> $\left|a_{ii}\right|\ge\sum_{j\ne i}\left|a_{ij}\right|$.

> **定理 3.6 (迭代法收敛的充要条件)**
> 
> $\rho\left(M\right)< 1$.
## 习题 3-3

用雅可比和高斯-赛德尔迭代法求解方程组, 初值零, 迭代 4 次.

### 解答 习题 3-3

雅可比收敛于 $\left(-3,3,1\right)^\top$, 高斯-赛德尔发散. $\blacksquare$

## 习题 3-5

讨论雅可比迭代法收敛时实数 $a$ 的范围.

### 解答 习题 3-5

$\rho\left(B\right)=\left|2/a\right|$, 收敛当 $\left|a\right|> 2$. $\blacksquare$

## 习题 3-7

写出三种迭代法公式并判断收敛性.

### 解答 习题 3-7

$A$ 对称正定, $0< \omega=1.35< 2$, 高斯-赛德尔与 SOR 收敛, 雅可比发散. $\blacksquare$

## 习题 3-8

写出收敛的迭代式.

### 解答 习题 3-8

交换行次序得严格对角占优矩阵. $\blacksquare$
