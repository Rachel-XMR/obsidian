---
LINK:
  - "[[Text Mining]]"
  - "[[Natural Language Processing NLP]]"
  - "[[Data Science/Natural Language Processing NLP/Annotation Formats.md]]"
  - "[[Sequence processing with recurrent neural networks]]"
---


- Relax the independence assumption by arranging the output variables in a linear chain 通過在線性鏈中排列輸出變量來放鬆獨立性假設




## Hidden Markov Model (HMM): 隱藏的馬爾可夫模型
  - A sequence of input: $X = \{x_t\}_{t=1}^T$  輸入序列
  - A sequence of states: $Y = \{Y_t\}_{t=1}^T$  序列狀態
  - $y_t$ is only dependent on the previous state $y_{t-1}$ 取決於前一個
  - $x_t$ is only dependent on the current state $y_t$ 取決於當前- Joint distribution: $p (y, x) = \prod_{t=1}^{T} p (y_t|y_{t-1}) p (x_t|y_t)$

- 屬於生成模型，主要學習聯合概率分佈 $p (y, x)$，通過狀態轉移和觀測概率生產序列
- 虽然HMM可以用于序列标注（如词性标注），但其本质更偏向**序列生成与概率建模**，而非直接分类。



## Conditional Random Fields (CRFs)

- a discriminative sequence model for sequence labeling 序列標記的區分序列模型
- finds the **most probable label sequence** $y^*$ given an observation sequence $x$ 找到最可能的標籤序列y觀測序列x
- $y^* = \arg\max_y p (y|x)$ 
where $x$ consists of the sequence of tokens from input text 在哪裡x由輸入文本的令牌序列組成
- 属于**判别模型**，直接学习条件概率 p(y∣x)p(y∣x)，专注于输入序列到输出标签的映射。
- 常用于序列分类任务（如命名实体识别），因此更接近典型的**分类方法**。



### Linear-chain CRFs

Computation of probability
![](PICTURE/Sequence%20model/febf9cb6efb53e54c59afe70173c2284_MD5.jpeg)
Normalisation factor: to make sure the sum of probability is equal to 1



## **RNN/LSTM**：
    
-  作为神经网络模型，它们可以灵活处理序列分类（如情感分类）或序列生成任务（如机器翻译），具体取决于任务设计和输出层结构。




# Feature function

- Characterises the input
- ![](PICTURE/Sequence%20model/3bbbc3ac2163bbfb2ccf2ea8d5c57134_MD5.jpeg)
- Example: $y_{t-1} = O, y_t = B\text{-}PERSON, \text{1}^{\text{st}} \text{ letter of } x_t \text{ is uppercase}$

## Feature Types:
- Contextual 上下文
  - current word $w_o$
  - words around $w_o$ in \[-3, \ldots, +3\] window
   ![](PICTURE/Sequence%20model/a90cc9a159ee662d17fdf41ec1f963f4_MD5.jpeg)
- Part-of-speech tag (when available) 副本標籤
- Trigger words  觸發單詞
  - for person (Mr, Miss, Dr, PhD)
  - for location (city, street)
  - for organisation (Ltd., Co.)
- Length (in terms of number of tokens)
- Orthographic (binary and not mutually exclusive)
  - initial-caps, all-caps, lonely-initial 首寫大字母
  - all-digits contains-dots, punctuation-mark  所有數字
  - single-char, contains-hyphen, URL 單字符
  - roman-numeral 
	  ![](PICTURE/Sequence%20model/17c6240bf90675c338fe84ec55a0c45c_MD5.jpeg)
- Suffixes (length 1 to 4) 後綴
  - each component of the NE
  - whole NE
- Gazetteers
  - geographical locations 地理位置
  - first names, surnames
  - company names
  - many others
  - whole NE is in gazetteer?
  - any component of the NE appears in gazetteer?

The more useful features you incorporate, the more powerful your learner gets!

## Pros vs. Cons

- **Pros:**
  - Features are intuitive
  - It is easy to interpret and debug the model
  - High performance

- **Cons:**
  - Feature engineering → domain knowledge

**-> The solution is Neural Network**



## [recurrent neural networks復發性神經網絡](Data%20Science/Deep%20Learning/Deep%20Learning%20for%20NLP.md#Recurrent%20neural%20networks%20復發性神經網絡)







