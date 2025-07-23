---
File: Statistic/Linear Algebra.md
LINK:
  - "[[Statistic]]"
  - "[[Linear Algebra]]"
---


# Vector 向量

## column vector：
是一個  $n \times 1$ matrix， 儘管在更多的數學工作中，存在區別，意味著不同的符號

$$\mathbf{v} = \left( v_i \right)_{i=1,\ldots,n} = \begin{pmatrix}
v_1 \\
v_2 \\
\vdots \\
v_n
\end{pmatrix}$$



## row vector:
$$
\mathbf{w}^\top = \left( w_j \right)_{j=1,\ldots,p}^\top = \begin{pmatrix}
w_1 & w_2 & \cdots & w_n
\end{pmatrix}
$$


## Vector Lengths：


The usual ‘length’ of a vector is given by e.g. Pythagoras’ theorem（畢達哥拉斯定理）:$H = \sqrt{O^2 + A^2}$

For a length-n vector v, we will often consider a generalisation of this to the $\ell_p$ norm, which is $$\|\mathbf{v}\|_p = \left( \sum_{i=1}^{n} |v_i|^p \right)^{1/p}$$
### Norms
- Norms that are often used in clustering procedures are: 聚類過程中經常使用的規範是
	- $\ell_2$ – Euclidian distance (most common) 歐幾裡得距離 $\|\mathbf{v}\|_2 = \left( \sum_{i=1}^{n} |v_i|^2 \right)^{1/2}$  表示向量的"直線"長度  單獨向量本身計算=> $\|\mathbf{b}|_2 = \sqrt{\mathbf{b}^\top \mathbf{b}}$ 
	- $\ell_1$ – Manhattan distance 曼哈頓距離 $\|\mathbf{v}\|_1 = \sum_{i=1}^{n} |v_i|^1$  表示向量各分量絕對值之和（也稱為"城市街區"距離）
	- $\ell_{\infty}$ – Supremum distance 極值距離 $\|\mathbf{v}\|_{\infty} = \max(|v_1|, |v_2|, \ldots, |v_n|)$ 表示向量分量中絕對值的最大值


## Vector-vector products
length-p vectors: u and w length-n vector w

### inner product
 inner product of u and v is a scalar
$$
\mathbf{u}^T \mathbf{v} = \mathbf{v}^T \mathbf{u} = \mathbf{u} \cdot \mathbf{v} = \mathbf{v} \cdot \mathbf{u} = \sum_{i=1}^{p} u_i v_i
$$

vector length is $|\mathbf{v}| = \sqrt{\mathbf{v} \cdot \mathbf{v}} = \|\mathbf{v}\|_2$

### outer product
w and v is an n × p matrix

$$
\mathbf{w} \mathbf{v}^\top = \mathbf{w} \otimes \mathbf{v} = [w_i v_j]_{\substack{i=1,\ldots,n}}^{j=1,\ldots,p}
$$

## Vector projection 矢量投影

### basis vectors 基向量
![](PICTURE/Foundation/658838cd1260011a1a18ad6316c3f36e_MD5.jpeg)

$$
\hat{e}_1 = \begin{pmatrix} 1 \\ 0 \end{pmatrix}, \quad \hat{e}_2 = \begin{pmatrix} 0 \\ 1 \end{pmatrix}
$$
向量表示變形為：
$$
\mathbf{r} = \begin{pmatrix} x \\ y \end{pmatrix} = r_1 \hat{\mathbf{e}}_1 + r_2 \hat{\mathbf{e}}_2 = x\hat{\mathbf{e}}_1 + y\hat{\mathbf{e}}_2
$$
projection of r onto a vector, in this case $\hat{\mathbf{e}}_i$
$$
r_i = \frac{\mathbf{r} \cdot \hat{\mathbf{e}}_i}{|\hat{\mathbf{e}}_i|}, \quad \text{for } i \in \{1, 2\}
$$


