---
LINK:
  - ""
  - "[[cognitive robotics]]"
File: Computer Science/cognitive robotics/未命名.md
---


計算機和機器人可以很容易地預先變成來記住字典，但無法理解它們使用的語言



Robots, Language & Cognition 






學習與發展：
機器人可以很容易地預先變成來記住字典，但無法完全理解他們使用的語言



![](PICTURE/intro/81246ba4421352088096f60e607896a2_MD5.jpeg)

認知機器人技術是將人工智能以及認知和生物科學的見解和方法融入機器人技術的領域和融入機器人技術的領域




### Terminology 術語

- Cognitive Robotics 認知機器人
	智能機器人的感覺運動和認知能力的設計直接收到認知和生物學的啟發
- Artificial Cognitive Systems 人工認知系統
	從自然和認知係統重汲取靈感，對模擬和具體化/機器人代理進行建模
- Intelligent Robotics （Robotics and AI） 智能機器人
	智能功能設計和方程方法在機器人中使用任何人工智能方法

影響CR的原理和理論：
- 具身認知理論
- 人工智能和基於知識的系統
- 基於行為的機器人技術 - 綜合方法 



[Modelling Cognitive System 認知系統建模](Computer%20Science/cognitive%20robotics/Modelling%20Cognitive%20System%20認知系統建模.md)

## What is Cognition 

認知是一個自主系統感知環境、從經驗中學習、預測事件結果、採取行動追求目標並適應不斷變化的環境的的過程 

但認知的定義可能取決於
- 認知是為了什麼 
- 認知如何在物理係統中實現

![](PICTURE/intro/555f4b3041b068070f635d8f9b4b757b_MD5.jpeg)


## Marr ’s Levels of Abstraction
- A theoretical/computational model is an abstraction of a real system
- Marr’s Levels of Abstraction (Marr 1982)
	- From computer vision to cognitive systems
	- Levels of analysis and understanding of a system
	- Hierarchical and sequential levels
		1. Computational / theory
		2. Representation / algorithmic
		3. Implementation
![](PICTURE/intro/5f7f8df13cf2a120605f30691b4fe03e_MD5.jpeg)

他認為要理解一個\[智能系統\] 的運作方式 (不論是人類大腦或機器人)，我們需要從三個不同的層次來分析

### Level 1： Computational Level 
核心問題：這個系統 \[需要解決什麼問題\]？
- 是什麼現象？ 系統的目的是什麼？
- 例如：一個認知機器人想要\[避開障礙物\]
	- 類比人類： 你知道自己要走路避開別人 | 類比機器人： 機器要能\[知道自己應該避開東西\]

### Level 2： Algorithmic Level 演算法層
核心問題：這個問題\[是怎麼被解決的\] ？ 用什麼規則或流程？
- 使用什麼輸入/輸出 哪個演算法或邏輯? 
- 例如：計算距離最近的障礙物 -> 右轉或左轉


### Level 3： Implementation 實作層 
核心問題：這些演算法 \[用什麼來實現\] 
- 用哪種機器？硬件？電路？神經元？






## Developmental Robotics 發展機器人技術

Direct inspiration from developmental psychology直接受到發展心理學的啟發
                                                                                                          

### Six principles 

– Dynamical systems動力係統, phylogenetic系統發生-ontogenetic個體發生 interaction, Embodiment具體化, Intrinsic motivation內在動機
– Incremental增量, non linear developmental stages and open ended learning 


|                         Principles                                                                |                                             Characteristics                                                                        |
|:--------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------|
|           Development as a Dynamical System 動態系統          <br><br>發展不是直線式、單一控製的，而是很多因素一起動態互動出來的結果 |  Decentralized system 分散系統(去中心化[沒有一個單一指揮中心，各部分相互影響]) Self-organization and emergence Multicausality Nested timescales  多因果性嵌套時間尺寸  |
|  Phylogenetic and Ontogenetic Interaction 系統發展和個體發展相互作用成熟                                         |                                Maturation，內在機制隨時打開 Critical period Learning 關鍵時期學習                                                 |
|         Embodied and Situated Development 具身及情境化發展                                                |       Embodiment具身性&nbsp;Situatedness情境性&nbsp;Enaction 行动性Morphlogical computation形态逻辑计算&nbsp;Grounding基础性                         |
|     Intrinsic Motivation and Social Learning 內在動機和社會學習                                            |                         Intrinsic motivation 內在動機(自己想學而不是外部獎勵推動) Value systems價值體系&nbsp;Imitation 模仿 (透過觀察他人行為來學習)                 |
|        Nonlinear, Stage-Like Development 非線性、階段式發展                                                |                              Qualitative stages U-shape phenomena 定性階段 U形現象                                                        |
|      Online Open-Ended Cumulative Learning 在線開放式積累學習                                              |             Online learning在線學習&nbsp;Cumulative累積性&nbsp;Cross-modality Cognitive跨模態&nbsp;bootstrapping 認知引導                        |  

這六大原則共同組成了 \[像人類一樣發展成長\]的機器人設計哲學，目的是讓機器人不只是被編程好的，而是能自我成長和適應世界


#### Princip 1： Dynamical System 動力系統 
- Decentralized system 去中心化系統
- Self-organization and emergence 自組織與湧現
- Multicausality 多因果關係
- Nested timescales 嵌套時間表

