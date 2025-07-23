---
LINK:
  - "[[Statistic]]"
  - "[[Dimensionality Reduction]]"
  - "[[Data Science]]"
---
在因子分析中，假設p個觀測值可以用以下公式來解釋m 個 factors
$$
\mathbf{X} = \mu + \boldsymbol{\Delta} \mathbf{F} + \psi
$$


-  $\mathbf{X}$ is a length- $p$ random feature vector. 隨機特征向量
-  $\boldsymbol{\mu}$ is a length- $p$ constant mean vector. 常數均值向量
-   $\boldsymbol{\Lambda}$ is a $p \times m$ constant matrix of $\textbf{loadings}$. 常數載荷矩陣
-  $\mathbf{F}$ is a length- $m$ random vector of uncorrelated $\textbf{factors}$ 不相關因子隨機向量 with $\text{Cov}(\mathbf{F}) = \mathbf{I}_m$.
-  $\boldsymbol{\psi}$ is a $p \times 1$ random vector of $\textbf{specific variances}$. 具有特定方差

因子分析的主要問題是方程並不總能唯一的確定因子，所以我們需要做一些其他事情


但是因子分析 涉及一定程度的主管性，因為他可以自由地輪換因子

因子分析主要用於心理學
### Solving Factor Analysis

#### 1. Choose the exact rotation “by hand” 
需要對研究的現象有很強的專業知識 



#### 2. Assume multivariate normality假設多元正態分佈
並使用方差最大等原理修復旋轉


#### 3. independent components analysis (ICA3)
Invoke full statistical independence of the factors while maximising their deviation from multivariate normality 


















































































