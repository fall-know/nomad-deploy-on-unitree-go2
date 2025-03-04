## 1. 坐标系说明
- **Unitree GO2 EDU** 遵循右手坐标系，且相机指向的方向为 **x轴的正方向**。

## 2. Nomad 航点输出
- 经测试，**Nomad** 输出的航点同样遵循右手坐标系，无需进行坐标变换或更改。

## 3. Nomad 的大致推理流程
### Step 1: 输入图像进行特征提取
- 将 **context 图像**、**obs 图像** 和 **goal 图像**（如果有的话）输入到 **视觉编码器**，提取视觉特征。

### Step 2: 使用扩散模型进行运动轨迹预测
- 将提取的视觉特征输入到 **扩散模型**（Diffusion），用于约束去噪过程。
- 扩散模型输出 **8条预测的运动轨迹**。

### Step 3: 选择并执行运动轨迹
- 从 8 条运动轨迹中选择一个特定轨迹的某一点作为 **waypoint**。
- 调用 **API** 到达该航点。



## 4.Nomad数据集制作和微调过程
### requirement

在unitree 内置拓展坞上安装好了ros2（由于unitree官方只支持ros2）并装好了rosbag2

### step 1.
- 通过rosbag2 订阅IMU和Camera话题
### step 2.
- 将得到的数据传到自己电脑上,且需要安装一个ros库,并使用rosbag—reverse把rosbag2转换成rosbag
### step 3.
- 使用nomad提供的process_bags.py对rosbag进行处理
### step 4.
- train.py 启动！



### LOOK THIS

还不是完整版的README,后续会继续补充相关细节。
