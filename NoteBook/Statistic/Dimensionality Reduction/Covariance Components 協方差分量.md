---
LINK:
  - "[[Statistic]]"
---

[協方差矩陣 (Variance-Covariance Matrices)](Statistic/Linear%20Algebra/Eigensystem%20特征系統.md#**變異數-共變異數矩陣%20協方差矩陣%20(Variance-Covariance%20Matrices)%20的特徵系統**)

令 $\boldsymbol{\Psi} = \text{diag}(\boldsymbol{\psi})$ denote the diagonal matrix defined by $\boldsymbol{\Psi}$
$$
\mathbf{S} = \boldsymbol{\Lambda} \boldsymbol{\Lambda}^T + \boldsymbol{\Psi}
$$
這意味將矩陣 將矩陣M的第a個對角線元素記為 $M_{a}$ ，那麼我們可以將第a個測量值的方差分解為 $$
\text{Var}(X_a) = \underbrace{\Lambda_a^2}_{\text{Commonality}} + \underbrace{\Psi_a}_{\text{Specific Variance}}
$$ 一般而言，共性（ commonality）越大，特定方差（specific variance）越小

我們不僅僅通過太多的因素來實現這一點，因此在因素的數量和特定方差 (也稱為誤差) 的減少之間存在權衡

