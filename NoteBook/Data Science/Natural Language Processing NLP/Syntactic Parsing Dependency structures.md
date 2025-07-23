---
aliases:
  - "Syntactic Parsing: Dependency structures"
---
- Syntactic ambiguity


## Dependencies 依賴性

In order to understand sentences, we cannot treat each word in isolation.
We need to determine what a word is attached or connected to

There are connections between tokens which form the structure of the sentence代幣之間有連接，形成句子結構
Formally speaking: dependency = connection 依賴關係 = 連接
	an asymmetric binary relation linking two lexical items (tokens): one is the head and the other is the dependent 連接兩個詞彙項目 (令牌) 的部隊稱二進制關係


### head 
- The head of the sentence is the main verb; its subject and object are dependents 主要動詞 
- For the rest of the tokens: check if a token is modifying something else
	- modified token: head
	- token that modifies (modifier): dependent

### Dependency structure
Sentence structure based on dependencies 基於依賴的句子結構
Analysis of dependency structure:
● looking for dependencies between token pairs 尋找令牌對之間的依賴關係
● drawing a link between two tokens and specifying a label: grammatical function 在兩個令牌之間繪製鏈接並制定標籤： 語法功能
![](PICTURE/Syntactic%20Parsing%20Dependency%20structures/74a1267a85f6cb40d0daa59726b7b946_MD5.jpeg)


#### Grammatical functions: Examples

[Universal dependency relations](https://universaldependencies.org/u/dep/)
![](PICTURE/Syntactic%20Parsing%20Dependency%20structures/e658e246522513b6f59f27f29b72d7cc_MD5.jpeg)
![](PICTURE/Syntactic%20Parsing%20Dependency%20structures/a819b3b643f106f55c06c6d9abd73a43_MD5.jpeg)


![](PICTURE/Syntactic%20Parsing%20Dependency%20structures/361eeb88d26a0a59327ed7feef83535a_MD5.jpeg)
Tokens + grammatical function


### Dependency graph

A directed graph $G$ with: 
- a set of nodes $V$
- a set of edges $E$
- with a linear precedence order on $V$

**Nodes** represent tokens (surface form, sometimes together with the POS tag)
**Edges** are labelled with relation type (grammatical functions)


### syntactic dependency parsing tree 法依存分析樹
![](PICTURE/Syntactic%20Parsing%20Dependency%20structures/950ce3491d896ee83ce8a48ac803c561_MD5.jpeg)

![](PICTURE/Syntactic%20Parsing%20Dependency%20structures/d9493f2b535dbb18f25d89be3f1d4e08_MD5.jpeg)


#### Machine-readable notation
![](PICTURE/Syntactic%20Parsing%20Dependency%20structures/f29a8caa3cec753fb808b7305536efac_MD5.jpeg)


## Phrase structure 
- Sentence structure based on phrases
- Phrase structure trees show:
	- groupings of words into phrases
	- hierarchical structure of phrases

### Types of phrases

- NP: noun phrase
- VP: verb phrase
- PP: prepositional phrase
- AdjP: adjective phrase
- AdvP: adverbial phrase

#### Context Free Grammars
Production rules
![](PICTURE/Syntactic%20Parsing%20Dependency%20structures/544b44e1b3d0abcc4472e6dc2bf6ce8b_MD5.jpeg)


## Analysis of Phrase Structure
- Step： 
	1. Label the syntactic category (POS) of each of the tokens 先給每個token 標記上句法類別POS ![](PICTURE/Syntactic%20Parsing%20Dependency%20structures/f2f058df54f5154202d6227dd79b81e3_MD5.jpeg)
	2.  There are two principal constituents--a noun phrase (NP) and a verb phrase (VP). Locate the boundary between the two 先找到兩個主要成分![](PICTURE/Syntactic%20Parsing%20Dependency%20structures/53dc60012d02cdc1495bc611fd731cfe_MD5.jpeg)
	3. : For each head noun/pronoun, verb, adjective, adverb and preposition, project a phrasal node: NP, VP, AdjP, AdvP, PP.![](PICTURE/Syntactic%20Parsing%20Dependency%20structures/3d1837533e260bb4fd9f41cab2e1bc4c_MD5.jpeg)
	4. Connect the remaining tokens to the nodes they belong to![](PICTURE/Syntactic%20Parsing%20Dependency%20structures/896a69db9924db488f36cd8ab6977b32_MD5.jpeg)
	5. Final tree![](PICTURE/Syntactic%20Parsing%20Dependency%20structures/031ebb8a5ceff64d30946f70f5ef65af_MD5.jpeg)

represent：

| Dependency structure                          | Phrase structure                                                        |
| --------------------------------------------- | ----------------------------------------------------------------------- |
| directed edges: head-dependent relations 依賴頭部 | non-terminal nodes: phrases (and their hierarchical structure) 非末端節點 短語 |
| edge labels邊緣標籤: grammatical functions 語法功能   | POS tags: syntactic categories                                          |
| POS tags: syntactic categories句法類別            |                                                                         |

### Dependency structures: Endocentric vs Exocentric Constructions

![](PICTURE/Syntactic%20Parsing%20Dependency%20structures/f27cb6827fd44887bf57c3bfbd82e6cb_MD5.jpeg)

| Construction | Head | Dependent        | Required? |
| ------------ | ---- | ---------------- | --------- |
| Exocentric   | verb | subject (sbj)    | yes       |
| Exocentric   | verb | object (obj)     | yes       |
| Endocentric  | verb | adverb (vmod)    | no        |
| Endocentric  | noun | adjective (nmod) | no        |


### Verb valency
Certain verbs require certain types of dependents
Valency: the number of arguments controlled by the predicate (verb)
![](PICTURE/Syntactic%20Parsing%20Dependency%20structures/cf75e7f158c56dc887e1ad0acc9c039d_MD5.jpeg)


### Predicate-argument Structures 謂詞

- Generalisation of the concept of verb valency 動詞價 
- Predicates can be any part of speech (not just verbs)
- Arguments are specified using an argument number
[Enju Parser](https://mynlp.is.s.u-tokyo.ac.jp/enju/)

> [!example]+
> The executive order by Trump caused confusion at airports and embassies 
> ![](PICTURE/Syntactic%20Parsing%20Dependency%20structures/b97d7f05b233809f9663cce2a5a02cb2_MD5.jpeg)









