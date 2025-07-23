---
LINK:
  - "[[cognitive robotics]]"
---

- HRI： 社交機器人和語言模型在人機交互場景中的應用
- 技術和科學挑戰：
	-  Speech recognition / production 語音識別 / 產生
	- Action recognition and intention reading 動作識別和意圖讀取
	- Trust and acceptability 信任和接受度
	- Emotion recognition / production 情緒識別/產生
	- Long-term interaction 長期互動



## Speech in Robotics 
- ASR: Automatic Speech recognition 自動語音識別
	- From Hidden Marcov Models (HMM) to deep learning systems (see 2019 ASR systems blog) 
	- Nuance VoCon, Sphinx
	- Google, Bing, Alexa
	- Robot-specific ASRs
- Speech Synthesis 語言合成
	- Text-to-speech 
	- Loquendo/Nuance
	- Google cloud text-to-speech





## Trust in HRI 

### Bayesian ToM Trust Model
- Bayesian Network (BN) 貝葉斯網絡: Separate BN for reliable可靠的 (R) and unreliable不可靠 (U) speaker 
- The action of the child is a consequence of her internal belief內心信念 $X_C$ and the informant's action告密者的行為 $Y_R$ or $Y_U$.
	![](PICTURE/Human-Robot%20Interaction%20(HRI)%20and%20Applications/c22e96000994ba467e5fcb7ae2f175f6_MD5.jpeg)
- Children collect statistical information for tracking the reliability of agents (MLE Maximum Likelihood Estimation for the setting of BN parameters). 孩子們收集統計信息來跟蹤代理的可靠性 (用於設置BN參數的MLE最大似然估計)
![](PICTURE/Human-Robot%20Interaction%20(HRI)%20and%20Applications/6f427de71890b6abade1eba8bb2d2e17_MD5.jpeg)




### HRI Trust Experiments 信任實驗
- Anthropomorphic and social factors in human’s trust of robots 人類對機器人信任的擬人化和社會因素
  - Social gaze 社交凝視
  - Speech 語言
  - Anthropomorphic priming 擬人化啟動
  - Share actions 分享行動
  - Imitation 模仿

- HRI protocols for measuring trust 用於測量信任的HRI協議
  - Price game judgement 價格博弈判斷
  - Investment game 投資博弈

### HRI Trust and Social Gaze 信任與社會關註

- **Experimental Questions:** 實驗問題
  - Does gaze, the developmental precursor of social behavior, support trust between humans and robots? 凝視作為社會行為發展的前兆，是否能夠支撐人類與機器人之間的信任？
  - Does the appearance of the robot have an influence on trust? 機器人的外表是否會影響信任

- **Experimental Design:** Extension of Rau’s et al. (2009) Price Judgment Task
  - Social Gaze (gaze / no gaze) 社交凝視
  - Appearance (Nao humanoid / Baxter) (also iCub) 外觀
  - Priming Order
    - first Nao – second Baxter
    - first Baxter – second Nao


#### Social and Humanoid Priming
- Trust = Change Rate
	- Number of participants’ price changes divided by the number of cases when the robot disagrees 參與者價格變化的數量除以機器人不同意的情況數量
	![](PICTURE/Human-Robot%20Interaction%20(HRI)%20and%20Applications/ce160b74b0e4539e1720118c4dc86021_MD5.jpeg) 
####  Measuring trust with behavioural game theory 與機器人作為合作夥伴或對手進行經濟遊戲
- Playing economic games with robots as partners or opponents 
	- Implicit measure 隱式測量
	- Repeated measures 重複測量
	- Complex interactions 複雜的相互作用
	- Investment amount = implicit measure of trust 投資金額 = 信任的隱性衡量標準
	- Repeated rounds track the development of trust over time/experience 重複的輪次跟蹤信任隨時間的/經驗的發展


#### Investment Game and Trust 投資博弈與信任

- Can anthropomorphic **behaviour** increase trust? 擬人行為可以增加信任嗎
  - Joint attention 共同關注
    - Head tracking, gaze, and gestures when playing the game
  - Interaction with the **intentions** of the robot與機器人的意圖進行交互
- Results
	![](PICTURE/Human-Robot%20Interaction%20(HRI)%20and%20Applications/25cb4cb6245d9ba3bc0ad58f76b17754_MD5.jpeg)


### HRI Applications: Robot Tutors for Education 教育機器人導師

#### 機器人的作用 ：
1. 導師 - 一對一互動
	- 機器人作為導師：最了解情況. 
2. 教師
3. 同伴與新手
4. 混合導師/教師 

- 結果
	- 機器人的角色是特定於應用的
	- 輔導在許多領域和許多年齡段中最有效
	- 沒有證據表明某個特定角色在結果方面優於其他角色


## Example

### Robots increase Learning  機器人促進學習
- 與機器人互動時學習收益
- Three conditions:
	- Lessons by the computer
	- Lessons by an on-screen robot 
	- Lessons by a physically embodied robots (Keepon)


### Social robots as tutors: example 
![](PICTURE/Human-Robot%20Interaction%20(HRI)%20and%20Applications/89ea267ae028b1e54ab87d38bf8b3607_MD5.jpeg)




### Robot Companions for Care 護理機器人伴侶


- Robots for healthcare with children
  - Children with autism (e.g. [Aurora project](#))
  - Children in hospital (e.g. [ALIZ-E project](#)) ([vimeo](#))
- Robot Companions for older people
  - H2020 [RobotEra](#) and [MoveCare](#) projects ([youtube](#))
  - [Turing Manchester Workshop](#), October 2019










