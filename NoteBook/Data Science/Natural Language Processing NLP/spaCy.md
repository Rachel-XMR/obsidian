---
LINK:
  - ""
  - "[[Natural Language Processing NLP]]"
  - "[[Text Mining]]"
File: Data Science/Natural Language Processing NLP/spaCy.md
---
#python


![](PICTURE/spaCy/be96a21abd21e8c93a2bd2a563c27e53_MD5.jpg)

能夠比較兩個對象，並預測**它們的相似之處**
預測相似性對於構建推薦系統或標記重複項很有用。
計算相似性分數可能會有所幫助

在 **spaCy** 中，**相似性分數（similarity score）** 主要基於詞向量（word vectors），使用**餘弦相似度（cosine similarity）** 來衡量兩個詞、短語或句子之間的相似程度。以下是其計算原理和應用方式

**詞向量的餘弦相似度（cosine similarity）**:
$$
\text{cosine similarity} = \frac{\mathbf{A} \cdot \mathbf{B}}{\|\mathbf{A}|| \|\mathbf{B}||}
$$



<iframe width=80% height=500px src="https://spacy.io/usage/linguistic-features#sbd"> spaCy 開發文檔
</iframe>
https://spacy.io/usage/linguistic-features#sbd 



| Name                              | Description                                                                                                        |
|-----------------------------------|--------------------------------------------------------------------------------------------------------------------|
| Tokenization                      | Segmenting text into words, punctuations marks etc.                                                                |
| Part-of-speech (POS) Tagging      | Assigning word types to tokens, like verb or noun.                                                                 |
| Dependency Parsing                | Assigning syntactic dependency labels, describing the relations between individual tokens, like subject or object. |
| Lemmatization                     | Assigning the base forms of words. For example, the lemma of “was” is “be”, and the lemma of “rats” is “rat”.      |
| Sentence Boundary Detection (SBD) | Finding and segmenting individual sentences.                                                                       |
| Named Entity Recognition (NER)    | Labelling named “real-world” objects, like persons, companies or locations.                                        |
| Entity Linking (EL)               | Disambiguating textual entities to unique identifiers in a knowledge base.                                         |
| Similarity                        | Comparing words, text spans and documents and how similar they are to each other.                                  |
| Text Classification               | Assigning categories or labels to a whole document, or parts of a document.                                        |
| Rule-based Matching               | Finding sequences of tokens based on their texts and linguistic annotations, similar to regular expressions.       |
| Training                          | Updating and improving a statistical model’s predictions.                                                          |
| Serialization                     | Saving objects to files or byte strings.                                                                           |


處理過程：先將文本標記為單詞，標點符號














```python
import spacy

nlp = spacy.load("en_core_web_sm")  # 載入英文模型
text = "Apple is looking at buying U.K. startup for $1 billion."

doc = nlp(text) #doc物件會自動解析文本
```

### foundation

#### 1. Tokenization 分詞 第一步：將文本標記成為單詞，標點符號等
通過應用每種語言的規則來完成


```python
for token in doc:
    print(token.text)
```

> [!example]+
> ```python
> import spacy 
> nlp = spacy.load("en_core_web_sm")
> doc = nlp("Apple is looking at buying U.K. startup for $1 billion")
> for token in doc:
> 	print(token.text)
> ``` 
output:
![](PICTURE/spaCy/050f64f8f1c3ca3ae911bf001539fefe_MD5.jpeg)

spaCy can split **complex, nested tokens** like combinations of abbreviations and multiple punctuation marks
![](PICTURE/spaCy/86f3aa22db195c6229e034a2405fc110_MD5.jpeg)

