---
LINK:
  - "[[Text Mining]]"
  - "[[Natural Language Processing NLP]]"
---


# Main types of evaluation

[Performance evaluation 績效評估](##Performance%20evaluation%20績效評估)
- How well is a system doing against an ideal state (benchmark)? 系統對理想狀態的表現如何

[Adequacy evaluation](##Adequacy%20evaluation) 充分評估
- Is the system fit for purpose? Does it do what the user wants (within cost, time)? 該系統適合目的嗎？

[Diagnostic evaluation](##Diagnostic%20evaluation) 診斷評估
- Any side effects from recent updates? 最近更新有什麼副作用
- Use of test suites 使用測試套件


## Performance evaluation 績效評估

Often based on a **benchmark data set** 
Organised around a community challenge/shared task
- Specific task is **defined**
- [**Gold standard**](###Gold%20) data provided: training, development, test
Automated means for scoring submissions, whereby the following are compared:
- **response**: system-generated annotations/predictions
- **reference**: gold standard



### Gold Standard Data
Time-consuming and costly to produce 耗時且昂貴的生產
Requires annotation instructions (annotation guidelines) 
Annotations done by experts
- May need some training in linguistics可能需要一些語言培訓
- Multiple annotators need to label the same samples (a subset) 多個注釋需要標記同樣的樣本
Need to ensure that annotations are reliable需要確保注釋可靠
- Calculate [inter-annotator agreement](####Inter-annotator%20agreement%20(IAA)) 計算通道間協議
- There might be disagreements 可能存在分歧


#### Inter-annotator agreement (IAA): 

Scott's Pi

- \( P (e) \): different chance for different chance for different categories

註釋者對注釋有主觀解釋

Fleiss' Kappa

- multi- annotator generalisation of (Cohen's) Kappa and Scott's Pi

These would work if we can define negative cases; for some tasks this is not possible, e.g., NER

For such tasks, **F-score** is reported instead


##### Kappa coefficient

Takes individual bias into consideration: annotators have subjective interpretations of annotation guidelines

$$\kappa = \frac{P (a) - P (e)}{1 - P (e)}$$

$P (a) =  observed agreement$, proportion of times judges agreed 觀測到的協議，法官同意的次比例

$P (e) =  expected agreement$, proportion of times judges expected to agree by chance 預期協議， 預期偶然同意的次數的比例

Assume:

we have two annotators $A_1$ and $A_2$  我們有兩個注釋者
they are providing annotations for a binary classification task: does a sample belong to some class $c$? yes or no

> [!example]+
> ![](PICTURE/Evaluation/4b1fa91adcaf9f2f6301e66d0f6f461b_MD5.jpeg) 
> 
> $\begin{array}{l}
P (a) = P (A_1 = \text{yes}, A_2 = \text{yes}) + P (A_1 = \text{no}, A_2 = \text{no}) \\ 
\quad = \dfrac{31}{40} + \dfrac{6}{40} \\ 
\quad = 0.925
\end{array}
$
> 
> $\begin{array}{l}
P (e) = P (A_1 = \text{yes}) \cdot P (A_2 = \text{yes}) + P (A_1 = \text{no}) \cdot P (A_2 = \text{no}) \\ 
\quad = \left ( \dfrac{33}{40} \times \dfrac{32}{40} \right) + \left ( \dfrac{7}{40} \times \dfrac{8}{40} \right) \\ 
\quad = 0.695
\end{array}
$
> 



統計數據更準確的反應出我們的注釋的可靠性

###### Interpretation
- Landis and Koch, 1977
  - slight < 0.2 < fair < 0.4 < moderate < 0.6 < substantial < 0.8 < perfect
- Grove et al., 1981 (psychiatric community)
  - 0.6 < acceptable
- Krippendorff, 1980
  - 0.67 < tentative conclusions < 0.8 < definite conclusions
- Rietveld and van Hout, 1993
  - 0.4 < moderate < 0.6 < substantial < 0.8
- Green, 1997
  - low < 0.4 < fair/good < 0.75 < high



### Scoring
Applies to automated systems and IAA

Precision: fraction of annotated items that are correct
Recall: fraction of correct items that are annotated

Confusion matrix:

|                  | Correct            | Not correct       |
|------------------|--------------------|-------------------|
| Annotated        | True positive (TP) | False positive (FP) |
| Not annotated    | False negative (FN) | True negative (TN)  |
$Precision = TP / (TP+FP)$
$Recall = TP / (TP + FN)$




#### F-score (a.k.a. F-measure, F1-score)

- Weighted harmonic mean 加權諧波平均值

$F_{\beta} = \frac{(\beta^2 + 1) PR}{\beta^2 P + R}$

- Usually balanced F1 measure is used, where $\beta = 1$

$F1 = \frac{2PR}{P + R}$

- Harmonic mean is a more conservative average (truer picture) 更保守的平均值


#### 對於宏觀和微觀的平均值 ：

- Macro-averaging does not consider class imbalance; micro-averaging is less sensitive to imbalance
- Weighted average: average weighted by the number of true instances for each class 









## Adequacy evaluation
Evaluation as seen by users用戶看到的評估
- Can I carry out some task effectively and productively
- Context of use is critical

Direct comparison of systems difficult

Judging **external quality**: characteristics are interdependent
- sometimes one hurts another
- sometimes one helps another


| 特性           | 描述                                                                                                                   |
| ------------ | -------------------------------------------------------------------------------------------------------------------- |
| Adaptability | a system can be used, without modification, in new applications                                                      |
| Integrity    | prevention of unauthorized or improper assess to a program and data                                                  |
| Efficiency   | use of system resources                                                                                              |
| Robustness   | degree to which a system continues to function in the presence of invalid inputs                                     |
| Correctness  | the degree to which a system is free from faults in its specification, design and implementation 系統在規範，設計和實施中沒有故障的長度 |
| Reliability  | a mean time between failures                                                                                         |
| Usability    | how easy it is to learn and use a system                                                                             |
| Accuracy     | degree to which a system is free from error; how well it does the job                                                |


### Trade-offs between characteristics

![](PICTURE/Evaluation/54fbdb9f5e4f61fb1594034df701c043_MD5.jpeg)


## Diagnostic evaluation
Evaluation as seen by developers
Internal quality


| 特性                | 描述                                                                          |
| ----------------- | --------------------------------------------------------------------------- |
| Portability       | the extent you can modify a system to operate in a different environment    |
| Reusability       | the extent to which you can use parts of a system in other systems          |
| Maintainability   | the ease with which you can modify a software system                        |
| Testability       | the degree to which you can unit-test and system-test a system              |
| Flexibility       | the extent you can modify a system for uses other than originally specified |
| Understandability | the ease with which you comprehend a system (at a more general level)       |
| Readability       | the ease with which you can read and understand the source code of a system |


### Test suites

- For an NLP-based system, design and coverage of diagnostic test suites is hard
- Range of phenomena system expected to tackle is hard to anticipate

May emphasise idealised linguistic aspect, may be of reduced use in face of ungrammatical (real) text










