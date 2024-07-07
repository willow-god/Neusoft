# 三层神经网络实现

这是一个用Python实现的简单三层神经网络。该项目展示了基本的前向传播和反向传播算法，并包括了训练和预测功能。

## 功能概述

- **激活函数**:
  - `identify_function`: 恒等函数，直接返回输入值。
  - `sigmoid`: Sigmoid激活函数，将输入值压缩到0和1之间。
  - `softmax`: Softmax函数，计算多分类问题中每个类别的概率。

- **损失函数**:
  - `cross_entropy_error`: 交叉熵损失函数，用于计算预测值和真实值之间的误差。

- **网络初始化**:
  - `init_network`: 初始化神经网络的权重和偏置，使用固定参数进行初始化。

- **前向传播**:
  - `forward`: 依次计算每一层的加权和及激活函数，最终输出经过softmax处理的结果。

- **反向传播**:
  - `backward`: 计算损失函数相对于每个参数的梯度，并使用梯度下降法更新网络的权重和偏置。

- **预测**:
  - `predict`: 使用训练后的网络进行预测，返回网络的输出结果。

- **训练过程**:
  - 在训练过程中，输入数据和真实标签通过前向传播计算输出，然后通过反向传播计算梯度并更新网络的参数。训练多个周期（epochs），不断优化网络参数以减少损失函数值。

## 代码结构

- **identify_function**: 定义恒等函数。
- **sigmoid**: 定义Sigmoid激活函数。
- **softmax**: 定义Softmax函数。
- **cross_entropy_error**: 定义交叉熵损失函数。
- **init_network**: 初始化神经网络的权重和偏置。
- **forward**: 定义前向传播函数。
- **backward**: 定义反向传播函数。
- **predict**: 定义预测函数。

## 使用方法

1. 初始化网络参数。
2. 提供输入数据和真实标签。
3. 通过前向传播计算输出，通过反向传播更新参数。
4. 重复上述过程进行训练。
5. 使用训练后的网络对新数据进行预测。

## 示例

以下是一个简单的示例，演示了如何初始化网络、进行训练并进行预测：

```python
# 初始化网络
network = init_network()

# 输入数据
x = np.array([[1.0, 0.5]])
t = np.array([[0, 1]])  # 真实标签，使用one-hot编码

# 训练过程
epochs = 1000
for epoch in range(epochs):
    y, z1, z2 = forward(network, x)
    loss = cross_entropy_error(y, t)
    backward(network, x, t, y, z1, z2)
    if epoch % 100 == 0:
        print(f"Epoch {epoch}, Loss: {loss}")

# 预测
x_test = np.array([[1.0, 0.5]])
y_test = predict(network, x_test)
print("Predicted:", y_test)
```

## 结论

该项目展示了一个简单的三层神经网络的实现，包括前向传播、反向传播、训练和预测。通过这些步骤，我们可以对输入数据进行分类，并不断优化模型参数以提高准确性。