![](PICTURE/intro/8990b22c26531b8a848803affd13324b_MD5.jpeg)




#### Principle 3： Embodied and Situated 具體化和情境化

- Embodiment: Body-Brain-Environment interaction (Wilson 2002; Ziemke 2003) 
- Situatedness: Learning in context (Clark 1997) 
	- Enaction: Own model of the world (Vernon, 2010) 定制：自己的世界模型
	- Morphological computation (cf. robot lectures) 形態計算
	- Grounding (cf. language lecture 基礎

#### Principle 4： Intrinsic Motivation 內在動機 and Social Learning社會學習

- Intrinsic Motivation 內在動機：
	- Curiosity, surprise, novelty-seeking, values, drives
- Social Learning and imitation
	- cf. Social and Human-Robot Interaction lecture

#### Principle 5： No Linear， Stage development

- Developmental milestones:
![](PICTURE/intro/b41687ea2a8b37019055a73201f58748_MD5.jpeg)
- Qualitative Stages (Piaget)
	- Genetic Epistemology Theory 發生認識論
	- 4 Stages
		![](PICTURE/intro/eacce25ba961817eecd290a431751f7c_MD5.jpeg)
		- The Sensorimotor Stage 感覺運動天賦 
			- Age: Birth to 2 Years
			- Major Characteristics and Developmental Changes:
				- The infant knows the world through their movements and sensations 嬰兒通過自己的動作和感覺來認識世界
				- Children learn about the world through basic actions such as sucking, grasping, looking, and listening 兒童 通過吸吮、抓握、觀看和聆聽等基本動作來認識世界
				- Infants learn that things continue to exist even though they cannot be seen (object permanence)
				- They are separate beings from the people and objects around them 他們與周圍的人和物體是獨立的個體
				- They realize that their actions can cause things to happen in the world around them 他們意識到自己的行為會導致周圍世界發生變化
		- The Preoperational Stage 前操作階段
			- Age: 2 to 7 Years
			- Major Characteristics and Developmental Changes:
				- Children begin to think symbolically and learn to use words and pictures to represent objects. 兒童開始進行象征性思維，並學會使用語言和圖片來表示事物
				- Children at this stage tend to be egocentric and struggle to see things from the perspective of others. 該階段的兒童往往以自我為中心，難以從他人的角度看待事物
				- While they are getting better with language and thinking, they still tend to think about things in very concrete terms. 儘管他們的語言和思維能力正在提高，但仍然傾向於以非常具體的方式思考問題
		- The Concrete Operational Stage 具體操作階段
			- Age: 7 to 11 Years
			- Major Characteristics and Developmental Changes:
				- During this stage, children begin to thinking logically about concrete events 嬰兒開始對具體時間進行邏輯思考
				- They begin to understand the concept of conservation; that the amount of liquid in a short, wide cup is equal to that in a tall, skinny glass, for example 開始理解守恆的概念
				- Their thinking becomes more logical and organized, but still very concrete 思維變得更加邏輯和有條例但仍然非常具體
				- Children begin using inductive logic, or reasoning from specific information to a general principle 開始使用歸納推理，即從具體信息推斷出一般原則
		- The Formal Operational Stage 形式運算階段
			- Ages: 12 and Up
			- Major Characteristics and Developmental Changes:
				- At this stage, the adolescent or young adult begins to think abstractly and reason about hypothetical problems 開始抽象思考，並對假設性問題進行推理
				- Abstract thought emerges 抽象思維開始出現
				- Teens begin to think more about moral, philosophical, ethical, social, and political issues that require theoretical and abstract reasoning開始更多地思考需要理論和抽象推理的道德、哲學、理論、社會和政治問題
				- They begin to use deductive logic, or reasoning from a general principle to specific information 開始使用演繹邏輯，即從一般原則的推導出具體信息

- Non-linear development (U-Shape)
		![](PICTURE/intro/297c7836bff394ccb63eafe4e6f6ba15_MD5.jpeg)

#### Principle 6: Online, Open Ended, Cumulative
- Online learning 在線學習
- Cumulative 累積
- Cross-modality 跨模態
- Cognitive bootstrapping 認知引導


## Developmental Robotics of Language Acquisition  語言習得的發展機器人學
- ERA architecture for cumulative learning  用於累計學習的ERA架構
	- 5+ Experiments: first words, mutual exclusivity, U-learning, word order 
	- Collaboration with BabyLabs: Smith (Indiana USA), Horst(Sussex), Floccia & Cattani (Plymouth), Twomey (Manchester)

![](PICTURE/intro/1c5daa33cefd4ffd5b05f669c22e4d25_MD5.jpeg)



## Robotics basics 


![](PICTURE/intro/12ef3461611bbdb043048ead0fc6496f_MD5.jpeg)

a. Kinematics 運動學: Kinematics studies the motion of a robotic manipulator without considering the forces or torques that cause the motion. 

b. Workspace: The workspace is the volume of space that a robot's end- effector can reach, defined by its kinematic and structural constraints. 

c. Frame: A frame is a coordinate system used to define the position and  orientation of a point or object in space. 

d. Trajectory: A trajectory specifies the path and the associated velocity  or acceleration profiles of a robot’s end-effector in its workspace.













