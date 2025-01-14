## 解决每次多个的结果都一样

为了提高彩票预测结果的多样性，针对现有应用程序进行了以下改动：

### 1. 增强输入随机性

- **改动内容**：将随机输入的生成方式从均匀分布改为正态分布，并扩大随机输入的范围。
- **实现效果**：每次预测使用更具多样性的输入，显著提升了预测结果的随机性和多样性。

### 2. 改进 CRF 的采样策略

#### 2.1 引入温度采样

- **改动内容**：在采样过程中加入温度参数，控制概率分布的平滑程度。
- **实现效果**：温度采样使得采样过程更加灵活，能够根据需求调整随机性。

#### 2.2 增加 Top-K 值

- **改动内容**：将每个时间步保留的候选标签数量从3增加到5。
- **实现效果**：通过考虑更多的候选标签，解码器能够探索更广泛的序列组合，提升预测的多样性。


### 3. 优化模型训练以提高泛化能力

- **改动内容**：
  - 在 LSTM 模型中加入 Dropout 层，防止过拟合。
  - 应用正则化技术，如 L2 正则化。
  - 增加训练数据的多样性，确保模型学习到更广泛的模式。
- **实现效果**：
  - Dropout 和正则化技术有效减少了模型的过拟合，提高了模型的泛化能力。
  - 通过增加训练数据的多样性，模型能够生成更具变化性的预测结果。


### 4. 温度采样参数调整

- **改动内容**：在采样函数中引入温度参数，允许用户根据需求调整随机性。
- **实现效果**：用户可以通过调整温度值，灵活控制预测结果的随机性和平衡性。

---