The basis vectors don’t need to be the standard Cartesian basis vectors
![](PICTURE/Foundation/e0fc4c99389001ca5044a5c8181ff017_MD5.jpeg)

$$
\hat{\mathbf{u}}_1 = \frac{1}{\sqrt{2}} \begin{pmatrix} 1 \\ 1 \end{pmatrix}, \quad \hat{\mathbf{u}}_2 = \frac{1}{\sqrt{2}} \begin{pmatrix} -1 \\ 1 \end{pmatrix}
$$
can be write :
$$
\mathbf{r} = \tilde{r}_1 \hat{\mathbf{u}}_1 + \tilde{r}_2 \hat{\mathbf{u}}_2 = 3\sqrt{2} \hat{\mathbf{u}}_1 + \sqrt{2} \hat{\mathbf{u}}_2
$$

線性組合可以將向量分解為沿著基向量方向的分量 $\mathbf{r} = \tilde{r}_1 \hat{\mathbf{u}}_1 + \tilde{r}_2 \hat{\mathbf{u}}_2 = 3\sqrt{2} \hat{\mathbf{u}}_1 + \sqrt{2} \hat{\mathbf{u}}_2$


> [!tip] 
>  - 向量不一定是標準笛卡爾基向量，我們可以選擇任何線性無關的向量作為基向量
>  - 向量投影公式在任何基向量下都適用，可以將向量分解為沿著基向量方向的分量
>  - 線性組合可以將向量表示為基向量的線性組合，其中係數是向量在基向量上的分量
>  - 基向量是相互垂直的，他們構成一個正交基

###### 應用

- 在計算機圖形學中，我們可以使用非標準基向量來表示物體的局部坐標系。
- 在機器學習中，我們可以使用非標準基向量來進行特徵提取和降維。
- 在信號處理中，我們可以使用非標準基向量來表示信號的頻域分量。




# Matrices 矩陣

<mark style="background: #FFB8EBA6;"></mark>在計算機中模擬事物或構建事物時，矩陣會被大量使用

An $n \times p$ matrix $M$ is an array of numbers made up of $n$ rows and $p$ columns. We write this in the following way:

$$
M = \left[ M_{ij} \right]^{j=1,\ldots,p}_{\substack{i=1,\ldots, n}} = \left[ \begin{array}{cccc}
M_{11} & M_{12} & \cdots & M_{1p} \\
M_{21} & M_{22} & \cdots & M_{2p} \\
\vdots & \vdots & \ddots & \vdots \\
M_{n1} & M_{n2} & \cdots & M_{np}
\end{array} \right].
$$

The matrix transpose exchanges rows and columns and is written：
$$M^\top = \left[ M_{ji} \right]^{j=1,\ldots,p}_{\substack{i=1,\ldots,n}} = \begin{bmatrix}
M_{11} & M_{21} & \cdots & M_{n1} \\
M_{12} & M_{22} & \cdots & M_{n2} \\
\vdots & \vdots & \ddots & \vdots \\
M_{1p} & M_{2p} & \cdots & M_{np}
\end{bmatrix}.$$



## Zero matrix
 A matrix in which all of the entries are $0$.

3 X 3 zero matrix: $O_{3 \times 3} = \begin{bmatrix} 0 & 0 & 0 \\0 & 0 & 0 \\0 & 0 & 0\end{bmatrix}$
2 X 4 zero matrix: $O_{2 \times 4} = \begin{bmatrix}0 & 0 & 0 & 0 \\0 & 0 & 0 & 0\end{bmatrix}$ 


## Scalar-Matrix Multiplication 
Multiplication of this by a scalar (regular number) α involves multiplying each element of the matrix by the scalar so that  i=1,\ldots, n  j=1,\ldots, p
$$
\alpha M = \left[ \alpha M_{ij} \right]^{j=1,\ldots, p}_{\substack{i=1,\ldots, n}}
$$

given an other matrix $N = \left[ N_{ij} \right]^{j=1,\ldots, p}_{\substack{i=1,\ldots, n}}$

