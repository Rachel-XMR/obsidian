---
LINK:
  - "[[Text Mining]]"
  - "[[Natural Language Processing NLP]]"
  - "[[Data Science/Neural Networks 神經網絡/Neural Networks 神經網絡]]"
File: Data Science/Artificial Neural Networks 神經網絡/Introduction.md
---

## Machine learning (supervised learning definition)

- Given an input x, find an output y
- Classification: y is one of N classes

[Open: Pasted image 20250202171527.png](PICTURE/Introduction%20to%20ANNs/017746f009b6703c107a493d83adc95c_MD5.jpeg)
![](PICTURE/Introduction%20to%20ANNs/017746f009b6703c107a493d83adc95c_MD5.jpeg)

像Supervised Machine Learning

### Neurons 神經元
[Open: Pasted image 20250202172018.png](PICTURE/Introduction%20to%20ANNs/9a97a633dc51057232c4895e85dd5372_MD5.jpeg)
![](PICTURE/Introduction%20to%20ANNs/9a97a633dc51057232c4895e85dd5372_MD5.jpeg)
生物神經元啟發的計算單元

x1 x2 x3 轉換成vector


在神經網絡中有好幾個函數 $f（x）$  （激活函數）
[Open: Pasted image 20250202172134.png](PICTURE/Introduction%20to%20ANNs/f01a4d4c3798aaa14114e36573be3353_MD5.jpeg)
![](PICTURE/Introduction%20to%20ANNs/f01a4d4c3798aaa14114e36573be3353_MD5.jpeg)
對於神經元網絡 可能取決於下游任務




### Multi-layer Neural Networks

[Open: Pasted image 20250202174712.png](PICTURE/Introduction%20to%20ANNs/3da3846fce2dded04125d066526a24f3_MD5.jpeg)
![](PICTURE/Introduction%20to%20ANNs/3da3846fce2dded04125d066526a24f3_MD5.jpeg)

$y_1$ 是隱藏層 hidden Layer
![](PICTURE/Introduction%20to%20ANNs/a16358777e8c3b0c48eee536d7f782a4_MD5.jpeg)


How many hidden layers do we need?
需要至少一層hidden layer
[Open: Pasted image 20250202174749.png](PICTURE/Introduction%20to%20ANNs/a4122808dbc994b693a7afdc1e4e6001_MD5.jpeg)
![](PICTURE/Introduction%20to%20ANNs/a4122808dbc994b693a7afdc1e4e6001_MD5.jpeg)
In theory, one hidden layer is enough: two-layer neural networks are universal approximators (they are capable of approximating any continuous function to any desired degree of accuracy). 理論上，一個隱藏層就夠了，兩層神經網路是通用近似器（它們能夠近似任何連續函數到任何想要的精確度）。

[Open: Pasted image 20250202174843.png](PICTURE/Introduction%20to%20ANNs/fafc045ef2ace1e7bf766cdcd0843742_MD5.jpeg)
![](PICTURE/Introduction%20to%20ANNs/fafc045ef2ace1e7bf766cdcd0843742_MD5.jpeg)



### Classification Task

[Open: Pasted image 20250202174920.png](PICTURE/Introduction%20to%20ANNs/ef56823d84e5c3f66357ee6a1cba22a4_MD5.jpeg)
![](PICTURE/Introduction%20to%20ANNs/ef56823d84e5c3f66357ee6a1cba22a4_MD5.jpeg)


Training a neural net (for classification)
- Training set: D train = {(x1 ,c 1 ),..., (xn ,c n )}, a set of pair x and its correct class c
- Our neural network has parameters θ (the set of all the weight matrices)
- Minimize the cross-entropy loss (i.e., negative log-likelihood)

$$
J(\theta) = \frac{1}{n} \sum_{i=1}^{n} -\log y_{i,c_i} + \frac{\lambda}{2} \|\theta\|_2^2 \equiv -\frac{1}{n} \sum_{i=1}^{n} \log Pr(c_i|\mathbf{x}_i) + \frac{\lambda}{2} \|\theta\|_2^2
$$


### (Minibatch) Stochastic gradient descent

[Open: Pasted image 20250202175250.png](PICTURE/Introduction%20to%20ANNs/Pasted%20image%2020250202175250.png)
![](PICTURE/Introduction%20to%20ANNs/Pasted%20image%2020250202175250.png)

