---
LINK:
  - "[[Statistic]]"
  - "[[Linear Algebra]]"
---
For an $n × n$ matrix $M$ , a scalar $λ$ and a $length-n$ vector $v$, then if:
$$
M \mathbf{v} = \lambda \mathbf{v}
$$

we say that $λ$ is an eigenvalue 特征 of $M$ and $v$ is an eigenvector特征向量

In general there will be $n$ such vectors and values. We call the collection of these $(\lambda_i, \mathbf{v}_i)_{i=1}^n$ the $\textbf{eigensystem}$ of the matrix.





We will typically be interested in the eigensystem of **variance-covariance 協方差矩陣** matrices, which means that:
1. The matrix will be $\textbf{symmetric}$ 對稱, meaning that $M^\top = M$, and so we only need to consider right multiplication as above.
2. The eigenvalues will be positive and real-valued.
3. The eigenvectors will be $\textbf{orthogonal}$, meaning that $\mathbf{v}_i^\top \mathbf{v}_j = 0$ unless $i = j$. 如果兩個成績為0則為正交



## **特徵值 (Eigenvalues) 和 特徵向量 (Eigenvectors)**
    
 - 定義：對於一個 n x n 的矩陣 M，如果存在一個標量 λ 和一個長度為 n 的向量 v，使得 $Mv = λv$ 成立，那麼我們稱 λ 為矩陣 M 的一個特徵值，v 為對應於特徵值 λ 的一個特徵向量。
 - 意義：特徵向量表示矩陣 M 作用在它上面時，只會改變其大小（乘以特徵值 λ），而不會改變其方向。特徵值則表示這種大小變化的比例。
- $Mv = λv$，這是特徵值和特徵向量的基本公式。
## **特徵系統 (Eigensystem)**
- 定義：一個 $n \times n$ 的矩陣 $M$ 的特徵系統是指由其所有特徵值 ($λᵢ$) 和對應的特徵向量 ($vᵢ$) 組成的集合，通常表示為 $(\lambda_i, \mathbf{v}_i)_{i=1}^n$
- 意義：特徵系統完整地描述了矩陣 M 的性質，可以幫助我們理解矩陣的作用方式。
## **變異數-共變異數矩陣 協方差矩陣 (Variance-Covariance Matrices) 的特徵系統**
    
- 應用：在統計學和機器學習中，我們經常需要分析變異數-共變異數矩陣，它描述了數據中各個變量之間的關係。
- 性質：
    1. **對稱性 (Symmetric)**：變異數-共變異數矩陣是對稱矩陣，即 $Mᵀ = M$。這意味著我們只需要考慮右乘向量的情況（Mv）。
    2. **正實數特徵值 (Positive and Real-valued Eigenvalues)**：變異數-共變異數矩陣的特徵值都是正實數。
    3. **正交特徵向量 (Orthogonal Eigenvectors)**：變異數-共變異數矩陣的不同特徵值對應的特徵向量是正交的，即 vᵢᵀvⱼ = 0 (除非 i = j)。

> [!hint] 
> - **特徵值和特徵向量**是描述矩陣性質的重要工具。
> - **特徵系統**完整地描述了矩陣的作用方式。
> - **變異數-共變異數矩陣**的特徵系統具有特殊的性質，可以幫助我們分析數據中的變量關係。

在主成分分析中，我呢吧可以使用變異數-共變異數矩陣的特征系統來提取數據的主要成分





## Multivariate normal contours 多元正態輪廓

 the multivariate normal distribution has ellipsoidal橢圓 contours centred on the mean


