---
LINK:
  - "[[Data Science]]"
  - "[[Data Science/Neural Networks 神經網絡/Introduction to ANNs]]"
  - "[[cognitive robotics]]"
---

Neural networks are AI computational systems that are “inspired” by biological neural systems

Their main feature is the ability to learn from experience with input stimuli.

![](PICTURE/Neural%20Networks%20%E4%BA%BA%E5%B7%A5%E7%A5%9E%E7%B6%93%E7%B6%B2%E7%B5%A1/772a9799ef6acaadec5f11269c27907e_MD5.jpeg)



## Neural Network 

An artificial neural network consists of a set of interconnected nodes相互連接節點. It is able to
receive input stimuli from the environment and to learn new behaviours/responses

![](PICTURE/Neural%20Networks%20%E4%BA%BA%E5%B7%A5%E7%A5%9E%E7%B6%93%E7%B6%B2%E7%B5%A1/6febfe467a0e796009c66fbfef3b8473_MD5.jpeg)

![](PICTURE/Neural%20Networks%20%E4%BA%BA%E5%B7%A5%E7%A5%9E%E7%B6%93%E7%B6%B2%E7%B5%A1/5f6895255f1acc9cc41acb60715a0112_MD5.jpeg)

神經網絡模擬： 輸入-> 處理 -> 輸出

### 基本結構 ： 三層神經網絡 (最常見)
\[輸入層\] ->  \[隱藏層\] -> \[輸出層\]
每層有：
- 神經元 (Neuron): 每個神經元會接收輸入值，加上權重和偏置，然後經過\[激活函數\]來輸出結果
- 連接 (weights): 控制\[輸入值\] 對\[輸出值\]的影響大小
- 偏差(bias): 幫助模型調整輸出基準值


### 如何學習： 


梯度下降和反向傳播的過程：

![](PICTURE/Neural%20Networks%20%E4%BA%BA%E5%B7%A5%E7%A5%9E%E7%B6%93%E7%B6%B2%E7%B5%A1/6e93195d6edef3fe06fe7ae37c35a80d_MD5.jpeg)
#### 每一層 都會做這個運算 ：
- x：輸入 
- W： 權重 
- b：bias 
- f (.): Activation Function 
- a： 本層輸出

當做一個判斷過程：
	輸入 -> 加權 -> 判斷是否激活 -> 輸出 

#### Loss Function
MSE （Mean Squared Error ）用於回歸任務 
$$
L = \frac{1}{n} \sum_{i=1}^{n} (\hat{y}_i - y_i)^2
$$
Cross Entropy 用於分類任務 
$$
L = -\sum_{i=1}^{n} y_i \log(\hat{y}_i)
$$

#### Backpropagation 反向傳播

計算每個參數 (每條連接的權重) 對錯誤的貢獻

利用鏈式法則 (Chain Rule) 從輸出層一路反推每一層的偏導數 (∂L/∂W)
利用這些導數 (梯度) 來告訴我們每個參數如何調整


### Characteristics

- Neural structure 神經結構
	- neurons 神經元：每個神經元會接收輸入值，加上權重和偏置，然後經過\[激活函數\]來輸出結果
	- connections 連接
- Parallel Distributed Processing 並行分佈式處理
	- more units work at the same time 更多單元同時工作
	- sub-symbolic processing 亞符號處理
- Deep neural networks (2014+)
	- CNN (LeNet, AlexNet…)
	- RNN (LSTM)



![](PICTURE/Neural%20Networks%20%E4%BA%BA%E5%B7%A5%E7%A5%9E%E7%B6%93%E7%B6%B2%E7%B5%A1/e227300306959a4c83e651e95bde749f_MD5.jpeg)


![](PICTURE/Neural%20Networks%20%E4%BA%BA%E5%B7%A5%E7%A5%9E%E7%B6%93%E7%B6%B2%E7%B5%A1/c446a29cf269e3cb49944ac6ebe47261_MD5.jpeg)

