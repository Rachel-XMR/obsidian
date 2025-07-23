
The standard deviation of the $a-th$ varaible:
$$
\sigma_a = \sqrt{S_{aa}}
$$


Standardisation involves涉及 subtracting減去 the mean and dividing by the standard deviation 標準差
$$
\mathbf{Z} = [z_{ia}], \quad \text{where} \quad z_{ia} = \frac{x_{ia} - \langle x_a \rangle}{\sigma_a}, \quad i \in [n] \quad a \text{ and } a \in [p]
$$
$$
X' = \frac{X - \mu}{\sigma}
$$
那麼我們說Z是數據集X的標準化版本 
我們註意到標準化數據的方差-協方差矩陣等於原始數據的相關矩陣


### 為什麼要標準化
- **在機器學習算法中**（如 PCA、線性回歸、KNN、SVM），特徵的不同尺度可能會導致某些特徵對結果的影響過大，影響模型性能。
- **在計算歐幾里得距離的算法中**（如 K-means、KNN），尺度不同的特徵會影響距離計算結果。
- **PCA 降維** 依賴數據的方差，未標準化的數據可能會讓高方差特徵主導主成分分析的結果。




























