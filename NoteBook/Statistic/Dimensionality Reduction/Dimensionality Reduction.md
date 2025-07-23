---
LINK:
  - "[[Statistic]]"
  - "[[Data Science]]"
  - "[[PCA]]"
---


## Motivation

We consider a $p-dimensional$ distribution with mean $μ$ and $variance-covariance$ matrix $Σ$
我們考慮一個具有均值μ和方差-協方差矩陣Σ的p維分佈

這樣的矩陣有p個正實特征值和p正交特征向量
$$
\Sigma \hat{\mathbf{v}}_i = \lambda_i \hat{\mathbf{v}}_i, \quad \lambda_i \in (0, \infty), \quad \hat{\mathbf{v}}_i \cdot \hat{\mathbf{v}}_j = 
\begin{cases} 
1 & \text{if } i = j, \\
0 & \text{otherwise,}
\end{cases} \quad i, j \in [p]
$$
We will usually order the labels so that $λ1 ≥ λ2 ≥ · · · ≥ λp$. The first of these, $λ1$, is called the dominant eigenvalue 主特征值

### Multivariate normal eigensystem and geometry
#Multivariate_normal_Distribution

p-dimensional multivariate normal has ellipsoidal橢圓體 contours with the length of the i-th axis being proportional to $\sqrt{\lambda_i}$
![](PICTURE/Dimensionality%20Reduction/3a1548fb82caef248d6ee16bfbf4b8b6_MD5.jpeg)

需要應用的技術不需要多元正態性但是數據越接近正態性，效果越好



### 基本方法：
- 如果我們有一個 $n \times p$  的數據矩陣X，我們可以透過一個 $p \times d$ 的投影矩陣P來將其投影到較低維度的空間：
	$$
	Y = XP
	$$

- 這樣可以得到一個d-維的矩陣Y 其中 $d < p$ 




## recommend book

[RG] Rogers, S. and Girolami, M. (2017), _A First Course in Machine Learning_, 2nd edition, Chapman & Hall/CRC
[B] Bishop, C. M. (2006). _Pattern recognition and machine learning_. Springer.
[H1] James, G., Witten, D., Hastie, T., & Tibshirani, R. (2013). _An introduction to statistical learning_ (Vol. 112, p. 18). New York: Springer.
[H2] Friedman, J., Hastie, T., & Tibshirani, R. (2001). _The elements of statistical learning_ (Vol. 1, No. 10). New York: Springer series in statistics.
Normal random variables: [RG] 2.5.4 and [B] 2.3.
PCA: [RG] 7, [B] 12.1, [H1] 10.2, [H2] 14.
ICA: [B] 12.4.1, [H2] 14.7.
FA: [B] 12.2.4.
CCA: [H2] 3.7

