![](PICTURE/Neural%20Networks%20%E4%BA%BA%E5%B7%A5%E7%A5%9E%E7%B6%93%E7%B6%B2%E7%B5%A1/b1d88d7f3afa1e705d27d9f4f758b4cd_MD5.jpeg)




### Single output  最簡單的神經元
單輸入輸出 
這是一個類似\[線性回歸\] 或 \[邏輯回歸\]的模型 

> [!hint] 結構：
> - 輸入：x
> - 權重：w
> - 偏差: b
> - 激活函數：  $\sigma$ （例如：sigmoid or ReLU）
> - 輸出：$y=σ(wx+b)$
> 這是一個只有一個輸入與輸出的單元，也稱為 Perception



### Single Layer, Multiple Outputs 單層神經網絡 

> [!hint] 結構
> - 多個輸入：$x_2, ..., x_n$
> - 多個輸出神經元：每個神經元有自己的權重與偏差。
> - 無隱藏層，直接輸出結果 
> eg：
>   - 輸入層->輸出層 (有多個神經元)
>   - 輸出：可為分類認為 (Softmax 多類別) 或 多個回歸目標


#### Single-Layer Feedforward Network 單層前餽神經網絡





### Multiple Layers 多層神經網絡

輸入層
   ↓
隱藏層1（多個神經元 + 激活函數）
   ↓
隱藏層2（可選）
   ↓
輸出層（單輸出或多輸出）

每層之間是\[全連接\]，每個神經元計算：
$$
y = \sigma (Wx+b)
$$
好處：
- 可學習非線性映射 
- 可處理負責分類或回歸任務
- 增加層數與神經元數據可提升表現，但需注意過擬合


| 類型      | 說明            | 任務範例                         |
| ------- | ------------- | ---------------------------- |
| **單輸出** | 模型輸出一個實值或一個類別 | 二分類、單變數回歸                    |
| **多輸出** | 模型輸出一個向量（多個值） | 多分類（Softmax）、多任務學習、圖像中每個像素預測 |


### Input and Activation Function 

![](Pasted%20image%2020250516134218.png)


#### Input Function  輸入加權總和
$$
[y_i = \sum_{j=1}^{N} w_{ij} x_j - b_i]()
$$

- $x_j$：第 $j$ 個輸入神經元的激活值（activation value）
- $w_{ij}$：從輸入神經元 $j$ 到輸出神經元 iii 的權重
- $b_i$ ​：輸出神經元 $i$ 的偏差（bias）
- $y_i$ ​：是「尚未通過激活函數」的輸出（又稱 pre-activation）


#### Activation Function: Linear （線性激活函數） 激活函數的引入是為了進行非線性引擎

- 就像線性回歸
- 不加入任何非線性特征 
- 易於計算與訓練


單層線性模型，無法捕捉複雜關係
多層線性結合 = 單層線性結合 → 沒有增加模型表達能力

| 函數             | 公式                                                                | 特性                       | 圖                                        |
| -------------- | ----------------------------------------------------------------- | ------------------------ | ---------------------------------------- |
| **Sigmoid**    | σ(z)=11+e−z\sigma(z) = \frac{1}{1 + e^{-z}}                       | 壓縮到 [0,1][0, 1]，常用於二分類輸出 | ![](Pasted%20image%2020250516155450.png) |
| **Tanh**       | tanh⁡(z)=ez−e−zez+e−z\tanh(z) = \frac{e^z - e^{-z}}{e^z + e^{-z}} | 壓縮到 [−1,1][-1, 1]，更對稱    | ![](Pasted%20image%2020250516155502.png) |
| **ReLU**       | f(z)=max⁡(0,z)f(z) = \max(0, z)                                   | 非常快，解決梯度消失，現代CNN主流       | ![](Pasted%20image%2020250516155514.png) |
| **Leaky ReLU** | f(z)=max⁡(0.01z,z)f(z) = \max(0.01z, z)                           | 避免ReLU死神經元問題             |                                          |
**激活函數是神經網絡的「非線性引擎」**，讓它不只是線性堆疊，而是真正具備學習複雜模式的能力




