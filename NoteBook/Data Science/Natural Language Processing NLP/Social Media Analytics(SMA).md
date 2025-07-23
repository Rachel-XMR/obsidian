---
LINK:
  - "[[Text Mining]]"
  - "[[Natural Language Processing NLP]]"
---
Social Media: a channel for people to express their thoughts, beliefs and opinions 人表達自己的思想，信念和觀點的渠道

- highly subjective 高主觀
- individually, cannot be taken as facts 單獨地將事實視為事實
- but can provide insight if information is aggregated

Social Media Analytics

Computational analysis of information made available in online data-sharing platforms

## Types of data

### Structured data

- user profile information
  - age
  - gender
  - location
- interactions
  - number of posts
  - number of replies (retweets, likes)
  - number of followers

### Unstructured data: the actual text 實際文本

- can be short, often are incomplete sentences
- noisy
  - intentional misspellings ("very tiiiiired", "hellooooo!")
  - acronyms ("AFAIK", "BFF")
  - slang ("woke")
  - code-mixing: combining different languages
  - URLs, hashtags, user mentions, emojis


#### Sentiment Analysis/Emotion Detection

![](PICTURE/Social%20Media%20Analytics(SMA)/052af367a04d8af2aa3a6c09ab8a6b9f_MD5.jpeg)

給定一段文字，它包含任何情感嗎？
	如果是： 是正面還是負面？
	可能得標籤：中性，正面，負面

Approaches:
	Lexicon/dictionary-based + rules
	Machine learning-based

##### Sentiment Analysis using Dictionaries
![](PICTURE/Social%20Media%20Analytics(SMA)/848c9ccab16a1db4e8824cb76f45c714_MD5.jpeg)
通過匹配單詞來計算情感得分

##### Sentiment Analysis using Machine Learning
![](PICTURE/Social%20Media%20Analytics(SMA)/6db69b8a8699d5bc5ebbb8f5644601fb_MD5.jpeg)

##### Emotion Detection
Bears similarities to Sentiment Analysis but finer-grained; cast as a multi-class classification task Plutchik's wheel
![](PICTURE/Social%20Media%20Analytics(SMA)/3184380f6f7d9458d2c1292dbd2e8459_MD5.jpeg)










#### Topic Modelling
Finding hidden topics--represented as a group of words--in a corpus of documents Based on Latent Dirichlet Allocation (LDA) by Blei and Jordan, 2003

##### Latent Dirichlet Allocation (LDA)

an unsupervised approach 無監督方法
a generative statistical model that produces words associated with a topic 與主題相關的單詞的生成統計模型
Given that observed data = words in documents 
● each document is a mixture of topics 每個文檔都是主題的混合
● the presence of each word is attributable to at least one of the topics 每個單詞的存在至少歸因於其中之一
number of topics k often needs to be pre-defined

![](PICTURE/Social%20Media%20Analytics(SMA)/f905b1885ca287fe2c732416992356d5_MD5.jpeg)


#### Ethical Considerations 道德考慮


At different stages
- Data collection
- Data analysis
- Data dissemination/publication


##### Data Collection

##### Data Analysis

##### Data Dissemination





































