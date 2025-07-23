---
LINK:
  - "[[Statistic]]"
  - "[[Linear Algebra]]"
---
線性回歸可以被視為最大化相關性的一種方法，它解釋了再簡化的線性回歸模型中，最小化誤差與最大化預測變量和響應變量之間的關係

Consider Equation：簡化的線性回歸模型
$$
Y = \boldsymbol{\beta} \cdot \mathbf{X} + \mathcal{E}
$$
$\beta$ 是回歸係數 $\mathcal{E}$ 是零均值誤差項，表示模型無法解釋的部分
其中Y和X分別是zero-mean unit-(co) variance random scalar（零均值單位（協）方差隨機標量）和向量，E是零均值誤差。重寫Equation為：
$$
\mathcal{E} = Y - \boldsymbol{\beta} \cdot \mathbf{X}
$$
誤差的平方期望值：
$$
\mathbb{E}[\mathcal{E}^2] = 1 + |\boldsymbol{\beta}|^2 - 2 \times \text{cov}(Y, \boldsymbol{\beta} \cdot \mathbf{X})
$$
$|{\beta}|^2$ 表示回歸係數向量 $\beta$ 的模的平方，與模型的複雜度相關
This means that $\textbf{error minimisation}$ is related to finding parameters such that $|\boldsymbol{\beta}|^2$ is small and $\text{cov}(Y, \boldsymbol{\beta} \cdot \mathbf{X})$ is large. $\textbf{Maximization of correlation}$ $\text{cov}(Y, \boldsymbol{\beta} \cdot \mathbf{X})/|\boldsymbol{\beta}|$ does that as well.
$cov(Y, β · X)$ 表示響應變量Y和預測值 ${\beta}$ 

最小化 $E[ε²]$ 等價於找到一組迴歸係數 $β$，使得 $|β|²$ 較小且 $cov(Y, β · X)$ 較大
最大化相關性 $cov(Y, β · X) / |β|$ 也能達到相同的效果
線性迴歸可以被視為最大化響應變量 Y 和預測值 β · X 之間的相關性


**線性迴歸的目標是找到一組迴歸係數 β，使得模型能夠最好地擬合數據**

從誤差最小化的角度來看，線性迴歸的目標是最小化響應變量 Y 的實際值與模型預測值 $β · X$ 之間的差異。


- **共變異數 (Covariance)**：共變異數衡量了兩個隨機變量之間線性關係的強度和方向。
- **相關性 (Correlation)**：相關性是標準化的共變異數，它衡量了兩個隨機變量之間線性關係的強度和方向，並且不受變量尺度的影響。
- **最小二乘法 (Least Squares)**：最小二乘法是求解線性迴歸模型參數 β 的常用方法，它通過最小化誤差平方和來找到最佳擬合。












