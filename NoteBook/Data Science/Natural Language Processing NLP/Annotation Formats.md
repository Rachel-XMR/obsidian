---
LINK:
  - "[[Natural Language Processing NLP]]"
  - "[[Text Mining]]"
  - "[[Data Science/Natural Language Processing NLP/Tokenisation 象征化.md]]"
File: Data Science/Text Mining/Annotation Formats.md
---

**Annotation（標註）** 是在文本中為每個 token 添加額外的信息，例如**詞性標註**（*Part-of-Speech Tagging, POS Tagging*）、**命名實體識別**（*Named Entity Recognition, NER*）等。




## Understanding documents
Documents rarely have a simple structure 很少有簡單結構
Documents are meant to be <font color="#ffc000">human-readable</font>

> [!example] 
> - news article
> - research article

 
# Annotations:






## Enabling machine-readablility
![](PICTURE/Annotation%20Formats/7d1b5a0b7c4e5839be878e737addcad1_MD5.jpeg)
![](PICTURE/Annotation%20Formats/238e557e0f22df25014bc279d43f59ee_MD5.jpeg)


![](PICTURE/Annotation%20Formats/40f8d04fe843998f78dd0efdf6bb66c0_MD5.jpeg)
![](PICTURE/Annotation%20Formats/875ad453c826788203008d9d15282031_MD5.jpeg)

如圖展示的 他從單純的文字變成機器可讀的樣式

## Types of annotation Formats
Boundary notation 邊界符號
Inline markup language elements 內聯標記語言元素
Stand-off
- delimiter-separated values (DSV)
- JSON






















## Part-od-Speech Tagging (POS Tagging) 詞性標註
 給每個單詞分配詞性標籤

> [!example] 
> ```python
> import nltk 
>nltk.download('averaged_perceptron_tagger') 
> sentence = "She runs fast." 
> tokens = word_tokenize(sentence) 
> pos_tags = nltk.pos_tag(tokens) 
> print(pos_tags) 
> # [('She', 'PRP'), ('runs', 'VBZ'), ('fast', 'RB')]
 > ```

### [The Penn Treebank Tagset](https://www.ling.upenn.edu/courses/Fall_2003/ling001/penn_treebank_pos.html)
![](PICTURE/Annotation%20Formats/9fce835cc3487173b9e5e3824b40cbf2_MD5.jpeg)

### [The Universal Scheme](https://universaldependencies.org/u/pos/all.html)
![](PICTURE/Annotation%20Formats/13aff618694491ddc63af7ced7587d41_MD5.jpeg)











## Named Entity Recpgnition (NER) 命名實體識別
**高度依賴上下文關係**

NER 用來識別文本中的**人名、地名、組織名**等專有名詞

**句子：**  
_"Apple is looking at buying U.K. startup for $1 billion."_

**NER 標註結果：**

1. "Apple" → ORG（組織）
2. "U.K." → GPE（地名）
3. "$1 billion" → MONEY（貨幣）

```python
import spacy 
nlp = spacy.load("en_core_web_sm") 
sentence = "Apple is looking at buying U.K. startup for $1 billion." 
doc = nlp(sentence) 

for ent in doc.ents: 
	print(ent.text, ent.label_) 
# Apple ORG 
# U.K. GPE
 # $1 billion MONEY
```

- The central question to understand a sentence:
		who did what to whom? (also where and when)
- NER: 識別指定的實體提到及其感興趣的類型

#### what is a named entity:
- A real world object (can be physical or abstract) that can be named
  - Person: Bill Gates, \[your name\]
  - Location: London, Mexico, \[your PoB\]
  - Time expression: 31/01/2020, \[your DoB\]
  - Monetary value: $15, \[your tuition fee\]
  - ...

- For a specific task/domain, we care only some entity types
  - News: person, location, organisation, monetary, ...
  - Biomedical: gene/protein, drug name, symptom, disease, ...

#### what is an entity mention
- An entity mention is a<span style="background:#fdbfff"> span of text 文本的跨度</span>(can be a single word or multiple words)
	![](PICTURE/Annotation%20Formats/1be5b55335d2173413c7873034266bba_MD5.jpeg)
- Nested entities
	![](PICTURE/Annotation%20Formats/bb2a2646c074fe3d87b5ed3b3dbca7c4_MD5.jpeg)





**高度依賴上下文關係**
![](PICTURE/Annotation%20Formats/bc52f711a833e030bb71ec5a476e886f_MD5.jpeg)
1. 實體歧義消除：
	- Washington可能是地名（華盛頓州/市），人名（喬治·華盛頓）或機構名，需要通過上下文（cities in USA）判斷其具體類型 
2. 縮寫與全稱關聯
	- - 如“Common Admission Test”缩写为“CAT”，但“CAT”单独出现时可能指动物（猫）、基因名称或其他术语，需上下文明确其指代。
3. 领域特定实体识别
    - 基因/蛋白质名称（如链接中的 UniProt 条目）需要结合生物医学文本的上下文，甚至依赖外部知识库才能准确识别。
