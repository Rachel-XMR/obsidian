$$
\mathbf{X} = [\mathbf{x}_i^\top]_{i=1}^n = \begin{bmatrix} \mathbf{x}_1^\top \\ \mathbf{x}_2^\top \\ \vdots \\ \mathbf{x}_n^\top \end{bmatrix} = [\mathbf{y}_a]_{a=1}^p = \begin{bmatrix} y_1 & y_2 & \cdots & y_p \end{bmatrix}
$$


where each $y$  is essentially a univariate dataset and each $x^{T}$ is a set of $p$ observations of an individual. 

我們將 $x$ 成為第i個觀測的特征向量，並且通常會刪除 $i$ 並且為 $x$ 來表示典型的此類向量

### 樣本方差-協方差矩陣 (調整為1確實自由度)：
$$
S = [S_{ab}], \quad \text{where} \quad S_{ab} = \frac{1}{n-1} \sum_{i=1}^{n} (x_{ia} - \langle x_a \rangle)(x_{ib} - \langle x_b \rangle)
$$
 The sample correlation matrix has elements that relate to the slopes of the (linear) regression lines between variables 樣本相關矩陣具有與斜率相關的元素
$$
\mathbf{R} = [R_{ab}], \quad \text{where} \quad R_{ab} = \frac{S_{ab}}{\sqrt{S_{aa} S_{bb}}}
$$










