##### Limits：
1. 只有線性激活函數 + 沒有隱藏層
	- 這樣的神經網絡與線性模型等價，沒法處理非線性問題
2. 無法表現複雜函數或模式識別
	- 解決辦法：需引入**非線性激活函數**（如 ReLU、sigmoid）與**隱藏層（hidden layers）**


### Gradient Descend 梯度下降 
發生在神經網絡的\[訓練階段\] 用來更新每一層的weights和biases 參數，目的是讓模型的預測越來越準確 


```text
┌───────────────────────────────┐
│        Forward Pass 正向傳播 │
│ x → W → (Wx + b) → f(⋅) → ŷ    │
└───────────────────────────────┘
              ↓
┌───────────────────────────────┐
│      Compute Loss (L)         │ 比較模型預測 
│   L(ŷ, y) = 預測 ŷ 和真值 y 的差  │ 比較模型預測與實際標籤，得到損失值L
└───────────────────────────────┘
              ↓
┌───────────────────────────────┐
│     Backpropagation           │ 反向傳播
│   對 Loss 對每層的 W, b 求偏導    │ 用鏈式法則求導數(梯度) 找出每個參數對損失的影響(偏導數)
└───────────────────────────────┘
              ↓
┌───────────────────────────────┐
│     Gradient Descent          │ 梯度下降
│   W ← W - η·∇W(∂W/∂L) ，b ← b - η·∇b(∂L/∂b)    │ η is learning rate
└───────────────────────────────┘
              ↑
         重複多輪 Epoch

```


![](PICTURE/Neural%20Networks%20%E4%BA%BA%E5%B7%A5%E7%A5%9E%E7%B6%93%E7%B6%B2%E7%B5%A1/5aae715dd6a1be8070dd21125141da10_MD5.jpeg)



![](PICTURE/Neural%20Networks%20%E4%BA%BA%E5%B7%A5%E7%A5%9E%E7%B6%93%E7%B6%B2%E7%B5%A1/36efbbaa8656db13f7558339cf7f9d1c_MD5.jpeg)

學習率： 梯度 (學習) 下降的速度 - 高學習率 = 偏離最小值


#### Batch Gradient Descent 批量梯度下降
- 在每個批次結束時計算梯度 (epoch = 整個數據集) - 在批次結束時更新權重 
	![](PICTURE/Neural%20Networks%20%E4%BA%BA%E5%B7%A5%E7%A5%9E%E7%B6%93%E7%B6%B2%E7%B5%A1/b120a0057715d8d5a1b6c44a7ddc79e1_MD5.jpeg)

#### Stochastic Gradient Descent 隨機梯度下降 
- Calculate gradient at each iteration/stimulus 計算每次迭代/刺激的梯度 
- Dynamic surface 動態表面
- single stimulus error not good approximators
![](PICTURE/Neural%20Networks%20%E4%BA%BA%E5%B7%A5%E7%A5%9E%E7%B6%93%E7%B6%B2%E7%B5%A1/f08f1b742b0b7820cc07bdc06ccf111a_MD5.jpeg)

![](PICTURE/Neural%20Networks%20%E4%BA%BA%E5%B7%A5%E7%A5%9E%E7%B6%93%E7%B6%B2%E7%B5%A1/fb55e5bbcba62cfed2291734c8f5c299_MD5.jpeg)


![](Pasted%20image%2020250516170602.png)


#### Convergence
![](PICTURE/Neural%20Networks%20%E4%BA%BA%E5%B7%A5%E7%A5%9E%E7%B6%93%E7%B6%B2%E7%B5%A1/48717fab4838df897aad203464f24b48_MD5.jpeg)


