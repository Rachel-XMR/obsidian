---
LINK:
  - "[[Classification]]"
  - "[[Clustering]]"
---

首先假定有給定數量K個待查找聚類，然後嘗試為這些聚類選擇中心，使得中心與聚類成員之間的距離較小

密切相關的基於模型的聚類算法也要求我們指定聚類的數量，然後假設一個底層概率模型，並用強大的EM算法以最大似然的方法對我進行擬合


begin with a collection of data points $\mathbf{x}_j \in \mathbb{R}^d$
$$
\mathbf{x}_1, \mathbf{x}_2, \ldots, \mathbf{x}_n
$$
and seek to separate them into $k$ clusters, $C_{1},C_{2},\dots,C_{k}$ where the points in each cluster are close to each other 每個簇中的點彼此接近，以Euclidean distance 測量距離$$
d(\mathbf{x}_j, \mathbf{x}_k) = \|\mathbf{x}_j - \mathbf{x}_k\|_2
$$ where $$
\|\mathbf{u}\|_2 = \sqrt{\sum_{j=1}^{d} u_j^2} = \sqrt{u_1^2 + \cdots + u_d^2}.
$$
Arrange the points $x_{1},x_{2},\dots,x_{n}$ into $k$ groups $C_{1},C_{2},\dots,C_{k}$ (with k $\leq$ n) ---- called clusters so that a certain total within -cluster sum of squares is minimised某個聚類內總和平方和最小化:  $$
\min_{C} \sum_{j=1}^{k} \sum_{\mathbf{x} \in C_j} \|\mathbf{x} - \boldsymbol{\mu}_j\|_2^2.
$$
這裡取最小值，表示所有可能的點到簇的分配情況，$|C_{j}|$ is the number of points in the j-th cluster $\mu_j = \frac{1}{|C_j|} \sum_{\mathbf{x} \in C_j} \mathbf{x}$
is the mean position of the points in the j-th cluster and is called the cluster’s centre 是第j個簇重點的平均位置，成為該簇的中心

![](PICTURE/K-Means%20k%E5%9D%87%E5%80%BC%E8%81%9A%E9%A1%9E%E7%AE%97%E6%B3%95/8d109f0f413f2ab295d76e2ade32323b_MD5.jpeg)

One positions the clusters through an iterative process in which one alternately 通過迭代過程來定位簇 過程中交替
- assigns points to the nearest centre 將點分配到最近的中心
- moves each centre to the middle of its cloud of points 將每個中心移動到其點雲的中間
中心以菱形表示，集群成員身份以顏色表示


過程：
- Choose initial positions for the centers $\boldsymbol{\mu}_1, \ldots, \boldsymbol{\mu}_k$ 選擇中心的初始位置
- 對於每個點 $x_{i}$ 計算 $x_{i}$ 到 $k$ 個中心的Euclidean distances， 並將x分配到中心附近的聚類
- 將所有店分配到聚類後，通過聚類成員取平均值來計算新的中心 $\boldsymbol{\mu}'_{j}$  $$
\mu'_j = \frac{1}{|C_j|} \sum_{\mathbf{x} \in C_j} \mathbf{x}.
$$
- 如果中心沒有移動 $\boldsymbol{\mu}_{j} = \boldsymbol{\mu}'_{j}$ 則停止，否則返回步驟2，並根據新中心組裝新簇


> [!check]+ Choosing the initial centres 選擇初始中心
There are lots of ways to do this. Common approaches include: 
• Choose $k$ points uniformly and at random inside a box defined by the ranges of the data. This risks choosing centres that are far from any of the $x_j$ . 在數據範圍定義的框內均勻隨機地選擇 $k$ 個點 這可能會選擇遠離任何x的中心
• Forgy’s method: choose $k$ of the data points themselves. One risks getting all the centres close together or, at the other extreme, selecting outliers that aren’t especially near any other points. 選擇k個數據點本身 這樣做的風險是讓所有中心都靠的很近
• Random partition隨機分區: assign the points to clusters uniformly at random, so each cluster starts with around $n/k$ points, then use the cluster means as initial centres. 
• Choose the most centrally-located point as $μ_1$, then work through the data and take $μ_2$ to be the next point that is at least a distance $T$ away . . . . This, of course, depends on $T$ and the ordering of the data.
• Maximin: choose $μ_1$ arbitrarily, then choose subsequent centres to be the data point with largest minimum-distance to all the existing centres

該算法最終會停止，但得到的聚類結果取決於初始中心(the clustering one gets depends on the initial centres)。 因此最好使用不同的初始中心運算該算法幾次，然後選擇平方和最小的結果


可能會發生集群最終為空的情況

### Choosing the number of clusters:
#### make an elbow plot 肘部圖