> [!important]+ attribute：
> - **Text:** The original word text. 原始單詞
> - **Lemma:** The base form of the word. 單詞的基本形式
> - **POS:** The simple [UPOS](https://universaldependencies.org/u/pos/) part-of-speech tag. 言論的一部分標籤
> - **Tag:** The detailed part-of-speech tag. 詳細的語音標籤
> - **Dep:** Syntactic dependency, i.e. the relation between tokens. 句法依賴性
> - **Shape:** The word shape – capitalization, punctuation, digits. 單詞形狀
> - **is alpha:** Is the token an alpha character? 
> - **is stop:** Is the token part of a stop list, i.e. the most common words of the language? 
> 


npl.vocab 是詞彙表：使用預設詞彙表來進行標記化



#### 2. POS Tagging 詞性標註 

```python
for token in doc:
    print(token.text, token.pos_, token.dep_)
```

Even though a `Doc` is processed – e.g. split into individual words and annotated – it still holds **all information of the original text**, like whitespace characters. You can always get the offset of a token into the original string, or reconstruct the original by joining the tokens and their trailing whitespace. This way, you’ll never lose any information when processing text with spaCy. 即使處理了Doc，例如分為單個單詞並注釋，他任然包含原始文本的所有信息，例如空字符。

以做出整個語言概括的預測
spaCy **encodes all strings to hash values** to reduce memory usage and improve efficiency


#### Named Entity Recognition, NER 命名實體識別
可以**通過向模型進行預測來識別文檔中各種命名實體**。

```python
for ent in doc.ents:
    print(ent.text, ent.label_)
```





#### Dependency Parsing  依存關係解析


```python
for token in doc:
    print(token.text, token.dep_, token.head.text)
```

| nsubj    | 名詞性主語（nominal subject）          |
|----------|---------------------------------|
| dobj     | 直接賓語（direct object）             |
| iobj     | 間接賓語（indirect object）           |
| prep     | 介詞（preposition）                 |
| pobj     | 介詞賓語（prepositional object）      |
| aux      | 助動詞（auxiliary）                  |
| advmod   | 副詞修飾語（adverbial modifier）       |
| amod     | 形容詞修飾語（adjectival modifier）     |
| det      | 限定詞（determiner，如 "the", "a"）    |
| compound | 複合詞（compound word，如 "New York"） |
| punct    | 標點符號（punctuation）               |

##### 使用 `displacy` 可視化依存關係

```python
from spacy import displacy

doc = nlp("The quick brown fox jumps over the lazy dog.")
displacy.render(doc, style="dep", jupyter=True)
```

會顯示句子的依存樹，可視化詞語之間的語法關係。


##### 句法分析的應用

- **關鍵信息提取**：找出句子中的主語、謂語和賓語。
- **關係抽取**：確定不同詞之間的語法關係。
- **情感分析**：分析形容詞、副詞等修飾語如何影響句子情感。
- **機器翻譯**：理解詞與詞之間的關係，提升翻譯質量。
這些特性使 **spaCy 的句法分析** 在 NLP 任務（如信息提取、文本分類、問答系統等）中非常有用





#### Word Similarity 相似度分析
相似性通過比較單詞向量來確定


```python
word1 = nlp("dog")
word2 = nlp("cat")

print(word1.similarity(word2))  # 0.8（數值越接近 1，表示語義越相近）
```

> [!tip] 
> 需要使用 `en_core_web_md` 或 `en_core_web_lg`，因為 `en_core_web_sm` 沒有詞向量。

Similarity is determined by comparing **word vectors** or “word embeddings”, multi-dimensional meaning representations of a word. Word vectors can be generated using an algorithm like [word2vec](https://en.wikipedia.org/wiki/Word2vec) and usually look like this:  相似性是通過比較**單詞向量**或“詞嵌入”來確定的， 單詞的多維含義表示。單詞向量可以是 使用類似算法生成 [Word2Vec](https://en.wikipedia.org/wiki/Word2vec) ，通常看起來像這樣：









#### Custom Pipeline

```python
from spacy.tokens import Span

nlp = spacy.load("en_core_web_sm")
doc = nlp("ByteDance is an AI company.")

# 手動標註 ByteDance 為一個公司（ORG）
doc.ents = list(doc.ents) + [Span(doc, 0, 1, label="ORG")]

for ent in doc.ents:
    print(ent.text, ent.label_)
```





### Example

#### 使用 spaCy 處理 MongoDB 內的文本數據


```python
from pymongo import MongoClient
import spacy

nlp = spacy.load("en_core_web_sm")

# 連接 MongoDB
client = MongoClient("mongodb://localhost:27017/")
db = client["mydatabase"]
collection = db["mycollection"]

# 處理文本數據
for doc in collection.find({}, {"text": 1}):
    text = doc["text"]
    nlp_doc = nlp(text)
    for ent in nlp_doc.ents:
        print(ent.text, ent.label_)
```




#### 相似度 ： `doc1.similarity(doc2)`













