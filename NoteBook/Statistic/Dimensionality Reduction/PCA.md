---
File: Statistic/PCA.md
LINK:
  - "[[Statistic]]"
  - "[[Dimensionality Reduction]]"
  - "[[Data Science]]"
  - "[[Unsupervised Learning]]"
---

我們總是將<font color="#ff0000">數據置於中心</font>。 一般來說<font color="#ffc000">標準化是必要的</font>，除非我們使用<font color="#ffc000">相同的單位</font>來測量相同的東西


### components to retain 取決於 application： Common method
- looking for an elbow in the scree plot <font color="#00b0f0">碎石圖肘部</font>
- including PCs until the cumulative variance crosses a threshold PC直到積累方差超過閾值
- Kaiser's rule： 僅包括PCs with variance > 1 

# limitation：
- PC are not always easily interpretable bu可解釋的
- Sensitivity to outliers 對異常值的敏感性
- it is a linear method  因此如果數據位於彎曲形狀上，則效果不佳




## General recipe
1. 標準化數據並使用協方差矩陣，或使用相關矩陣
2. 計算特征系統
3. 第i個主成分及時的樣本總方差的百分比為：$\frac{\lambda_i}{\sum_{j=1}^{p} \lambda_j} \times 100\%$


![](PICTURE/PCA/7466dad7be3768c0cfbe80f144706781_MD5.jpeg)

會產生每個成分的方差量 如果碎石圖呈L形狀則PCA被視為效果良好，即前幾個成分解釋了大部分方差


### Biplots 雙標圖
![](PICTURE/PCA/77295b2479388c5d6eb07b5b4705b7d0_MD5.jpeg)
給出一個“雙標圖”
這顯示了數據和原始變量“沿著”前兩個主成分

# Application

### PCA是迄今為止最流行的技術 ：
- 特征系統分析的現代算法意味著這可以擴展到非常大的p例如從 $10^{6}$ keep 100 components
- 更少的數據使得任何其他成分更加高效和穩定

### 消除變量的相關性 ，也是為了增加進一步分析的穩定性
例如：PC可以用作回歸中的協變量 (covariates ) -- principal component regression

### Reduce noise
如果數據是聚類的，我們要盡可能保持各個聚類的分離，減少噪音：假設所有變量都存在獨立同分佈Gaussian noise ，則第一個PC（方差較大，但不含噪音）具有較大的 signal-to-noise ratio

### Other ： 
anomaly detection,
obscuring data
filling in missing values







































