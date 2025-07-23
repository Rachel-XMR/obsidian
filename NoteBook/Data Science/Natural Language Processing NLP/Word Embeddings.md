---
LINK:
  - "[[Natural Language Processing NLP]]"
  - "[[Text Mining]]"
  - "[[Data Science/Natural Language Processing NLP/Word Sense Disambiguation (WSD).md]]"
---


## Count-based Approach 

[Distributional Semantics 分佈語義](Data%20Science/Natural%20Language%20Processing%20NLP/Distributional%20Semantics%20分佈語義.md #Co-occurrence vectors: word-word matrixes)



[Co-occurrence vectors: word-word matrixes](Data%20Science/Natural%20Language%20Processing%20NLP/Distributional%20Semantics%20分佈語義.md#Co-occurrence%20vectors%20word-word%20matrixes)

[Open: Pasted image 20250202050626.png](PICTURE/Word%20Embeddings/247ee21bfdbf831d58c8301693f22412_MD5.jpeg)
![](PICTURE/Word%20Embeddings/247ee21bfdbf831d58c8301693f22412_MD5.jpeg)


### Term-document matrix: Document vectors
Two ways to extract information from the matrix:
1. Column-wise: a document is represented by a |V|-dim vector (V: vocabulary)
[Open: Pasted image 20250202050809.png](PICTURE/Word%20Embeddings/e765c37995b2b35616ba0f65fe26267e_MD5.jpeg)
![](PICTURE/Word%20Embeddings/e765c37995b2b35616ba0f65fe26267e_MD5.jpeg)
Widely used in information retrieval:
- find similar documents 查找類似的文件
	- Two documents that are similar will tend to have similar words
	- [Open: Pasted image 20250202050939.png](PICTURE/Word%20Embeddings/aaa8b9133985c6e3f384b321ff119b5f_MD5.jpeg)
		![](PICTURE/Word%20Embeddings/aaa8b9133985c6e3f384b321ff119b5f_MD5.jpeg)
- find documents close to a query 查找附近的查詢的文件
	- Consider a query as a document 
	- [Open: Pasted image 20250202051110.png](PICTURE/Word%20Embeddings/0ad6ea63a0e16a100d5e680de6420a6e_MD5.jpeg)
		![](PICTURE/Word%20Embeddings/0ad6ea63a0e16a100d5e680de6420a6e_MD5.jpeg)
2. Row-wise: a word is represented by a |D|-dim vector (D: document set
[Open: Pasted image 20250202051242.png](PICTURE/Word%20Embeddings/c125e8cbec4d37ac04e0d86936e68f02_MD5.jpeg)
![](PICTURE/Word%20Embeddings/c125e8cbec4d37ac04e0d86936e68f02_MD5.jpeg)


### Term-term matrix
we have seen it before (co-occurrence vectors): Count how many times a word u appearing with a word v
	[Open: Pasted image 20250202130458.png](PICTURE/Word%20Embeddings/4c7ead6a9f673d2b5790a896942749db_MD5.jpeg)
	![](PICTURE/Word%20Embeddings/4c7ead6a9f673d2b5790a896942749db_MD5.jpeg)
- raw frequency is bad 原始頻率不良
	- Not all contextual words are equally important: of, a, … vs. sugar, jam, fruit… 並非所有上下文單詞同樣重要
	- Which words are important, which ones are not?
		- infrequent words are more important than frequent ones (examples?
		- ) 不頻繁的單詞比常見單詞更重要
		- correlated words are more important than uncorrelated ones (examples?)
		- ...


→ weighing schemes (TF-IDF, PMI,...)


#### Weighing terms: TF-IDF (for term-document matrix）

- tf (frequency count):
$$
tf(t,d)=\log_{10}(1+count(t,d))
$$
- idf (inverse document frequency): popular terms (terms that appear in many documents) are down weighed
$$
idf(t,d)=\log_{10}\frac{N}{df(t)}
$$

- TF - IDF:
$$
tf - idf(t,d) = tf(t,d) *idf(t)
$$
[Open: Pasted image 20250202154211.png](PICTURE/Word%20Embeddings/9b566d97825414b4f1b64bbe43bf6f7e_MD5.jpeg)
	![](PICTURE/Word%20Embeddings/9b566d97825414b4f1b64bbe43bf6f7e_MD5.jpeg)
- Many word pairs should have > 0 counts, but their corresponding matrix entries are 0s because of lacking data (data sparsity)
→ Laplace smoothing: adding 1 to every entry (pseudocount)


![](PICTURE/Word%20Embeddings/e4e0a92a8c26f881482b1a3f9173c98c_MD5.jpg)

| Pros                                                                                                                                           | Cons                                                                                                                                                                |
| ---------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Simple and intuitive                                                                                                                           | Word/document vectors are sparse (dims are \|V\|, vocabulary size, or \|D\|, number of documents, often from 2k to 10k) → difficult for machine learning algorithms |
| Dimensions are meaningful (e.g., each dim is a document / a contextual word)<br><br>→ easy to debug and interpret (Think about Explainable AI) | How to represent word meaning in a specific context?                                                                                                                |
| (From sparse vectors to dense vectors)->                                                                                                       | Employ dimensionality reduction (e.g., latent semantic analysis - LSA)                                                                                              |
|                                                                                                                                                | Use a different approach: prediction (coming up next)                                                                                                               |



## Prediction-based Approach

[Introduction to ANNs](Data%20Science/Neural%20Networks%20神經網絡/Introduction%20to%20ANNs.md) used to learn word embeddings

- two major count-based approach methods: 
	- term-document matrix 術語文檔矩陣
	- term-term matrix 術語矩陣
- Raw frequency is bed
	- using weighing schemes to "correct" counts使用稱重方案
	- using smoothing to take into account "unseen" events使用平滑來考慮看不見的事件


### Formalisation
Assumptions:
● each word w ∈ V is represented by a vector v ∈ R d (d is often smaller than 3k)
● there is a mechanism to compute the probability Pr (w|u 1 , u 2 , ..., u l) of the event that a target word w appears in a context (u 1 , u 2 , ..., u l ).

Task: find a vector v for each word w such that those probabilities are as high as
possible for each w and its context (u 1 , u 2 , ..., u l ).

<font color="#ffc000">We use a neural network with parameters θ to compute the probability by minimizing the cross-entropy loss使用具有最小參數θ的神經網絡。透過最小化交叉熵損失來計算概率</font>

$L(\theta) = -\sum_{(w, u_1, \ldots, u_l) \in D_{\text{train}}} \log \Pr(w \mid u_1, \ldots, u_l)$



### Bengio 
[Open: Pasted image 20250202222835.png](PICTURE/Word%20Embeddings/d0dbae58c1f875db786a1eaf58cdf220_MD5.jpeg)
![](PICTURE/Word%20Embeddings/d0dbae58c1f875db786a1eaf58cdf220_MD5.jpeg)


### CBOW:
#### **CBOW 模型的工作原理**

1. **輸入 (Input Layer)**：
    
    - 給定一個目標詞 $w_t$ ​，選取其 **前 m 個詞** 和 **後 m 個詞** 作為**上下文詞 (context words)**。
    - 這些詞會從詞嵌入矩陣 CCC 中查找對應的詞向量。
2. **投影層 (Projection Layer)**
    
    - 將這些上下文詞對應的詞向量取平均： $y = \text{average}(w_{t-1}, ..., w_{t-m}, w_{t+1}, ..., w_{t+m})$
    - **這一步沒有非線性變換 (例如 ReLU 或 tanh)，只是簡單的平均**。
3. **輸出層 (Output Layer)**
    
    - 計算該平均向量 $y$ 與詞彙矩陣 $W$ 的線性變換，並使用 softmax 來預測中心詞 wtw_twt​： $P(w_t | w_{t-1}, ..., w_{t-m}, w_{t+1}, ..., w_{t+m}) = \text{softmax}(Wy)P(wt​∣wt−1​,...,wt−m​,wt+1​,...,wt+m​)=softmax(Wy)$
    - Softmax 的輸出是一個機率分佈，表示詞彙表 (vocabulary) 中每個詞作為中心詞的可能性。
#### **CBOW 的特點**
1. **上下文到目標詞**：它是**從上下文詞預測中心詞**（這與 Skip-gram 相反，Skip-gram 是用中心詞預測周圍的上下文詞）。
2. **計算高效**：由於使用**平均詞向量**，CBOW 計算速度通常比 Skip-gram 更快，尤其是在大語料庫上訓練時。
3. **適合大規模語料庫**：CBOW 在大語料庫下通常表現更穩定，適合訓練大詞彙的詞向量。

#### **CBOW 在 NLP 任務中的影響**

- **詞向量學習**：CBOW 提供了一種高效的方式來學習詞向量，後來影響了 **GloVe、FastText** 等模型的發展。
- **語意計算**：學到的詞向量可以用來計算詞語之間的語義相似性，例如**餘弦相似度 (cosine similarity)**。
- **下游應用**：CBOW 訓練出的詞向量可以應用於 **文本分類、情感分析、機器翻譯** 等 NLP 任務。

[Open: Pasted image 20250202222904.png](PICTURE/Word%20Embeddings/45154a534aec7773c5c73acc3433df04_MD5.jpeg)
![](PICTURE/Word%20Embeddings/45154a534aec7773c5c73acc3433df04_MD5.jpeg)


[Open: Pasted image 20250202222919.png](PICTURE/Word%20Embeddings/cfceca027b37f0a00096a81f12ff27f6_MD5.jpeg)
![](PICTURE/Word%20Embeddings/cfceca027b37f0a00096a81f12ff27f6_MD5.jpeg)





[Open: Pasted image 20250202222937.png](PICTURE/Word%20Embeddings/391ffe6a654bf73c9d119f804eaaec28_MD5.jpeg)
![](PICTURE/Word%20Embeddings/391ffe6a654bf73c9d119f804eaaec28_MD5.jpeg)
[Open: Pasted image 20250202223013.png](PICTURE/Word%20Embeddings/6fea3503ab0846f82e56faf1621b3729_MD5.jpeg)
![](PICTURE/Word%20Embeddings/6fea3503ab0846f82e56faf1621b3729_MD5.jpeg)




|      | CBOW        | Skip-gram            |
| ---- | ----------- | -------------------- |
| 目标   | 用上下文词预测中心词  | 用中心词预测上下文词           |
| 计算速度 | 快           | 慢（因为对每个中心词要预测多个上下文词） |
| 适用场景 | 大数据、大语料库    | 小数据、小语料库             |
| 效果   | 适合学习常见词的词向量 | 在低频词的词向量学习上更优        |






### word2vec

- Skip-gram model
- "a baby step in Deep Learning but a giant leap towards Natural Language Processing"
- can capture linear relational meanings (i.e., analogy):
	- king - man + women = queen


[Open: Pasted image 20250202223114.png](PICTURE/Word%20Embeddings/56802e40811a7a623bb40ec833e8d77d_MD5.jpeg)
![](PICTURE/Word%20Embeddings/56802e40811a7a623bb40ec833e8d77d_MD5.jpeg)



![](PICTURE/Word%20Embeddings/8ec24818433b17934e245d58652ec38e_MD5.jpeg)




#### Problems : biases (gender, ethnic, …)
- Word embeddings are learned from data → they also capture biases implicitly appearing in the data
- Gender bias:
	- "computer_programmer" is closer to "man" than "woman"
	- "homemaker" is closer to "woman" than "man"
- Ethnic bias:
	- African-American names are associated with unpleasant words (more than European-American names)
- …
→ Debiasing embeddings is a hot (and very needed) research topic



### Dealing with unknown words
- Many words are not in dictionaries
- New words are invented everyday
- Solution 1: using a special token #UNK # for all unknown words
- Solution 2: using characters/sub-words instead of words
	- Characters (c-o-m-p-u-t-e-r instead of computer)
	- Subwords (com-omp-mpu-put-ute-ter instead of computer)


### Word embeddings in a specific context
- The meaning of a word standing alone can be different than its meaning in a specific context
	- He lost all of his money when the bank failed.
	- He stood on the bank of Amstel river and thought about his future.
- Solution: w |c = f (w, c)
- Solution 1: f is continuous w.r.t. c (contextual embeddings, e.g., ELMO, BERT - next week)
- Solution 2: f is discrete w.r.t. c (e.g., word sense disambiguation - coming up in the next video)

### Summary
- Prediction-based approaches require neural network models, which are not
intuitive as count-based ones
- Low dimensional vectors (about 200-400 dimensions)
	- Dimensions are not easy to interpret
- Robust performance for NLP tasks



## **延伸：Word Embeddings 進化**

1. **靜態詞嵌入（Static Embeddings）**：
    
    - Word2Vec、GloVe、FastText
    - 缺點：一個詞的向量固定，不能根據不同上下文改變語義（如「bank」的不同意思）。
2. **上下文敏感的詞嵌入（Contextualized Embeddings）**：
    
    - ELMo、BERT、GPT
    - 解決了詞義多義性（Polysemy）問題，能夠根據上下文動態調整詞向量。





# Contextualised Word Embedding

## Static map 靜態地圖

f trained on large corpus Based on co-occurrence of words
![](PICTURE/Word%20Embeddings/0cab6a55dfa9943f52f309672de81a0c_MD5.jpeg)













