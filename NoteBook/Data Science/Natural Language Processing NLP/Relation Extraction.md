---
LINK:
  - "[[Natural Language Processing NLP]]"
  - "[[Text Mining]]"
---
通常分為兩個子任務
- Subtask 1：關係檢測 (Relation Detection) --判斷兩個實體之間是否存在關係
- Subtask 2：關係分類 (Relation Classification) --在已確定有關係的前提下，進一步分類具體的關係類型   是一個多分類任務 (Multi-class Classification Task)
	- 給定一對實體，確定它們之間的具體關係類別 (如“出生地”，“所屬公司”)
	- 一些方法會聯合學習Subtask 1，並包括no_relation類（表示兩者沒有關係） 



## Relationship types: Predefined


## Approaches:

- [Patten-based](###Patten-based)
- [Statistical/machine learning-based](###Statistical/machine%20learning-based)





### Patten-based 
Using regular expressions (regexes) 使用正則表達式（REGEXES）
Two options:

- Relaxing the pattern (to skip certain words)
- Expand the set of patterns (while keeping precision) using bootstrapping


#### 1. Bootstrapping 介绍
Bootstrapping 是一种迭代的关系抽取方法，它通过 **少量的种子（Seed Tuples/Patterns）** 逐步扩展数据集，从文本中发现更多的 **实体关系（Tuples）**，同时学习新的 **关系模式（Patterns）**，不断循环优化。

它的基本思想是：

1. **使用少量人工标注的种子（Seed Tuples 或 Seed Patterns）。**
2. **基于种子搜索新的实例（Tuples）。**
3. **利用新的实例提取更多模式（Patterns）。**
4. **用这些新模式寻找更多的关系实例（Tuples），不断循环，扩大数据集**




#### **2. 关系抽取过程解析**
![](PICTURE/Relation%20Extraction/742bb023b626abea946225cdeb7a2ab4_MD5.jpeg)
从图中可以看到，整个过程是一个闭环的 **迭代流程**，包括以下几个关键步骤：

##### **(1) 初始种子（Seed Tuples/Patterns）**
- 开始时，我们提供一组**种子元组（Seed Tuples）**，例如：  
    _("Barack Obama", "was born in", "Hawaii")_  
    这个元组表示 "Barack Obama" 和 "Hawaii" 之间存在 "出生地" 关系。
- 也可以使用 **种子模式（Seed Patterns）**，例如：  
    _"[X] was born in [Y]"_
这些种子用来初始化关系抽取系统。

##### **(2) 元组搜索（Tuple Search）**
- 在大规模文本数据中，**搜索符合种子模式的实例**，即找到满足已知关系的更多实体对（Tuples）。
- 例如，如果我们使用种子模式 _"[X] was born in [Y]"_，我们可能会找到：
    - _("Albert Einstein", "was born in", "Germany")_
    - _("Isaac Newton", "was born in", "England")_

##### **(3) 模式提取（Pattern Extraction）**
- 从新的元组中**抽取新的模式**。  
    例如，我们发现：
    - _"X, a native of Y,"_ 也可以表达 "出生地" 关系。
    - _"X was raised in Y."_ 也可能提供相关信息。
- 这些模式将被存储到 **模式集合（Pattern Set）** 中。

##### **(4) 模式搜索（Pattern Search）**
- 用新的模式去文本中搜索更多的元组（Tuples）。
- 例如，如果我们提取到了 _"X, a native of Y,"_ 这个新模式，我们可能会找到：
    - _("Leonardo da Vinci", "a native of", "Italy")_
    - _("Marie Curie", "a native of", "Poland")_

这些新元组被加入 **元组集合（Tuple Set）**。

##### **(5) 迭代循环（Iterative Expansion）**
- 继续迭代这个过程，每次都用新的元组**生成更多模式**，用新的模式**搜索更多元组**，直到收敛或满足某个停止条件（如达到数据规模上限）。


#### 3. Bootstrapping 的优缺点

| 優點                                | 缺點                                                   |
| --------------------------------- | ---------------------------------------------------- |
| 半监督学习：只需要少量种子数据即可启动，大量减少人工标注成本。   | 错误传播（Error Propagation）：如果错误的模式或元组被引入，可能会在后续迭代中扩大错误。 |
| 自适应扩展：能自动发现新的关系和模式，提升覆盖率。         | 模式质量不稳定：提取的模式可能过于泛化或过于具体，导致噪声数据增加。                   |
| 高效的文本信息提取：能够从大规模无标注文本中抽取结构化的关系数据。 | 需要良好的初始种子：种子选择会极大影响最终结果，质量不佳的种子可能导致不理想的关系抽取。         |

- Bootstrapping 是一种 **半监督迭代学习方法**，用于关系抽取。
- 通过 **种子元组（Seed Tuples）和模式（Patterns）** 不断扩展数据集。
- 包括 **元组搜索（Tuple Search）、模式提取（Pattern Extraction）、模式搜索（Pattern Search）** 等关键步骤。
- 优势在于 **自动化、扩展性强**，但存在 **错误传播、噪声问题**。
- 在 **信息抽取、知识图谱构建** 等 NLP 任务中有重要应用。




### Statistical/machine learning-based 



#### Feature Types：
1. 命名实体特征（Named Entity Features）
	- **实体类型（Entity Type）**：例如，"Barack Obama" 被标注为 **Person（人名）**，"USA" 被标注为 **Location（地点）**。如果实体类型是 **(Person, Location)**，那么 "出生地" 关系更可能出现。
	- **中心词（Head Word）**：指的是与实体最紧密相关的主要词。例如，在 **"Apple CEO Tim Cook"** 中，"CEO" 是 **Tim Cook** 的中心词，可以帮助关系分类。
2. 语境特征（Context Features）
	- **实体之间的单词（Words Between）**：
	    - 例如，"Barack Obama was born in Hawaii" 中，"was born in" 是两个实体之间的上下文信息，明显表明 "出生地" 关系。
	- **第一个实体前的单词（Words Before the First Entity）**：
	    - 例如，"Former president Barack Obama was born in Hawaii"，"Former president" 提供了额外的背景信息。
	- **第二个实体后的单词（Words After the Second Entity）**：
	    - 例如，"Barack Obama was born in Hawaii, a U.S. state"，后续的 "a U.S. state" 可能提供额外的辅助信息。
机器学习模型会使用一个 **固定窗口（fixed window）**，只考虑上下文中的一部分单词，防止噪声干扰。
3. 句法结构特征（Syntactic Structure）
	- **依存路径（Dependency Paths）**：
	    - 依存句法（Dependency Parsing）可以表示句子中的语法结构。例如：
	        - 句子："Barack Obama was born in Hawaii."
	        - 依存路径："Obama → born → Hawaii"
	    - 这个依存路径表明 "Obama" 和 "Hawaii" 通过动词 "born" 连接，表明 **出生地关系**。
	**依存路径的作用**：
	- 提取出 **核心关系路径**，忽略不相关的单词，提高模型分类的准确性。
	- 例如：
	    - **正确路径**："Obama → born → Hawaii"
	    - **错误路径**："Obama → president → Hawaii"（"president" 不是核心动词）


#### 機器學習模型的使用
在机器学习方法中，这些特征会作为输入，供不同的分类器使用，例如：

- **传统机器学习方法**：
    - **SVM（支持向量机）**
    - **决策树（Decision Tree）**
    - **随机森林（Random Forest）**
- **深度学习方法**：
    - **RNN（循环神经网络）** 处理序列数据
    - **CNN（卷积神经网络）** 处理局部特征
    - **BERT（基于 Transformer）** 提取语义关系

这些模型通过 **学习实体、上下文和句法特征之间的关联**，进行准确的关系分类。


#### 关系分类的实际应用
关系分类是 **信息抽取（Information Extraction）** 和 **知识图谱构建（Knowledge Graph Construction）** 任务的重要组成部分，广泛应用于：

- **问答系统（QA Systems）**：识别 "Who is the CEO of Apple?" 这类问题中的关系。
- **搜索引擎（Search Engines）**：自动理解网页中的实体关系，提升搜索结果的相关性。
- **医学信息提取（Biomedical Relation Extraction）**：自动从医学论文中提取 **"疾病-症状"、"药物-副作用"** 关系。



#### Dependency path

![](PICTURE/Relation%20Extraction/c5cb485b6931ff7877fc134d9ada4902_MD5.jpeg)





























































