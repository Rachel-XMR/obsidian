---
LINK:
  - "[[Statistic]]"
---
Multivariate Normal Distribution的contours與Covariance Matrix的Eigensystem


# Multivariate Normal Distribution

- 定義：多元常態分佈是單變量常態分佈在多維空間中的推廣。它由均值向量 (μ) 和共變異數矩陣 (Σ) 兩個參數決定。
- 輪廓線 (Contours)：多元常態分佈的等密度輪廓線是橢圓形的，中心位於均值向量 μ。
- 例子：圖中給出了一個二維多元常態分佈，其均值向量 μ = (1, 1)ᵀ，共變異數矩陣 Σ = ((1, 0.75), (0.75, 2))。


輪廓線與特徵系統的關係
- 主軸 (Major Axis)：特徵值最大的特徵向量 v₁ 指向橢圓輪廓線的主軸方向，主軸的長度與 √λ₁ 成正比。
- 副軸 (Minor Axis)：特徵值最小的特徵向量 v₂ 指向橢圓輪廓線的副軸方向，副軸的長度與 √λ₂ 成正比。
- 例子：圖中指出 3√λ₁v₁ 位於橢圓輪廓線的主軸上，3√λ₂v₂ 位於副軸上。

特徵值表示特徵向量方向上的變異數大小。特徵值越大，表示該方向上的變異數越大，數據在該方向上的分佈越廣





## [Vector 向量](Statistic/Linear%20Algebra/Foundation.md#Vector%20向量)與矩陣表示
在多元常態分佈中，我們通常使用均值向量 $μ$ 和協方差矩陣 $Σ$ 來描述分佈
$$
X \sim \mathcal{N}(\mu, \Sigma)
$$

>  - 其中 $μ$ 是 $d \times 1$ 的向量，表示每個變數的均值
>  - $Σ$ 是 $d \times d$ 的矩陣，表示變數之間的關係 (協方差)

這裡的矩陣來自[線性代數 ](Statistic/Linear%20Algebra/Linear%20Algebra.md)


## [特征值分解(Eigenvalue Decomposition)](Statistic/Linear%20Algebra/Eigensystem%20特征系統.md)
協方差矩陣式對稱的可以進行特征值分解
$$
\Sigma = Q \Lambda Q^T
$$
其中：
- $Q$ 是正交矩陣 (Orthogonal Matrix) 包含特征向量 (eigenvectors)
- $\Lambda$ 是對角矩陣 (Diagonal Matrix) 包含特征值 (eigenvectors)


PCA 和高維資料的集合性質非常重要




# Covariance Matrix
- 定義：共變異數矩陣描述了多元常態分佈中各個變量之間的變異數和共變異數。
- 特徵系統 (Eigensystem)：共變異數矩陣的特徵系統由其特徵值 (λᵢ) 和特徵向量 (vᵢ) 組成。
- 例子：圖中給出了共變異數矩陣 Σ 的特徵值和特徵向量：λ₁ ≈ 2.40，v₁ ≈ (0.47, 0.88)ᵀ；λ₂ ≈ 0.60，v₂ ≈ (-0.88, 0.47)ᵀ。


雖然 **多元常態分佈** 是機率與統計的概念，但它**大量依賴線性代數的工具**來進行分析，包括：

1. **矩陣運算** (加法、乘法、行列式、逆矩陣)
    
2. **特徵值與特徵向量** (用於解釋協方差結構)
    
3. **二次型 (Quadratic Forms)** (用於機率密度函數)
    
4. **線性變換與旋轉** (解釋資料分佈形狀)




## 應用

- **主成分分析 (Principal Component Analysis, PCA)**：PCA 是一種常用的降維方法，它利用共變異數矩陣的特徵系統來找到數據的主要成分，並將數據投影到這些成分上。
- **人臉辨識 (Face Recognition)**：在人臉辨識中，我們可以將人臉圖像表示為高維向量，然後使用 PCA 來提取人臉的主要特徵，從而實現人臉辨識。
- **圖像壓縮 (Image Compression)**：在圖像壓縮中，我們可以將圖像表示為矩陣，然後使用奇異值分解 (Singular Value Decomposition, SVD) 來提取圖像的主要特徵，從而實現圖像壓縮。






















