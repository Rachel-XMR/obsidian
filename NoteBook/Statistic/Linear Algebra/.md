---
File: Statistic/Linear Algebra.md
LINK:
  - "[[Statistic]]"
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