For each of a range of values of k, run the k-means algorithm repeatedly, with dierent random starts, and keep track of the sum-of-squares achieved. Typically this decreases rapidly for a while, then more slowly. Choose the value of k where the break in slope occurs對於k的每個值範圍，重複運行k均值算法，使用不同的隨機起點，並跟蹤所實現的平方和。通常，平方和會在一段時間內迅速下降，然後會變慢。選擇洩露出現突變的k值
![](PICTURE/K-Means%20k%E5%9D%87%E5%80%BC%E8%81%9A%E9%A1%9E%E7%AE%97%E6%B3%95/709830c4b9fdc7cb1f4375bf17cf1eed_MD5.jpeg)




### problem：
K-means seeks to minimize the distance from the centres to the points in the cluster, which implies that it can behave badly when the natural clusters aren’t balls  寻求最小化从中心到聚类中点的距离 寻求最小化从中心到聚类中点的距离

可以通過繪製 elbow plot來查看多少個聚類的時候最合適

![](PICTURE/K-Means%20k%E5%9D%87%E5%80%BC%E8%81%9A%E9%A1%9E%E7%AE%97%E6%B3%95/2493033c0336162845e7ffe64c165223_MD5.jpeg)

如圖 可以看到 k=3的時候 最合適

### ADV and DIS 
Some strengths:
- Simple to implement 易於實現
- Scales to large datasets 擴展到大型數據集
- Always converges 總是收斂
Some limitations:
- k must be pre-specified必須預先指定 → can try different values, but must be done manually  可以嘗試不同值 但必須手動完成 
- Results depend on initial configuration 結果取決於初始配置 → try various starting choices (or even methods) 
- Difficulty clustering data on varying sizes and densities without generalisation 難以對不同大小和密度的數據進行聚類，且無法進行泛化
	→ see kernel-k-means and model-based clustering 
- Difficulty clustering outliers 難以聚類的異常值 → consider removing them first 
- Difficulty scaling with number of dimensions (curse of dimensionality) → reduce dimensionality first by applying PCA (spectral clustering)



## kernel k-means
• Main idea: transform the data into a different, higher-dimensional space where k-means can more easily separate natural clusters.  將數據轉換到不同的、更高維的空間中在該空間中 l-mean可以更容易地分離自然聚類
• Here the map is φ :  R2 → R3 with φ(x1, x2) = (x21, x1x2, x22).
• In the plot at right below, points are coloured according to the clusters assigned by k-means with k = 2 in the transformed space

![](PICTURE/K-Means%20k%E5%9D%87%E5%80%BC%E8%81%9A%E9%A1%9E%E7%AE%97%E6%B3%95/f2439dee1198ebd8978a80b24fbc2b79_MD5.jpeg)

原始空間 (平面)： 綠色在中間，橘色點在外圍城環形 這說明資料在原始的2D空間中不是線性可分的(linearly divisible)；  傳統K-Mean使用Euclidean distance 畫出圓心點

對data做非線性映射 non-linear mapping 
使用核函數定義的高維距離

kernel 是 用於將數據轉換到高維空間然後再進行k-mean 

常見的kernel：

| Kernel 名稱        | 數學形式                                                     | 適合的情境               |                 |                |
| ---------------- | -------------------------------------------------------- | ------------------- | --------------- | -------------- |
| **Linear**       | K(x,y)=x⊤yK(x, y) = x^\top y                             | 和普通 K-means 一樣，線性可分 |                 |                |
| **Polynomial**   | K(x,y)=(x⊤y+c)dK(x, y) = (x^\top y + c)^d                | 有彎曲邊界的分群            |                 |                |
| **RBF/Gaussian** | K(x,y)=exp⁡(−∥x−y∥22σ2)K(x, y) = \exp(-\frac{\\          | x - y\\             | ^2}{2\sigma^2}) | 圓形、環形、任意形狀群體   |
| **Sigmoid**      | K(x,y)=tanh⁡(αx⊤y+c)K(x, y) = \tanh(\alpha x^\top y + c) | 類似神經網絡的激活效果         |                 |                |
| **Laplacian**    | K(x,y)=exp⁡(−∥x−y∥σ)K(x, y) = \exp(-\frac{\\             | x - y\\             | }{\sigma})      | 對 outlier 比較健壯 |


1. 將點隨機均勻的分配到聚類中。
2. 對於每個點x和每個聚類C計算距離
3. 通過將每個點放入中心最近的聚類中來更新聚類分配
4. 如果上一步中聚類分配沒有變化，則停止，否則返回第二步並根據新的分類分配計算新的中心

Kernel Function 是對稱的



![](PICTURE/K-Means%20k%E5%9D%87%E5%80%BC%E8%81%9A%E9%A1%9E%E7%AE%97%E6%B3%95/e0f33306e742519c73afcd900b70a6f6_MD5.jpeg)
















