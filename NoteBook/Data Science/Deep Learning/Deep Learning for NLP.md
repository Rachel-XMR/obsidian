---
File: Data Science/Deep Learning/Deep Learning for NLP.md
LINK:
  - "[[Text Mining]]"
  - "[[Natural Language Processing NLP]]"
  - "[[Deep Learning]]"
  - "[[Data Science/Neural Networks 神經網絡/Neural Networks 神經網絡]]"
---

**Distributional representation + neural networks + SGD + backpropagation = Deep Learning**


## Data-driven approaches

![](PICTURE/Deep%20Learning%20for%20NLP/d5797f9dcc64670d821c864ab2b68bb4_MD5.jpeg)
Input: Sequence of tokens (text) Possible tasks: 
- Classify sequence 
- Label tokens 
- Generate another sequence 
- Extract token span from input

### Data

- For now, let’s not focus on how this representation is learned (we will take a closer look later)
- Simplifying assumption: assume we express an NLP task as a set of textual inputs and expected outputs →<font color="#ffc000"> a neural network will learn the underlying statistical patterns to succeed at the task 神经网络将学习在任务中取得成功的基本统计模式</font> (provided strong enough signal, representative training data, and much, much more)
- How do we represent NLP tasks as input/output pairs?






## Geometrical view
![](PICTURE/Deep%20Learning%20for%20NLP/16550a70cbc611e1a822beed35895fd6_MD5.jpeg)


**a neural network will learn the underlying statistical patterns to succeed at the task**




## NLP as time series analysis
Sequence = time series  
time series = data points, indexed in time order  
data points = words in text  
time order = order appearance in text  

We will be looking at:  
- Sequence classification  
- Sequence labelling  
- Sequence extraction  
- Sequence to Sequence translation

#### Sequence Classification

![](PICTURE/Deep%20Learning%20for%20NLP/b046d41384f4459eb4ec76c6700b1833_MD5.jpg)


Applicable NLP tasks: 
• Sentiment analysis 
• textual entailment 
• paraphrasing 
• question type classification


#### Span extraction

![](PICTURE/Deep%20Learning%20for%20NLP/c0359509a56434e68b4e1fdcc4765a8e_MD5.jpg)

Applicable NLP tasks: 
• Question Answering 
• Relation Extraction



#### Sequence labelling
![](PICTURE/Deep%20Learning%20for%20NLP/102ee311e9430e36bb7cbbb28d48e7f3_MD5.jpg)



Applicable NLP tasks:
• POS tagging
• Named Entity Recognition
• OpenIE, Semantic Role Labelling
• question type classification


#### Sequence to sequence

![](PICTURE/Deep%20Learning%20for%20NLP/74d5538db16cd600f2a36107aeba8199_MD5.jpg)

Applicable NLP tasks: 
• Translation 
• Abstractive Summarisation 
• Text generation 
• Question answering





### from words to numbers

![](PICTURE/Deep%20Learning%20for%20NLP/4450a7d846ff2b27e09652a1c191fd12_MD5.jpeg)

### Recurrent neural networks 復發性神經網絡
Sketch:
- Feed network token by token
- Use output of previous token as additional input when processing the current token



#### From NN to RNN 

![](PICTURE/Deep%20Learning%20for%20NLP/ee6b7f6dd041eb7eac4ae20590b90865_MD5.jpeg)



|      |                                             NN                                             |                                 RNN                                 |
| :--: | :----------------------------------------------------------------------------------------: | :-----------------------------------------------------------------: |
|  輸入  |                                     $x_t$ (當前時間步的輸入向量)                                     |                   $x_t$ 和 $h_{t−1}$ (上一個時間步的隱藏狀態)                   |
| 權重矩陣 |                                      $W$（連接輸入到隱藏層的權重）                                      | **新增權重矩陣 U：**<br>- $U$ 負責連接前一個時間步的隱藏狀態 $h_{t−1}$ 到當前時間步的隱藏狀態 $h_t$。 |
|  輸出  |                             隱藏狀態 $h_t$ 計算如下：$h_{t}=g(Wx_{t})$                              |              **隱藏狀態計算方式改變：**$h_{t}=g(Uh_{t−1}+Wx_{t})$              |
|      | 這表示普通的前饋神經網絡（Feedforward Neural Network, FNN），沒有時間依賴關係，每個輸入 $x_{t}$ 都獨立計算對應的隱藏層表示 $h_{t}$。 |       這表示 RNN 可以捕捉時間步之間的依賴關係，使其適用於序列數據，如自然語言處理 (NLP) 和時間序列預測。       |

