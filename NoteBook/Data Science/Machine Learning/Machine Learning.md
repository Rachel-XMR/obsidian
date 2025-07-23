---
LINK:
  - "[[Data Science]]"
  - "[[Unsupervised Learning]]"
  - "[[Supervised Learning]]"
---




## 機器學習劃分方式 (根據學習方式)
機器學習通常是按照學習方式來分類


### 1.  [監督學習 (Supervised Learning)](Data%20Science/Machine%20Learning/Supervised%20Learning/Supervised%20Learning.md)
- 依據標註數據 (有標籤)
- 目標是學習輸入 X -> 輸出Y之間的映射關係
- 典型方法：
	- Classification：
		- 線性回歸 (Linear Regression)
		- 支持向量機 (SVM)
		- 決策樹 (Decision Tree)
		- 神經網絡 (Neural Network)
	- Regression： 線性回歸， Lasso回歸， XGBoost


### 2.  [Unsupervised Learning](Data%20Science/Machine%20Learning/Unsupervised%20Learning/Unsupervised%20Learning.md)
- no label 讓模型自行發現數據結構
- 典型方法：
	- Clustering:
		- K-means 
		- DBSCAN
	- Dimensionality Reduction:
		- PCA 
		- SVD 
	- Generative Models: 
		- GAN 
		- VAE 



### Semi-Supervised Learning 
一部分數據有標籤，一部分沒有 --> 常用於標註成本高的情境
Example：
- 自訓練 self-training 
- 一致性正則化 Consistency Regularization



### Self-Supervised Learning 
- 一種特殊的監督學習， 從數據本身生成標籤 (比如對比學習、預測下一個詞)
- example：
	- NLP：BERT、GPT(預測下一個單詞)
	- CV：SimCLR、 MoCo (對比學習)






### Reinforcement Learning 強化學習
- 透過與環境互動來學習決策策略
- 典型算法：
	- Q-learning
	- 深度強化學習
		- DQN 
		- PPO 
		- A3C






















