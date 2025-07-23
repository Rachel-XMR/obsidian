---
LINK:
  - "[[Data Science/Natural Language Processing NLP/Word Sense Disambiguation (WSD).md]]"
---

- Intuition直覺: choose the sense whose dictionary gloss词典词汇 or definition shares the most words with the target word’s neighborhood  選擇其字典光澤或定義於目標詞的鄰居共享最多單詞的感覺
- Formalisation 
	- Target word: $w$
	- Context words of w: $w_j$
	- Lexicon definition of senses: $D(.)$
	- Set of senses of a word: $S(.)$
- The rule:
	- $$
s_{optimised} = \arg\max_{s_k \in S (w)} \left ( sim (D (s_k), \bigcup_{w_j \in C} \bigcup_{s_i \in S (w_j)} D (s_i)) \right)
$$
- Possible similarity measures 相似性度量
	- $sim(X, Y) = 2 \frac{|X \cap Y|}{|X| + |Y|}$
	- $sim(X, Y) = 2 \frac{|X \cap Y|}{|X \cup Y|}$
	- $sim(X, Y) = 2 \frac{|X \cap Y|}{\sqrt{|X||Y|}}$
	- $sim(X, Y) = |X \cap Y|$



> [!example] 
> 
> Input sentence: Waves were hitting the steep bank.
Senses for bank:
>   1. sloping land (especially the slope beside a body of water)
>  2. a financial institution that accepts deposits and moves the money into lending activities
> 3. a building in which the business of banking transacted
> 
> #### Context definitions:
> -  wave – one of a series of ridges that moves across the surface of a liquid (especially
across a large body of water)
> -  hit – hit against; come into sudden contact with
> - steep – of a slope; set at a high angle
> 
> $$
> sim_1 = |\text{body, water, slope}| = 3, \quad sim_2 = |\text{moves}| = 1, \quad sim_3 = |\varnothing| = 0
$$


| Pros                    | Cons                                      |     |
| :---------------------- | :---------------------------------------- | --- |
| Simple to implement     | not all words have definitions in WordNet |     |
| No training data needed | need to deal with ambiguous context words |     |
|                         | poor performance                          |     |

