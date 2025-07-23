---
LINK:
  - "[[cognitive robotics]]"
---


# MuJoCo 

開源，由Deepmind提供支持  
[GitHub - google-deepmind/mujoco: Multi-Joint dynamics with Contact. A general purpose physics simulator.](https://github.com/google-deepmind/mujoco)

Multi-Joint dynamics with Contact (多關節接觸動力學) 一款用於機器人研究的物理模擬器 

> 是一個模擬器

### 核心場景：
- 算法開發與驗證： 通過MuJoCo仿真環境 (如MiMo模型) 設計強化學習策略、測試傳感器融合方法、優化控制算法 
- 认知科学研究：研究婴儿早期行为（如抓取、站立）的感知-运动协同机制，完全依赖虚拟环境中的多模态数据（视觉、触觉、本体感觉）。
- 低成本快速迭代：仿真允许无限次重复实验，规避硬件损坏风险，适合算法原型开发



## 初始化 
https://github.com/google-deepmind/mujoco

https://github.com/google-deepmind/mujoco/releases 下載安裝包

解壓到本地目錄  
設置環境變量：
新建系統變量：
- 變量名：MUJOCO_PY_MUJOCO_PATH 
- 變量值：文件位置 
- 編輯PATH 添加： %MUJOCO_PY_MUJOCO_PATH%\bin


```bash 
simulate C:\Users\<用户名>\.mujoco\mujoco-3.2.7\model\humanoid.xml #驗證是否安裝成功
```














# MIMo Infant Model嬰兒模型


模擬嬰兒早期認知發展，研究多模態感知 (本體感覺，視覺，觸覺) 與運動控制的協同機制 

關鍵技術： 
- 多模態傳感器：
	-  **本体感觉**：关节角度、速度、扭矩反馈。
    - **前庭系统**：加速度计、陀螺仪模拟平衡感知。
    - **视觉**：双目摄像头提供立体视觉输入。
    - **触觉**：虚拟皮肤含6147个触点，模拟触觉反馈。
- 驅動模型： 基於人體生物力學數據設計關節活動範圍 (ROM) 與扭矩限制
- **现实意义**：为康复机器人、人机交互提供仿生控制策略。

![](PICTURE/Cognitive%20Robot%20Simulation/376a3b503eb599cbd4ee56139bad5738_MD5.jpeg)
![](PICTURE/Cognitive%20Robot%20Simulation/3eaec20a0ac5b0f05fa8cc32c6046aa8_MD5.jpeg)



```bash
conda create -n mimo python=3.9
conda activate mimo
pip install mujoco==3.2.1 gymnasium stable-baselines3 numpy glfw
git clone https://github.com/trieschlab/MIMo.git
cd MIMO
cd ../
pip install glfw
```

https://github.com/trieschlab/MIMo



執行模型可以控制它的身體
![](PICTURE/Cognitive%20Robot%20Simulation/3dbf3f87aefdc0f0bdcbb47026f34ed4_MD5.jpeg)












# **强化学习（RL）与工具链**

- **核心框架**：
    - **Gymnasium**：标准化RL环境接口，支持MuJoCo、Atari等环境。
    - **Stable Baselines3**：提供PPO、SAC等先进算法的PyTorch实现，简化训练流程。
- **训练流程示例**（以“接球任务”为例）：
    1. **环境封装**：将MIMo的物理状态（关节角度、触觉信号）转换为RL观测空间。
    2. **奖励设计**：
        - 接触奖励（+1）、成功奖励（+100）、动作惩罚（抑制抖动）、失败惩罚（-100）。
        - 关键挑战：稀疏奖励问题，需结合课程学习（Curriculum Learning）逐步增加难度。
    3. **算法选择**：PPO适用于连续动作空间，SAC在样本效率上表现更优。
- **延伸应用**：
    - **多模态数据融合**：使用Transformer或图神经网络（GNN）处理视觉、触觉异构数据。
    - **迁移学习**：将在仿真中训练的策略迁移至真实机器人（Sim2Real），需引入域随机化（Domain Randomization）。


##  Reinforcement Learning (RL) with Gymnasium and Stable Baselines 帶有體育館和穩定基線的強化學習
- ![](PICTURE/Cognitive%20Robot%20Simulation/e3b7d4f18b74e36c265e96d2016645c9_MD5.jpeg)
- Gymnasium https://github.com/Farama-Foundation/Gymnasium is an open-source Python library for communicating between RL algorithms and environments. 用於在RL算法和環境之間進行通信
- Stable-Baselines3 library https://github.com/DLR-RM/stable-baselines3 provides implementations of reinforcement learning algorithms in PyTorch. 提供PyTorch中強化學習算法的實現


