#### Backpropagation 
Backpropagation is a gradient estimation method commonly used for training a neural network to compute its parameter updates. It is an efficient application of the chain rule to neural networks

![](PICTURE/Neural%20Networks%20%E4%BA%BA%E5%B7%A5%E7%A5%9E%E7%B6%93%E7%B6%B2%E7%B5%A1/32c11797d526f40b86b39fb375456d0c_MD5.jpeg)
![](PICTURE/Neural%20Networks%20%E4%BA%BA%E5%B7%A5%E7%A5%9E%E7%B6%93%E7%B6%B2%E7%B5%A1/274b92dbd0d3e94431bac3cfb1890845_MD5.jpeg)

![](Pasted%20image%2020250516171401.png)
![](PICTURE/Neural%20Networks%20%E4%BA%BA%E5%B7%A5%E7%A5%9E%E7%B6%93%E7%B6%B2%E7%B5%A1/003b8eaa0dbf6ee2bc63522fac1b5e90_MD5.jpeg)



### Overfitting 
![](PICTURE/Neural%20Networks%20%E4%BA%BA%E5%B7%A5%E7%A5%9E%E7%B6%93%E7%B6%B2%E7%B5%A1/238f04613c384728318880df87b3b6bc_MD5.jpeg)


#### Dropout （防止過度擬合） 神經元丟失

- Each neuron is inactive with some random probability during each training minibatch 在每個訓練小批量過程中，每個神經元都以一定的隨機概率處於非活動狀態
	![](PICTURE/Neural%20Networks%20%E4%BA%BA%E5%B7%A5%E7%A5%9E%E7%B6%93%E7%B6%B2%E7%B5%A1/5c787cad0a642a7ba49f3a559d930ba9_MD5.jpeg)
- Forces the network to be accurate even in the absence of certain information/neurons 即使缺乏某些信息/神經元的情況下也能保證網絡的準確性
- One of the most used methods in Deep NN 深度神經網絡中最常用的方法之一


#### Regularisation 正則化

##### L1 Regularisation 

##### L2 Regularisation  權重衰減


#### Max norm constraints 最大范数约束






## Datasets 

### CIFAR-10 
- 32x32 colour images
- 10 classes


### COCO 
Object segmentation




# Data Augmentation 數據增強 
- Extend training set generating
  - To reduce overfitting / improve generalisation
  - Generate new image with noise / light changes, shifting position, flipping
  - Data distortion (LeNet-5)
  - New image translations and horizontal reflections, extracting random 224 × 224 patches (AlexNet)
  - Altering intensities of RGB channels (AlexNet)





# Training Terminology

- **Error functions** (aka Error/Objective funct.)
  - Computes the (average) value of the error function
- **Accuracy**: for classification problems
  - binary accuracy, categorical accuracy, sparse categorical accuracy, top k categorical accuracy
- **Error loss**: difference between the predicted and the observed values
  - mean square error (MSE), root square error (RMSE), mean absolute error (MAE), mean absolute percentage error (MAPE), mean squared logarithmic error (MSLE).
- **Categorical loss**: cross-entropy for classification tasks:
  - binary cross-entropy (2 categories), categorical cross-entropy (multi-class classification), sparse categorical cross-entropy
- **Hinge Loss**: for training classifiers (hinger/square)



# Handling structure data 



- Additional relationships between inputs variables 變量之間的附加關係
	- Language - sequence 
	- Pixels of an image – spatial relationship
- In this class, we will learn CNN
	- Specific to image data


# Computer Vision 
 - Typical tasks/applications
	 - Classification / Image recognition 分類
	 - Detection 檢測
	 - Segmentation 分割
- Image data
	- Comprises a rectangular array of pixels
	- Grey-scale (0 for black and 1 for white) or triplet (red, green, and blue) – channels
	- Non-negative numbers – intensity (e.g., 0,…, 255, 8 bits)
	- MRI data, videos