4. 实体边界划分
	- 街道名（如“Main Street”）或复合人名（如“Mary Ann”）需通过上下文确定词汇组合是否构成完整实体。
5. **通用词汇的实体化**
    - 某些词在特定场景下可能成为实体（如“Java”可指编程语言或印尼岛屿），上下文是唯一区分依据。

**NER 的核心挑战在于如何利用上下文信息**，从表层文本中推断深层语义，而非孤立地识别词汇。图中的例子通过多类实体的对比，直观体现了上下文依赖的必要性。

Information extraction pipeline

![](PICTURE/Annotation%20Formats/792c0974e8d6e125089a97fc527764cf_MD5.jpeg)


#### Approaches to NER
- Dictionary lookup
- Rule-based methods


##### Machine learning-based methods

###### Classification
- Predicting tags:  $\text{probability}(\text{tag}|\text{token}) = \text{function } f$

- Local approach: tags are **independent** each other
  - Any classifiers for sequence can be used, e.g., RNN, LSTM, BiLSTM

- Global approach: tags are **dependent** each other
  - [Hidden Markov Model (HMM): 隱藏的馬爾可夫模型](Data%20Science/Natural%20Language%20Processing%20NLP/Sequence%20model.md#Hidden%20Markov%20Model%20(HMM)%20隱藏的馬爾可夫模型)
  - [Conditional Random Fields (CRFs)](Data%20Science/Natural%20Language%20Processing%20NLP/Sequence%20model.md#Conditional%20Random%20Fields%20(CRFs)) 隨機字段




####   Summary  

- NER is an important task in information extraction
- NER: need to detect correct entity mention and category
- NE categories are dependent on the downstream applications
- Three main approaches to NER




### Named entity linking (NEL)
Named entity linking (NEL) is the task of linking a mention to the corresponding
entity in a knowledge base (e.g., Wikipedia)

![](PICTURE/Annotation%20Formats/6170654f7efd1c831d2ef40e08d6e65e_MD5.jpeg)

### NEL is difficult

- A knowledge base can have a very large number of entities 大量實體
  - Wikipedia: 5 millions
  - Freebase: 44 millions
  - UMLS: 13 millions
- An entity can have very different surface forms 實體具有非常不同的表面形式
  - Donald Trump: Trump, President, Snowflake-in-Chief
- A surface form can be linked to several entities 表面形式可以鏈接到多個實體
  - Trump: Donald Trump, Ivanka Trump
- Knowledge base can’t cover all entities or forms of entities in texts 知識庫無法涵蓋文本中的所有實體或形式的實體

- import for nlp
![](PICTURE/Annotation%20Formats/8a1696e362ce821f9a755019ea42f147_MD5.jpeg)


- We can learn entity embeddings in a similar way we learn word embeddings
- Using **Wikipedia** for entity annotations實體注釋
  - We use pre-trained word embeddings (word2vec or glove) 使用預訓練的單詞嵌入
  - Learn entity embeddings using (entity, context) pairs from Wikipedia使用Wikipedia的學習實體嵌入
  - (We can jointly train entity embeddings and word embeddings)
https://wikipedia2vec.github.io/wikipedia2vec/
> ... but partially blames the **antitrust** litigation during the time...

### General approach

- Generate candidates 生產候選人
 * - Dictionary-based 基於字典
  - Rule-based 基於規則
  - Similarity 相似性
  - Information retrieval techniques, etc. 

- Rank candidates
  - Classification 分類
  - Neural-based 基於神經

![](PICTURE/Annotation%20Formats/75509fedb73c2b0c047586c584fab7f3_MD5.jpeg)



### Step 1: Candidate generation
- Extracting an entity-alias dictionary from Wikipedi 
	 ![](PICTURE/Annotation%20Formats/cec87e093e16a85b80bca6ee07741401_MD5.jpeg)
- An entity-alias dictionary gives us $Pr(entity=e| alias/mention=m)$: 
	 $Pr(e|m) = \frac{\text{count}(e, m)}{\sum_{e'} \text{count}(e', m)}$
- Selecting n (< 100) candidates by their Pr(entity|mention)
  ![](PICTURE/Annotation%20Formats/0a132768548a7fe1edd2ab4ab8c0c04e_MD5.jpeg)



### Step 2: Candidate ranking
- Learning to rank
	![](PICTURE/Annotation%20Formats/babe04bb22aeca0daf01a8aff041d43a_MD5.jpeg)
- Like NER, there are two approaches: local and global



### Local approach 
- For each mention $m$ in context $c$, we have a set $E$  of candidates $e_1, \ldots, e_{|E|})$
- We want the correct entity $e$ has the higher score among the candidates
  $text{score}(e|m, c) > \text{score}(e'|m, c) \text{ for all } e' \in E, e' \neq e$
- Using BiLSTM
![](PICTURE/Annotation%20Formats/60f21920c8abebbc79d773df33f36beb_MD5.jpeg)


### Global approach 
- Coherency hypothesis: entities appearing together in a document should be coherent. 在文檔中一起出現的實體應該是連貫的
	![](PICTURE/Annotation%20Formats/43d89ee7c7e317fde68f62f8c4119fa7_MD5.jpeg)
- $E = (e_1, \ldots, e_n), M = (m_1, \ldots, m_n), C = (c_1, \ldots, c_n)$
- Fully connected graph CRF (Ganea & Hofmann, 2017): Score function of **all entities at onces**


### Downstream applications 

- Information retrieval 信息檢索
  - Linking ambiguous entity mentions in query to improve the search results
- Content analysis 內容分析
  - Linking named entity mentions with a knowledge base across documents
- Question answering 問題回答
  - exploit the entity linking technique to predict the types of questions and candidate answers, and obtain promising results
- Knowledge base (KB) construction/completion 知識庫建設
  - Extract new facts/knowledge from texts, link them to existing KB

### Summary

- NEL is an important task in language understanding and useful for many downstream applications
- NEL is challenging
- Two main steps of NEL: candidate generation and ranking
- For candidate ranking, we can implement local or global approach using CRF and/or neural networks.





## Boundary Notation 
Done at the level of individual tokens 在單個token完成
How do we encode units of interest spanning several tokens
<span style="background:#fdbfff">BIO:  B=Begin  I=Inside  O=Outside</span>

> [!example] 
![](PICTURE/Annotation%20Formats/cf744d8fb3b8ce28a2fafdc77989c298_MD5.jpeg)

- Strengths
	- simple
- limitations
	- cannot handle hierarchical or structured annotations e.g., nested entities(NES) 嵌套實體, relations events

> [!example] Nested entities 
> 
> ![](PICTURE/Annotation%20Formats/0e2b147836c53694ebb0f343da45b599_MD5.jpeg)
> 
> 展示了Named Entity Recognition (NER) 命名實體識別的結果
>  - 是一種NLP技術，用來識別文本中的關鍵實體，比如**地名 (GPE)**，**組織 (Org)**, **人物 (Person)** 和 **事件 (Conflict_Attack)**  
> 	- GPE：
> 		- 國家或地區名稱
> 	- Org：
> 		- 機構或組織的名稱
> 	- Person：
> 		- 具體人名
> 	- Contact_Meet：
> 		- 這類標籤標識涉及會議或高級別會議
> 	- Conflict_Attack（衝突/攻擊, Conflict_Attack
> 		- 標識與戰爭或攻擊有關的事件
> 	- 關係標註（箭頭）
> 		- 表示某人參與了一場活動
> 		- Target (目標)
> 		- 標識某個實體是某個行動的目標
> 
> 
> 



## Inline markup language elements
By addition of markup tags within text
- HTML
- XML

> [!example] 
> ![](PICTURE/Annotation%20Formats/27f458b086a56bae386e7574e187abb7_MD5.jpeg)
> 
> ![](PICTURE/Annotation%20Formats/be4dee88da8aca76cac817831d410773_MD5.jpeg)

Strengths:
- can handle annotations which are hierarchical (e.g., nested NEs, trees) and structured (e.g., events) 可以處理分層的注釋 
Limitations:
- requires substantial processing with standard XML parsers 對標準XML處理器進行大量處理
- impossible to encode overlapping/intersecting annotations, e.g., second Iraqi city of Basra 無法編碼重疊/相交注釋

## Stand-off Annotations (JSON格式)
將標註信息與原始文本分離的標註方式，而不是將標註直接嵌入到文本內部。

## **為什麼使用 Stand-off Annotation？**

4. **避免污染原始數據**：原始文本保持不變，標註信息存儲在外部文件或數據結構中。
5. **允許多層次標註**：可以為相同文本提供多種標註（如詞性、語法結構、命名實體等），並獨立管理它們。
6. **便於版本控制**：標註數據和原始文本分開存儲，有助於管理不同版本的標註信息。
7. **支持長文本處理**：對於超大文本，標註信息存儲在索引數據結構中，提高效率。


> [!example]+
> ```text
> UK and US discuss the role of UN.
> ```
> 
> stand-off 標註文件
> ```JSON
> {
>     "text": "UK and US discuss the role of UN.",
>     "annotations": [
>         {
>             "id": "T1",
>             "type": "GPE",
>             "start": 0,
>             "end": 2,
>             "text": "UK"
>         },
>         {
>             "id": "T2",
>             "type": "GPE",
>             "start": 7,
>             "end": 9,
>             "text": "US"
>         },
>         {
>             "id": "T3",
>             "type": "ORG",
>             "start": 27,
>             "end": 29,
>             "text": "UN"
>         }
>     ]
> }
> ```
> 
> 

annotations are stored separately
requires a way to link between annotations and text
links annotations to text using indexing based on character offsets (computed over raw
text)


- strength:
	- original raw text is left untouched 原始文本未觸及
	- can handle structured and overlapping annotations 可以處理結構化和重疊的注釋
- limitations:
	- **not readily human-readable** 
























