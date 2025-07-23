---
File: Data Science/Natural Language Processing NLP/Tokenisation.md
LINK:
  - "[[Natural Language Processing NLP]]"
  - "[[Text Mining]]"
  - "[[Data Science/Natural Language Processing NLP/Annotation Formats.md]]"
  - "[[Data Science/Natural Language Processing NLP/Sentence Segmentation 句子細分.md]]"
---

Why need Tokenisation
- 機器學習模型通常使用「單詞」作為特徵，例如詞頻統計、情感分析等。
- 英文單詞之間有空格，中文沒有，需要不同的處理方法。



Break sentence into tokens

3 main classes of tokens often considered

- Morphosyntactic word
- Punctuation mark or special symbol
- A number
- Endings of contractions, e.g., "'re" in "we're"
- Compounds and multi-words (e.g., daughter-in-law)


### Challenges:

- Character encoding 
	- ASCII only?
	- Unicode (UTF-8)
- ASCII-fication or romanisation of texts
	- Transliterations
- Results from OCR may be poor
	- Pre-processing to detect/correct errors 預處理
	- OCR errors may appear as correct text (but not intended text)



> [!attention] Challenging
> 
> - Hyphenation
> 	- Manchester-based
> 	- Sister-in-law
> - Telephone numbers: many different Formats
> 	- with whitespace, dots
> 	- slashes, hyphens, parentheses, plus signs
> 
>> [!example]+ 
>> - Dates: 04 January 2018; 04-01-2018, Jan 4, 2018
>> - Decimals: 0.05; 3.4; .6
>> - Monetary values: a £5-a-dish dinner
> 


## Split or not to split 
- Sentence segmentation (split)
- Tokenisation (split)
- Named entity recognition (combine)
In other words: tokenisation is knowing when to split (not when to combine)













