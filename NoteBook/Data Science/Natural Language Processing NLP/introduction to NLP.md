---
LINK:
  - "[[Text Mining]]"
  - "[[Natural Language Processing NLP]]"
---


A research field focussed on creating software systems with knowledge about natural (human) language 研究重點是關於自認語言的知識


Interdisciplinary: makes use of theories from *Linguistics 語言學理論*, adopts an *Engineering* approach



Aimed at human-like understanding of language (but not yet there)


> [!tip] Contributing disciplines
Linguistics: formal models of language, linguistic knowledge
Computer Science: representations, efficient processing, state machines, parsing
algorithms, probabilistic models, dynamic programming, machine learning
Mathematics: formal automata theory, computational modelling
Psychology: psychologically plausible modelling of language use


## Many types of ambiguity歧義:
- Phonological 語音學
	- multiple interpretations due to how it sounds 有些音聽起來一樣 那麼在識別的時候會存在很多種解釋
- Lexical 詞匯
	- multiple interpretations due to a word having multiple senses 詞語的歧義，由於有的單詞本身帶有的意思多重導致的
- Syntactic 句法
	- due to a word having more than one possible part of speech 一個單詞有多個演講部分
	-  due to prepositional phrase attachment 介詞的附件
- Semantic 語義
	- multiple possible interpretations解釋 unless knowledge of the world is available


> [!danger] Two major approaches to NLP
> - Symbolic 象征
> 	- Rule- and dictionary-based systems 基於規則和字典系統
> 	- Captures linguistic knowledge in rules written by experts 補貨專家撰寫的規則中的語言知識
> - Statistical/Machine learning-based 
> 	- Data-driven 數據驅動
> 	- Use of large amounts of (labelled) textual data (文本數據) to train systems, **discover patterns**
> 
> Comparison
>
| Symbolic                                                                                                                          | Statistical/Machine learning                                                                                               |
|:----------------------------------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------|
| ✅&nbsp; Expert knowledge yields highly precise results 專業知識會產生高度精確的結果                                                      | ✅Can generalise well on unseen examples可以很好的概括在看不見的例子上                                                        |
| ❎**Shortage** of experts                                                                                                              | ❎Need **people for labelling**                                                                                                 |
| ❎Laborious rule writing, *dictionary preparation* | ❎Time consuming and laborious labelling 耗時且費力        |
| ❎ Domain adaptation problematic域適應性問題                                                                                              | ❎Must retrain for new domain必須重新訓練                                                                                               |
| ✅Results can be interpreted結果可以解釋                                                                                                       | ❎ Often cannot inspect/change models通常無法檢查/更改模型                                                                                  |
| ✅&nbsp; Good when labelled data is hard to obtain當很難獲得標記的數據時    | ✅ Good where dictionaries are unavailable |  



## NLP Pipelines
A ‘complete’ NLP system is usually a pipeline of components
Each component tackles a specific problem
![](PICTURE/introduction%20to%20NLP/f588106faba6d912b5e155643af0dd79_MD5.jpeg)

- [Sentence Segmentation 句子細分](Data%20Science/Natural%20Language%20Processing%20NLP/Sentence%20Segmentation%20句子細分.md)
- [Tokenisation 象征化](Data%20Science/Natural%20Language%20Processing%20NLP/Tokenisation%20象征化.md)
- Parsing
- Information


![](PICTURE/introduction%20to%20NLP/be96a21abd21e8c93a2bd2a563c27e53_MD5.jpg)


---

- Sentence segmentation (split)
- Tokenisation (split)
- Named entity recognition (combine)




Why is NLP challenging:
- Natural Language evolve:
	- new words appear constantly 
	- Syntactic rules are flexible 句法規則靈活
	- ambiguity (模糊性)  is inherent  固有的



Why Machine Learning for NLP 
- Traditional rule-based artificial intelligence (symbolic AI):  
	- requires expert knowledge to engineer the rules  需要專家知識來設計
	- not flexible to adapt in multiple languages, domains, applications 不能靈活低使用與多種語言
- Learning from data (machine learning) adapts:
	- to evolution: just learn from new data 從新數據中學習
	- to different applications: just learn with the appropriate target representation