$$
M + N = \left[ M_{ij} + N_{ij} \right]^{j=1,\ldots, p}_{\substack{i=1,\ldots, n}}
$$
結合：
$$
\alpha (M + N) = \alpha M + \alpha N
$$


## identity matrix
The $n\times n$ **identity matrix**, denoted $I_n$, is a matrix with $n$ rows and $n$ columns. The entries on the diagonal from the upper left to the bottom right are all $1$ 's, and all other entries are $0$.

$$
I_2 = \begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix}

I_3 = \begin{bmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix}

I_4 = \begin{bmatrix} 1 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 1 & 0 \\ 0 & 0 & 0 & 1 \end{bmatrix}
$$


## Matrix Multiplication

$n \times p$ matric $M$ and $p \times r$ matrix $Q$ -> matrix product $MQ$ with $n \times r$

$$
\left[ MQ \right]_{ik} = \sum_{j=1}^{p} M_{ij} Q_{jk},
$$

矩陣需要注意順序 -> $MQ \neq QM$ 
矩陣轉置：$(MQ)^T = Q^T M^T$ 
$$
\left[ \left( MQ \right)^\top \right]_{ki} = \left[ MQ \right]_{ik} = \sum_{j=1}^{p} M_{ij} Q_{jk} = \sum_{j=1}^{p} \left[ Q^\top \right]_{kj} \left[ M^\top \right]_{ji} = Q^\top M^\top
$$


## Pointwise Multiplication 逐點乘法  (Hadamard product) 元素積A⊙B
$M\circ R$：
$$
\left[MR\right]_{ij} = M_{ij}R_{ij}
$$

$$
M \circ R = R \circ M
$$

define pointwise exponentiation

$$
M^{\circ q}=[M_{ij}^{q}]_{i=1,...,n}^{j=1,...,p}
$$

滿足乘法交換律： $M ⊙ R = R ⊙ M$





| **操作**                                                           | **数学符号**       | **举例**                                                            | **说明**                                                                                                          |
| ---------------------------------------------------------------- | -------------- | ----------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| 点积(dot product)，也称内积(inner product)，标量积（scalar product）          | A.B  <br><a,b> | ![](PICTURE/Foundation/2b633e31110dd21e347d9c33dba7f836_MD5.jpeg) | 1.向量点积。变成一个数。<br><br>2.矩阵点积。矩阵的点积是每行每列的点积的矩阵。                                                                   |
| 外积(outer product)                                                | A⊗B            | ![](PICTURE/Foundation/a5affbf266c8e912ee935ee7a6491ed9_MD5.jpeg) | 1.向量外积。m维与n维的外积变成 $m*n$ 维。<br><br>2.矩阵外积。$m*n$ 维矩阵与 $a*b$ 维矩阵的外积变成 $m*n*a*b$ 维矩阵。matrix outer 是vector outer的并集。 |
| 元素积(element-wise product, point-wise product, Hadamard product ) | A⊙B            | ![](PICTURE/Foundation/656b36788fca5a2e7a64412f1b0296ae_MD5.jpeg) | 1.向量元素积。m维与n维的元素积变成 $m*n$ 维矩阵。n维与n维的元素积变成n维向量。<br><br>2.矩阵元素积。$m*n$ 维矩阵与 $m*n$ 维矩阵的元素积变成 $m*n$ 维矩阵              |
ref: https://blog.csdn.net/zkq_1986/article/details/78203972



##  Matrix-vector Multiplication

vectors can be thought of as matrices where one of the dimensions is 1

左乘和右乘的區別是矩陣在左邊還是右邊 -> 不同的線性變換過程

The right-multiplication of v by $M$ is a $length-n$ column vector with $i-th$ element  可以理解為線性變換
$$(Mv)_i = \sum_{j=1}^p M_{ij}v_j$$
 The left-multiplication of $w^{T}$ by $M$ is a $length-p$ row vector with $j-th$ element
$$
(\mathbf{w}^\top M)_j = \sum_{i=1}^n w_i M_{ij}
$$













