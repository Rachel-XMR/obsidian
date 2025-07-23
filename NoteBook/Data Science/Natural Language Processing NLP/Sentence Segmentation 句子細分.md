---
LINK:
  - "[[Natural Language Processing NLP]]"
  - "[[Text Mining]]"
File: Data Science/Natural Language Processing NLP/Sentence Segmentation 句子細分.md
---

 Sentence Detection is done before the text is tokenized 句子檢測在文本標記化之前進行
 

Task 順序：
- Determination of boundaries between sentences確定句子之間的界限
- Sentences used in subsequent NLP tasks 隨後NLP中使用的句子
- Is it enough to detect the full stop
	- Could be an end-of-sentence (EOS) marker 可能是句子結束 (EOS) 標記
	- Or an end of abbreviation marker 縮寫標記的結尾
	- Or both

通常是Text Mining的第一步，因為它將非結構化文本拆分成基本處理單位


Variation in delimiters 
- Typical：".","!","?"


> [!todo] # Approaches
> 
> - Regular expressions (Patterns) 正則表達式
> - Dictionaries (e.g., abbreviation lists) 字典
> - Hand-crafted rules,  手工製作的規則(e.g.to check whether the word following an EOS delimiter starts with an uppercase character 檢查EOS界定符之後的單詞是否從大寫字符開始) 
> - Statistical and ML approaches
> - Hybrid approaches 混合方法
> 
> 



### Example of useful rules or Features
First character after potential EOS char 潛在EOS Char之後的第一個字符
● Should be uppercase? Problematic for some languages, e.g. German 
● Permissible chars after potential EOS, e.g. lowercase characters?
Abbreviations 縮寫
● titles not likely to occur at EOS (e.g., Dr. Jones)
● company indicators could occur at EOS (e.g., MySocialMedia Inc.)




###  [OpenNLP](Data%20Science/Natural%20Language%20Processing%20NLP/OpenNLP.md)



 The OpenNLP Sentence Detector cannot identify sentence boundaries based on the contents of the sentence 無法根據內容識別句子邊界

<iframe width=80% height=500px src="https://opennlp.apache.org/docs/1.5.3/manual/opennlp.html#tools.sentdetect.detection"> OpenNLP 開發文檔
</iframe>

輸出的是一個個string 每個string都是一個分解出來的句子





### [spaCy](Data%20Science/Natural%20Language%20Processing%20NLP/spaCy.md)
for pdf and word docs



<iframe width=80% height=500px src="https://spacy.io/usage/linguistic-features#sbd"> spaCy 開發文檔
</iframe>