> [!important]+ 通過協方差矩陣Σ進行特征值分解 (Eigenvalue Decomposition, EVD)  
> $$
\mu = \begin{pmatrix} 1 \\ 1 \end{pmatrix}, \quad \Sigma = \begin{pmatrix} 1 & 0.75 \\ 0.75 & 2 \end{pmatrix}
> $$
> 
>> [!important]+ Step 1: 寫出協方差矩陣
>> $$
\quad \Sigma = \begin{pmatrix} 1 & 0.75 \\ 0.75 & 2 \end{pmatrix}
>> $$
> 
> 
>> [!important]+ Step 2: 計算特征值
>>  特徵值 $\lambda$ 滿足方程式：
>>  $$
\det(\Sigma - \lambda I) = 0
>>  $$
>> 其中 $I$ 是單位矩陣：
>> $$
\begin{vmatrix} 1 - \lambda & 0.75 \\ 0.75 & 2 - \lambda \end{vmatrix} = 0
>> $$
>> 計算行列式:
>> $$
\begin{align*}
(1 - \lambda)(2 - \lambda) - (0.75)(0.75) &= 0 \\
2 - \lambda - 2\lambda + \lambda^2 - 0.5625 &= 0 \\
\lambda^2 - 3\lambda + 1.4375 &= 0
\end{align*}
>> $$
>> 解二次方程：
>> $$
\begin{align*}
\lambda &= \frac{3 \pm \sqrt{9 - 5.75}}{2} = \frac{3 \pm \sqrt{3.25}}{2} \\
\lambda_1 &\approx 2.40, \quad \lambda_2 \approx 0.60
\end{align*}
>> $$
>
>> [!important]+ Step 3: 計算對應的特徵向量
>> 解 $(\Sigma - \lambda I) \mathbf{v} = 0$ 找到對應的特征向量
>> $$
\begin{align*}
\begin{pmatrix} 1 - 2.40 & 0.75 \\ 0.75 & 2 - 2.40 \end{pmatrix} \begin{pmatrix} v_{11} \\ v_{12} \end{pmatrix} &= 0 \\
\begin{pmatrix} -1.40 & 0.75 \\ 0.75 & -0.40 \end{pmatrix} \begin{pmatrix} v_{11} \\ v_{12} \end{pmatrix} &= 0
\end{align*}
>> $$
>>> 展開矩陣乘法：
>>> $$
\begin{align*}
-1.40v_{11} + 0.75v_{12} &= 0 \\
0.75v_{11} - 0.40v_{12} &= 0
\end{align*}
>>> $$
>>> 將第一方程改寫：
>>> $$
v_{12} = \frac{1.40}{0.75} v_{11} \approx 1.87 v_{11}
>>> $$
>>> 從第二個方程式：
>>> $$
v_{12} = \frac{0.75}{0.40} v_{11} \approx 1.875 v_{11}
>>> $$
>>> 兩個方程結果一致，說明這是一個線性相關的系統，表示特徵向量的方向為：
>>> $$
v_1 \propto \begin{pmatrix} 1 \\ 1.87 \end{pmatrix}
>>> $$
>>> 對特征向量進行正則化，使其長度為1：
>>> $$
\begin{align*}
\sqrt{(1)^2 + (1.87)^2} &= \sqrt{1 + 3.4969} = \sqrt{4.4969} \approx 2.12 \\
v_1 &= \frac{1}{2.12} \begin{pmatrix} 1 \\ 1.87 \end{pmatrix} \approx \begin{pmatrix} 0.47 \\ 0.88 \end{pmatrix}
\end{align*}
>>> $$
>> 
>> 解方程得到：
>> $$
>> \lambda_1 \approx 2.40, \quad \mathbf{v}_1 \approx \begin{pmatrix} 0.47 \\ 0.88 \end{pmatrix}, \quad \lambda_2 \approx 0.60, \quad \mathbf{v}_2 \approx \begin{pmatrix} -0.88 \\ 0.47 \end{pmatrix}
>> $$
![](PICTURE/Eigensystem%20%E7%89%B9%E5%BE%81%E7%B3%BB%E7%B5%B1/1adf48eb6558435615e4568d1a1ff32f_MD5.jpeg)

















































