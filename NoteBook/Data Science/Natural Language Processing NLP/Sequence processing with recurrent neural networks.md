---
aliases:
  - Sequence processing with recurrent neural networks
LINK:
  - "[[Text Mining]]"
  - "[[Natural Language Processing NLP]]"
  - "[[Deep Learning for NLP]]"
  - "[[Sequence model]]"
---
## POS tagging
![](PICTURE/Sequence%20processing%20with%20recurrent%20neural%20networks/13b03ae722920b0a1ecb18a036e60655_MD5.jpeg)



## NER
![](PICTURE/Sequence%20processing%20with%20recurrent%20neural%20networks/3f529be9b355c50b15e6f707fce9b24f_MD5.jpeg)


## Local approach using softmax 


- Predicting tags independently 建立預測標籤
- $P_{r}(tag|token)=softmax(Wh_{token}+b)$
	![](PICTURE/Sequence%20processing%20with%20recurrent%20neural%20networks/6b1a3078063d22698482dd8d43adb7bf_MD5.jpeg)
- Training a local model is to minimize negative log likelihood
	 $L(\theta) = \sum_{S \in D} \sum_{(tag, token) \in S} -\log Pr(tag|token)$



## Global approach

- predicting all tags at once 
	$Pr (tag_{1: n}|\text{token}_{1: n}) = \frac{\exp\{f (tag_{1: n}, \text{token}_{1: n})\}}{\sum_{tag'_{1: n} \in T} \exp\{f (tag'_{1: n}, \text{token}_{1: n})\}}$
- Training a local model is to minimize negative log likelihood
	$L (\theta) = \sum_{(tag_{1: n}, token_{1: n}) \in D} -\log Pr (tag_{1: n} | token_{1: n}; \theta)$
- Using linear-chain CRF
- The feature function can be replaced:
	![](PICTURE/Sequence%20processing%20with%20recurrent%20neural%20networks/201bf2baab23e4b1e70c8f959ab8484e_MD5.jpeg)


## Local vs global approaches
- For sequence labelling tasks, e.g., POS and NER, global approaches are better than local ones
- Why?
  - An I tag can only appear after an I or a B (never an O)
  - There are often more Os than Bs and Is, ...




## CRF vs. Neural networks

| CRF | Neural networks |
| --- | --- |
| Feature engineering | Do not need features |
| Do not need pre-trained vectors | Need pre-trained vectors from big language models |
| Models are roughly interpretable | Models use implicit features (created by hidden layers) → not easy to interpret |
| Perform well with datasets that have many NE categories (*) | Perform not so well with datasets that have many NE categories (*) |

(*) Note: NE categories refer to Named Entity categories.
















