---
LINK:
  - HRI (Human-Robot Interaction)
---


是一款3D动态模拟器，能够在复杂的室内和室外环境中精准有效地模拟及机器人群



## 用途 ：
- 测试机器人算法
- 设计机器人
- 用现实场景进行回归测试


## Gazebo的一些主要特点

- 包含多个物理引擎
- 包含丰富的机器人模型和环境库
- 包含各种各样的传感器
- 程序设计方便和具有简单的图形界面




```bash
$sudo sh -c 'echo "deb  http://packages.osrfoundation.org/gazebo/ubuntu-stable `lsb_release -cs` main" > /etc/apt/sources.list.d/gazebo-stable.list'
$wget http://packages.osrfoundation.org/gazebo.key -O - | sudo apt-key add 
$sudo apt-get update
$sudo apt-get install gazebo9
$sudo apt-get install libgazebo9-dev
```


## 上方工具栏
![](PICTURE/Gazebo/52a36a5f6182fe20e32c89c9c0c8f061_MD5.jpeg)
上部工作栏是Gazebo的主工具栏，它包含一些最常用的与模拟器交互的选项，例如：选择，移动，旋转和缩放对象等按钮; 创造一些简单的形状（如立方体，球体，圆柱体）; 复制/粘贴模型选项。 -选择模式（select mode）：在场景中导航
- 翻译模式（translate mode）：选择要移动的模型
- 旋转模式（rotate mode）：选择要旋转的模型
- 缩放模式（scale mode）：选择要缩放的模型
- 撤消/重做（undo/redo）：撤消/重做场景中的操作
- 简单形状（simple shape）：将简单形状插入场景中
- 灯光（lights）：为场景添加灯光
- 复制/粘贴（copy/paste）：在场景中复制/粘贴模型
- Align：将模型彼此对齐
- Snap：将一个模型与另一个模型对齐
- 更改视图（change view）：从各个角度查看场景






## 底部工具栏
![](PICTURE/Gazebo/9b27705d698f189be3dd45177c0323ec_MD5.jpeg)


 底部工具栏显示有关模拟的数据，如模拟时间及其与实际时间的关系。

- “模拟时间”是指模拟运行时模拟器中时间流逝的速度。模拟时间可以比实时更慢或更快，具体取决于运行模拟所需的计算量。
- “实时”是指模拟器运行时在现实生活中经过的实际时间。模拟时间和实时之间的关系称为“实时因子”（RTF）。它是模拟时间与实时的比率。RTF衡量模拟运行与实时相比的速度或速率。
- Gazebo的世界状况每迭代一次，计算一次。你可以在底部工具栏的右侧看到迭代次数。每次迭代都会将模拟推进固定的秒数，称为步长。默认情况下，步长为1 ms。您可以按暂停按钮暂停模拟，并使用步骤按钮逐步执行几个步骤。




```bash
ign gazebo
#or
ign gazebo shapes.sdf
```




```bash
export TURTLEBOT3_MODEL=burger
ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py
```























