1. sample a minibatch $D′$ of m examples from the training set $D$,  從小批量訓練 $D'$
2. compute $J(θ)$ on D′, 
3. update the parameters: $θ ← θ − η∂J/∂θ$ （計算這裡）
4. if stopping criteria are not met, jump to step 1 如果未能達到停止條件，請挑出步驟一
### Computing gradients: error back-propagation 誤差反向傳播
- Key: the chain rule: $\frac{\partial y}{\partial x} = \frac{\partial z}{\partial x} \frac{\partial y}{\partial z}$

[Open: Pasted image 20250202175507.png](PICTURE/Introduction%20to%20ANNs/82061d08773717ee1da59983f3db33a3_MD5.jpeg)
![](PICTURE/Introduction%20to%20ANNs/82061d08773717ee1da59983f3db33a3_MD5.jpeg)

$$
\frac{\partial J}{\partial y^{(2)}} = \frac{\partial J}{\partial y}
$$
$$
\frac{\partial J}{\partial z^{(2)}} = \frac{\partial J}{\partial y^{(2)}} \frac{\partial y^{(2)}}{\partial z^{(2)}} ; \quad \frac{\partial J}{\partial \mathbf{W}_2} = \frac{\partial J}{\partial z^{(2)}} \mathbf{y}^{(1)T} ; \quad \frac{\partial J}{\partial y^{(1)}} = \mathbf{W}_2^T \frac{\partial J}{\partial z^{(2)}}
$$
$$
\frac{\partial J}{\partial z^{(1)}} = \frac{\partial J}{\partial y^{(1)}} \frac{\partial y^{(1)}}{\partial z^{(1)}} ; \quad \frac{\partial J}{\partial \mathbf{W}_1} = \frac{\partial J}{\partial z^{(1)}} \mathbf{y}^{(0)T} ; \quad \frac{\partial J}{\partial y^{(0)}} = \mathbf{W}_1^T \frac{\partial J}{\partial z^{(1)}}
$$
$$
\frac{\partial J}{\partial \mathbf{x}} = \frac{\partial J}{\partial y^{(0)}}
$$

## Summary
Important parts of a neural network:
- Activation function
- Number of layers
- Training:
	- Loss function
	- Stochastic gradient descent



## Problem :



### 1. Spurious Correlations（虚假相关）



Neural networks excel at exploiting **statistical patterns** in data
- No device to distinguish between spurious and robust correlations 沒有設備可區分假相關性和穩健相關性
- With more training data, so the hope, robust correlations will prevail  希望穩健的相關性會佔上風
- However: Majority is not always right! 大多數並不總是對的

- **问题：** 神经网络擅长捕捉数据中的**统计模式**，但无法区分真正的因果关系和偶然的相关性。
- **示例：** 其中的问答任务展示了模型如何依赖数据中的表面模式来得出答案，而不是理解真正的逻辑关系。
- **与 Transformer 语言模型的关系：**
    - Transformer 模型也是**基于数据驱动的模式匹配**，它们可能会捕捉到虚假相关性。
    - 例如，GPT 可能会因为训练数据中的模式而误以为某个单词的出现一定与某个答案有关，即使它们在现实中无关。


### **2. Out-of-Distribution Generalisation（分布外泛化）**

- **问题：** 如果训练数据和测试数据的分布不同，神经网络很难泛化到新情况。If the training data is not representative of the application scenario, the patterns are different 訓練資料無法代表應用場景，模式就會不同
- **示例：** PPT 里提到的 “Super Bowl” 示例，原始数据可能支持一个答案（John Elway），但在对抗性修改后，模型的预测变得不可靠。 
- **与 Transformer 语言模型的关系：**
    - Transformer 语言模型依赖大量数据的统计模式，如果在训练数据中见过某种表达，它会在类似情况下给出相应答案。
    - 但如果输入的表达方式发生变化（即分布外数据，例如换了一种问法、换了命名方式），它可能会失败。
    - 这与 **Few-shot learning** 和 **Zero-shot learning** 相关：大多数 Transformer 需要大量训练数据来适应新任务，但对于完全没见过的情况，其表现可能不稳定。





### **3. Interpretability（可解释性）**

- **问题：** 神经网络的内部机制难以解释，我们不知道它到底学习到了哪些模式。
- **示例：** PPT 展示了一个简单的 “How many apples do I have?” 问题，模型错误地认为是一个“计数问题”，而没有真正理解句子含义。
- **与 Transformer 语言模型的关系：**
    - Transformer 语言模型是**黑盒模型**，我们无法直接理解它内部的权重如何影响决策。
    - 例如，BERT 可能会在阅读理解任务中做出正确的预测，但我们无法确定它是否真的“理解”了文本，还是仅仅利用了训练数据中的某些模式。
    - 近年来，很多研究都在尝试**解释 Transformer 内部的注意力机制**，但仍然没有清晰的答案。













