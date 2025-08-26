---
LINK: "[[Master Project]]"
---
# AIM： 改善病患交互自然度


# 关注： “**交互过程本身的设计、反馈与响应机制**”
# 目标人群： 病患、老年人、康复期患者等


- 如何让机器人理解患者的语义意图 (语音+姿态)
- 患者对不同类型的反馈
- 任务中交互频率与人对机器人的信任感
- 如何设计更自然的turn-talking 
- 


1. 通过语音+视觉 与系统交互 ： 语音 + 表情 -> 判断患者意图/痛苦指数
2. 主动交互 vs 被动交互 ：主动发起询问 (观测到表情变化后询问"你还好吗")
3. 多轮对话
4. 用户说不是这个意思后系统如何修正对话路径




## 交互原型
有交互场景原型设计的展示






使用LLM 提升语义理解  -> 与患者多轮交互能力 -> 可适配不同患者 -> 场景适应能力强
(与语音、动作等多模态集成)




## 用来进行对比的交互模式： 
### A. 传统规则对话系统
### B. 使用LLM的机器人 
## 测量：
语义理解准确率 


模拟场景


设计的架构或接口“通用性”或“可复用性








```rust
Instruction + Target  --->  OpenAI Model  ---> Predicted Action
          |                                       |
          v                                       v
     Ground Truth Action -------------------->  Evaluation (Accuracy, F1, Confusion Matrix)
```







Classification report:
                                               precision    recall  f1-score   support

               FOLLOW|human.pedestrian.adult       0.06      1.00      0.12         1
  FOLLOW|human. pedestrian. construction_worker       0.00      0.00      0.00         0
          FOLLOW|human. pedestrian. wheelchair       0.00      0.00      0.00         0
           FOLLOW|movable_object. trafficcone       0.00      0.00      0.00         0
                      FOLLOW|vehicle. bicycle       1.00      1.00      1.00         1
                    FOLLOW|vehicle. bus. rigid       0.67      0.50      0.57         4
                          FOLLOW|vehicle. car       0.52      0.80      0.63        15
                      FOLLOW|vehicle. trailer       0.00      0.00      0.00         0
                        FOLLOW|vehicle. truck       0.33      0.50      0.40         2
             GO_AHEAD|human. pedestrian. adult       0.00      0.00      0.00         2
        GO_AHEAD|human. pedestrian. wheelchair       0.00      0.00      0.00         1
             GO_AHEAD|movable_object. barrier       0.00      0.00      0.00         0
                  GO_AHEAD|vehicle. bus. rigid       0.00      0.00      0.00         0
                        GO_AHEAD|vehicle. car       0.00      0.00      0.00         3
                          GO_STRAIGHT|animal       0.00      0.00      0.00         0
          GO_STRAIGHT|human. pedestrian. adult       0.00      0.00      0.00         1
     GO_STRAIGHT|human. pedestrian. wheelchair       0.00      0.00      0.00         0
          GO_STRAIGHT|movable_object. barrier       0.00      0.00      0.00         0
               GO_STRAIGHT|vehicle. bus. rigid       0.00      0.00      0.00         0
                     GO_STRAIGHT|vehicle. car       0.00      0.00      0.00         0
                                OTHER|animal       0.00      0.00      0.00         1
                OTHER|human. pedestrian. adult       0.00      0.00      0.00        14
  OTHER|human. pedestrian. construction_worker       0.00      0.00      0.00         1
    OTHER|human. pedestrian. personal_mobility       0.00      0.00      0.00         3
           OTHER|human. pedestrian. wheelchair       0.00      0.00      0.00         8
            OTHER|movable_object. trafficcone       0.00      0.00      0.00         3
                     OTHER|vehicle. bus. rigid       0.00      0.00      0.00         2
                           OTHER|vehicle. car       0.00      0.00      0.00         5
              OTHER|vehicle. emergency. police       0.00      0.00      0.00         1
                                 PARK|animal       0.00      0.00      0.00         2
                 PARK|human. pedestrian. adult       0.00      0.00      0.00         8
                 PARK|movable_object. barrier       0.00      0.00      0.00         2
             PARK|movable_object. trafficcone       0.00      0.00      0.00         1
                            PARK|vehicle. car       0.00      0.00      0.00        19
                        PARK|vehicle. trailer       0.00      0.00      0.00         1
                          PARK|vehicle. truck       0.00      0.00      0.00         5
            SLOW_DOWN|human. pedestrian. adult       0.00      0.00      0.00         0
            SLOW_DOWN|human. pedestrian. child       0.00      0.00      0.00         0
       SLOW_DOWN|human. pedestrian. wheelchair       0.00      0.00      0.00         0
                 SLOW_DOWN|vehicle. bus. rigid       0.00      0.00      0.00         0
                       SLOW_DOWN|vehicle. car       0.00      0.00      0.00         0
                                 STOP|animal       0.50      1.00      0.67         3
                 STOP|human. pedestrian. adult       0.60      0.88      0.71        17
                 STOP|human. pedestrian. child       0.00      0.00      0.00         0
            STOP|human. pedestrian. wheelchair       1.00      0.71      0.83         7
                 STOP|movable_object. barrier       0.00      0.00      0.00         0
             STOP|movable_object. trafficcone       0.00      0.00      0.00         0
                        STOP|vehicle. bicycle       0.50      1.00      0.67         1
                      STOP|vehicle. bus. rigid       0.25      1.00      0.40         1
                            STOP|vehicle. car       0.13      1.00      0.24         2
                          STOP|vehicle. truck       0.00      0.00      0.00         0
          TURN_AROUND|human. pedestrian. adult       0.00      0.00      0.00         1
     TURN_AROUND|human. pedestrian. wheelchair       0.00      0.00      0.00         1
                            TURN_LEFT|animal       0.00      0.00      0.00         1
            TURN_LEFT|human. pedestrian. adult       0.57      0.50      0.53         8
            TURN_LEFT|human. pedestrian. child       0.00      0.00      0.00         1