![](PICTURE/Deep%20Learning%20for%20NLP/e9a338cb84de09c09f0c7513fa1d9682_MD5.jpeg)

![](PICTURE/Deep%20Learning%20for%20NLP/89c3411d12c9efa25a6f7021bf7d7afe_MD5.jpeg)


$\Delta W = -\eta \frac{\partial S}{\partial Y_{predict}} * \frac{\partial Y_{predict}}{\partial H_k} * \frac{\partial H_k}{\partial H_{k-1}} * \frac{\partial H_{k-1}}{\partial H_{k-2}} * \cdots * \frac{\partial H_2}{\partial H_1} * \frac{\partial H_1}{\partial W}$

$\frac{\partial H_k}{\partial H_{k-1}} = \tanh'(w_x x_k + w_h H_{k-1} + b) * w_h$

$S = (Y_{predict} - Y_{actual})^2$




#### RNN: Forward run 
![](PICTURE/Deep%20Learning%20for%20NLP/0477b23e7cbdba55360a88890398187a_MD5.jpeg)

**前向 RNN（h_f）：** 從 $x_1 \to x_2 \to x_3 \to x_4 \to x_5$

#### RNN: Backward run 
![](PICTURE/Deep%20Learning%20for%20NLP/869bdb2b725cdf9a7ef89d9419d4a382_MD5.jpeg)

**反向 RNN（h_b）：** 從 $x_5 \to x_4 \to x_3 \to x_2 \to x_1$
























### RNN: vanishing gradients
![](PICTURE/Deep%20Learning%20for%20NLP/0b969ec16bc3a272e4fbf9042a9b0525_MD5.jpeg)

依賴之前的時間步 即 $h_t$ ​ 取決於 $h_{t-1}$ 

***這樣的設計對於某些應用（如語言模型）是合理的，但對於**依賴完整上下文**的應用（如機器翻譯、命名實體識別等）可能會有局限性


### LSTM
![](PICTURE/Deep%20Learning%20for%20NLP/5c15eb93e4783c28dd3b667dba25130b_MD5.jpeg)





#### Context vector 
![](PICTURE/Deep%20Learning%20for%20NLP/822262f4dc7767fbf540d9e6530f28d4_MD5.jpeg)

- Context, or memory vector $C_t$ in addition to $h_t$
- Context information from "the past" calculations
- At any step $t$, LSTM learns how much of $h_t$ is to be "added" to $C_t$ and how much of $C_{t-1}$ is "kept"



![](PICTURE/Deep%20Learning%20for%20NLP/2e701b70b2e827b123cb3f9e12669f73_MD5.jpeg)



![](PICTURE/Deep%20Learning%20for%20NLP/acd32423e245c3f949845235a289085a_MD5.jpeg)




$\Delta W = -\eta \frac{\partial S}{\partial Y_{predict}} * \frac{\partial Y_{predict}}{\partial H_k} * \frac{\partial H_k}{\partial c_k} * \frac{\partial c_k}{\partial c_{k-1}} * \frac{\partial c_{k-1}}{\partial c_{k-2}} * \cdots * \frac{\partial c_2}{\partial c_1} * \frac{\partial c_1}{\partial W}$

![](PICTURE/Deep%20Learning%20for%20NLP/1f6ed127537fa4bc39146fa3517fb55e_MD5.jpeg)
這四個相加的結果 要麼落於0-1之間 要麼>1

如果這個系統是由0-1區間的數和大於一的數混合相乘組成則該係統會更加穩定，不同意出現梯度消失和爆炸的問題
![](PICTURE/Deep%20Learning%20for%20NLP/1e6ccb7c41b87822fcbff581e0bf118f_MD5.jpeg)






### GRU 
![](PICTURE/Deep%20Learning%20for%20NLP/eb88a34b4fcc73798be576240beea535_MD5.jpeg)

- Similar idea but less parameters 
- Similar performance to LSTM

Have vector representation of words that incorporate information from “the past” (left)
![](PICTURE/Deep%20Learning%20for%20NLP/879646d4fd191516256d6e4bc1e31000_MD5.jpeg)


