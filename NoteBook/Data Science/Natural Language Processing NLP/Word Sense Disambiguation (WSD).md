---
LINK:
  - "[[Natural Language Processing NLP]]"
  - "[[Text Mining]]"
  - "[[Data Science/Natural Language Processing NLP/Word Embeddings.md]]"
File: Data Science/Natural Language Processing NLP/Word senses.md
---


## Word senses

- We assumed each word has one meaning / sense
- In fact, a word can have several senses 實際上一個詞有很多種感官
	- ![](PICTURE/Word%20Sense%20Disambiguation%20(WSD)/bc59ab4f174bddd130d2db174633e7b0_MD5.jpeg)
- How to define word senses? WordNet
- How to predict word senses? Knowledge-based and supervised learning-based methods


## WordNet A Database of Lexical Relations

- Example:
	- The noun “bass” has 8 senses in WordNet. 
		1. $bass^1$ - (the lowest part of the musical range) 
		2. $bass^2$, $bass \ part^1$ - (the lowest part in polyphonic music) 
		3. $bass^3$, $basso^1$ - (an adult male singer with the lowest voice) 
		4. $sea\  bass^1$, $bass^4$ - (the lean flesh of a saltwater fish of the famliy Serranidae)
		5. $freshwater\ bass^1$, $bass^5$ - (any of various North American freshwater fish with  lean flesh (especially of the genus Macropterus)) 
		6. $bass^6$, $bass voice^1$, $basso^2$ - (the lowest adult male singing voice) 
		7. $bass^7$ - (the member with the lowest range of a family of musical instruments) 
		8. $bass^8$ - (nontechnical name for any of numerous edible marine and  freshwater spiny-finned fishes) 
	- supersenses
		- ![](PICTURE/Word%20Sense%20Disambiguation%20(WSD)/2f5f341f931fe242160f7466efe4d3d2_MD5.jpeg)
	-  sense relations
		- ![](PICTURE/Word%20Sense%20Disambiguation%20(WSD)/7bcf8c117d24a514f093b2d6e430b609_MD5.jpeg)
![](PICTURE/Word%20Sense%20Disambiguation%20(WSD)/e6ebc448e8d0f97b1112cd9b51496949_MD5.jpeg)



## Approaches

Task definition
- Input:
	- Word in a context
	- A fixed inventory of potential word senses
- Output:
	- The correct word sense in context 上下文中正確的單詞感
- Two main types:
	- Lexical sample task 
	- All-words tasks: similar to part-of-speech tagging


### Lesk algorithm (Lesk, 1986): WSD baseline


![![Data Science/Natural Language Processing NLP/Lesk algorithm.md]]

### Supervised learning:


#### all-word WSD
![](PICTURE/Word%20Sense%20Disambiguation%20(WSD)/d75c40566c2a729e468ac02a0043e834_MD5.jpeg)

https://www.kaggle.com/nltkdata/semcor-corpus
https://wordnet.princeton.edu/download?s=DEMO


**基於已標註的語料庫，直接對句子中所有單詞進行詞義消歧**
##### 核心特點：
全詞消歧


#### Feature-based WSD
- Using SVM with several features
	- Part-of-speech tags
	- Collocation features of words and n-grams
	- Weighted average of word embeddings (of all words in a window)
![](PICTURE/Word%20Sense%20Disambiguation%20(WSD)/0c69a4b7f8716ddf1288bec6e13a87ba_MD5.jpeg)

**使用特征工程（詞性標籤，共現特征，詞嵌入加權平均）和機器學習模型進行消歧**




# Summary
- WordNet is a large database of lexical relations for English 
- WSD is the task of determining the correct sense of a word in context. 確定上下文中單詞正確感的任務
- SemCor is the **largest** corpus with *WordNet-labeled* senses 
- Lesk algorithm, a WSD baseline, is a knowledge-based approach 基於知識的方法
- Feature-based algorithms using parts of speech and embeddings of words in the context of the target word work well.










