TURN_LEFT|human. pedestrian. personal_mobility       0.00      0.00      0.00         1
       TURN_LEFT|human. pedestrian. wheelchair       0.50      1.00      0.67         2
            TURN_LEFT|movable_object. barrier       0.00      0.00      0.00         0
  TURN_LEFT|movable_object. pushable_pullable       1.00      1.00      1.00         1
        TURN_LEFT|movable_object. trafficcone       1.00      1.00      1.00         3
                   TURN_LEFT|vehicle. bicycle       1.00      1.00      1.00         2
                 TURN_LEFT|vehicle. bus. rigid       1.00      0.33      0.50         3
                       TURN_LEFT|vehicle. car       0.89      0.44      0.59        18
          TURN_LEFT|vehicle. emergency. police       0.00      0.00      0.00         1
                   TURN_LEFT|vehicle. trailer       0.00      0.00      0.00         1
                           TURN_RIGHT|animal       0.00      0.00      0.00         1
           TURN_RIGHT|human. pedestrian. adult       0.00      0.00      0.00         2
      TURN_RIGHT|human. pedestrian. wheelchair       0.25      0.50      0.33         2
           TURN_RIGHT|movable_object. barrier       0.33      1.00      0.50         1
       TURN_RIGHT|movable_object. trafficcone       0.00      0.00      0.00         1
                  TURN_RIGHT|vehicle. bicycle       1.00      1.00      1.00         1
                      TURN_RIGHT|vehicle. car       0.25      0.20      0.22         5
                  TURN_RIGHT|vehicle. trailer       1.00      0.33      0.50         3
                    TURN_RIGHT|vehicle. truck       0.50      0.33      0.40         3

                                    accuracy                           0.35       200
                                   macro avg       0.20      0.24      0.19       200
                                weighted avg       0.35      0.35      0.32       200