### BiRNN: 雙向循環神經網絡, Bidirectional RNN
![](PICTURE/Deep%20Learning%20for%20NLP/6a7731e8939c7f80a2c3dd15cf417408_MD5.jpeg)


#### **BiRNN 與 RNN 的區別**

在前面的 RNN 圖片中，我們看到 RNN 只能從**左到右（past → future）**依賴之前的時間步（即 hth_tht​ 取決於 ht−1h_{t-1}ht−1​）。這樣的設計對於某些應用（如語言模型）是合理的，但對於**依賴完整上下文**的應用（如機器翻譯、命名實體識別等）可能會有局限性。

BiRNN **解決了這個問題**，它的核心思想是：

- **使用兩個 RNN：**
    - **前向 RNN（forward RNN）**：從左到右處理序列（即 past → future）。
    - **反向 RNN（backward RNN）**：從右到左處理序列（即 future → past）。
- **將兩個方向的隱藏狀態拼接 (concatenate) 在一起**，形成最終的隱藏狀態： $h_t = [h_{t_f}; h_{t_b}]$ 這裡 $h_{t_f}$ 是前向 RNN 的輸出，$h_{t_b}$ ​​ 是反向 RNN 的輸出。


#### BiLSTM：雙向長短期記憶網絡 

##### ELMo （Embeddings from Language Models）
![](PICTURE/Deep%20Learning%20for%20NLP/53832c6346c665ccc511d8208466d395_MD5.jpeg)

是一种基于双向LSTM（BiLSTM）的深度上下文词表示模型，其核心是通过**双向语言建模**学习词语的上下文相关嵌入。

### **1. ELMo的核心思想**

ELMo的目标是生成**上下文敏感的词向量**，即同一个词在不同语境中具有不同的表示（例如“bank”在“river bank”和“bank account”中含义不同）。  
为实现这一点，ELMo通过以下步骤训练：

1. **双向语言建模**：同时利用正向（从左到右）和反向（从右到左）的上下文预测当前词。
    
2. **多层BiLSTM结构**：通过堆叠多层BiLSTM捕捉不同层次的语义信息（如浅层语法特征、深层语义特征）。
    
3. **联合优化**：最大化正向和反向的联合对数似然（公式如下）：$O = \sum_{n=1}^{N} \left( \log P(x_n|x_1, \ldots, x_{n-1}) + \log P(x_n|x_{n+1}, \ldots, x_N) \right)$

###### **ELMo与BiLSTM的关系**

- **BiLSTM是ELMo的核心组件**：  
    ELMo使用多层BiLSTM作为编码器，每层BiLSTM分别处理正向和反向序列，并通过拼接或加权融合双向隐藏状态。
    
- **多层结构的作用**：
    
    - 浅层BiLSTM：捕捉局部语法特征（如词性、短语结构）。
        
    - 深层BiLSTM：捕捉全局语义特征（如指代消解、语义角色）。
        
- **动态词向量生成**：  
    ELMo最终输出是各层BiLSTM隐藏状态的加权组合，使词向量能够动态适应不同语境。

###### **ELMo的结构示例**



- **输入层**：词嵌入（如Word2Vec）。
    
- **BiLSTM层**：多个堆叠的BiLSTM，分别处理正向和反向序列。
    
- **输出层**：通过FFNN（前馈神经网络）和Softmax生成概率分布，预测当前词。
    
- **上下文示例**：
    
    - 句子：“He can speak fluent German.”
        
    - 预测“German”时，正向LSTM利用“speak fluent”，反向LSTM利用“He can”，综合双向信息提升准确性。



| 特性    | 传统BiLSTM     | ELMo              |
|-------|--------------|-------------------|
| 目标    | 特定任务（如分类、标注） | 预训练通用词表示          |
| 输出    | 最后一层隐藏状态     | 所有层隐藏状态的加权组合      |
| 应用方式  | 直接用于下游任务     | 作为特征输入下游模型（如BERT） |
| 上下文敏感 | 弱（静态词向量）     | 强（动态词向量）          |


![](PICTURE/Deep%20Learning%20for%20NLP/b38d212f5890f140569326c783669aa7_MD5.jpeg)


More expressive representations, because contextualised on current context as opposed to “static” word vectors that reflect







### Encoder/Decoder
![](PICTURE/Deep%20Learning%20for%20NLP/13a391071e58ade376fbc8107f52e6ba_MD5.jpeg)




























