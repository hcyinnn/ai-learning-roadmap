# AI学习路线图 - 深度学习基础

## 学习目标

通过本阶段的学习，您将能够：

1. **理解神经网络基本原理**：掌握人工神经元的数学模型、激活函数的作用机制以及神经网络的信息处理流程
2. **掌握前馈神经网络**：理解单层和多层网络的架构设计，掌握万能近似定理的含义及其实践意义
3. **学会反向传播算法**：深入理解链式法则在神经网络中的应用，掌握自动微分机制和计算图的概念
4. **掌握深度学习框架**：熟练使用PyTorch或TensorFlow/Keras构建、训练和评估深度学习模型

本阶段是AI学习的中级阶段，适合已经具备机器学习基础的学习者。通过系统学习，您将建立扎实的深度学习理论基础和实践能力。

## 学习内容

### 1. 神经网络基础 (2-3周)

#### 人工神经元模型

人工神经网络（Artificial Neural Networks, ANNs）是受生物神经系统启发的计算模型。理解人工神经元模型是掌握深度学习的第一步。

**感知机（Perceptron）**

感知机是最早的人工神经元模型，由Frank Rosenblatt于1958年提出。它是一个二分类线性分类器，其数学表达式为：

```
y = f(∑(wᵢxᵢ) + b)
```

其中：
- `xᵢ` 是输入特征
- `wᵢ` 是对应的权重
- `b` 是偏置项
- `f` 是激活函数（在原始感知机中是阶跃函数）

感知机的学习算法通过迭代更新权重来最小化分类错误。虽然单层感知机只能处理线性可分问题（如无法解决XOR问题），但它为后续的多层网络奠定了基础。

**激活函数（Activation Functions）**

激活函数为神经网络引入非线性，使其能够学习复杂的模式。以下是常用的激活函数：

1. **Sigmoid函数**
   - 公式：σ(x) = 1 / (1 + e⁻ˣ)
   - 输出范围：(0, 1)
   - 优点：输出可解释为概率，平滑可微
   - 缺点：梯度消失问题（当输入值很大或很小时，梯度接近0），输出不是零中心的
   - 应用：二分类问题的输出层，门控机制（如LSTM）

2. **Tanh函数**
   - 公式：tanh(x) = (eˣ - e⁻ˣ) / (eˣ + e⁻ˣ)
   - 输出范围：(-1, 1)
   - 优点：零中心化，梯度比Sigmoid更强
   - 缺点：仍然存在梯度消失问题
   - 应用：隐藏层，特别是在RNN中

3. **ReLU（Rectified Linear Unit）**
   - 公式：f(x) = max(0, x)
   - 优点：计算简单，缓解梯度消失问题，稀疏激活
   - 缺点：Dead ReLU问题（当输入为负时，梯度为0，神经元永远不激活）
   - 应用：目前最常用的隐藏层激活函数

4. **GELU（Gaussian Error Linear Unit）**
   - 公式：f(x) = x · Φ(x)，其中Φ(x)是标准正态分布的累积分布函数
   - 近似公式：f(x) ≈ 0.5x(1 + tanh(√(2/π)(x + 0.044715x³)))
   - 优点：在Transformer架构中表现优异，平滑非线性
   - 应用：BERT、GPT等Transformer模型的默认激活函数

#### 前馈神经网络

前馈神经网络（Feedforward Neural Networks）是最基本的神经网络类型，信息从输入层单向流向输出层。

**单层网络**

单层网络仅包含输入层和输出层，没有隐藏层。它等价于线性模型（如线性回归或逻辑回归）。数学表示为：

```
y = f(Wx + b)
```

单层网络的能力有限，只能学习输入到输出的线性映射。

**多层网络（Multilayer Perceptron, MLP）**

多层网络包含一个或多个隐藏层，能够学习非线性映射。一个具有L层的网络可以表示为：

```
h⁽¹⁾ = f⁽¹⁾(W⁽¹⁾x + b⁽¹⁾)
h⁽²⁾ = f⁽²⁾(W⁽²⁾h⁽¹⁾ + b⁽²⁾)
...
y = f⁽ᴸ⁾(W⁽ᴸ⁾h⁽ᴸ⁻¹⁾ + b⁽ᴸ⁾)
```

其中h⁽ⁱ⁾是第i层的输出（激活值），W⁽ⁱ⁾和b⁽ⁱ⁾是第i层的权重和偏置。

**万能近似定理（Universal Approximation Theorem）**

万能近似定理指出：具有至少一个隐藏层、有限个神经元和非线性激活函数的前馈神经网络，可以以任意精度近似任何连续函数。

这个定理的重要性在于：
1. 理论保证：证明了神经网络的强大表达能力
2. 实践指导：告诉我们增加网络深度或宽度可以提升模型能力
3. 限制：定理不保证学习算法能找到最优权重，也不保证泛化能力

在实践中，深度网络（多个隐藏层）通常比宽度网络（单层但神经元很多）更高效。

#### 网络架构

**输入层**

输入层接收原始数据，神经元数量等于输入特征的维度。例如：
- 图像数据：28×28像素的灰度图像有784个输入神经元
- 文本数据：使用词向量表示时，输入维度等于词向量维度

**隐藏层**

隐藏层是网络的核心计算层，负责学习数据的层次化表示。设计考虑因素包括：
- 层数：更深的网络可以学习更复杂的特征层次
- 每层神经元数量：通常逐层递减（金字塔结构）
- 激活函数选择：ReLU是常用选择

**输出层**

输出层产生最终预测，其设计取决于任务类型：
- 二分类：1个神经元 + Sigmoid激活
- 多分类：K个神经元（K为类别数）+ Softmax激活
- 回归：1个神经元，无激活函数（或线性激活）

### 2. 反向传播与优化 (2-3周)

#### 损失函数

损失函数衡量模型预测值与真实值之间的差异，是训练神经网络的优化目标。

**均方误差（Mean Squared Error, MSE）**

MSE是回归问题最常用的损失函数：

```
MSE = (1/n) ∑(yᵢ - ŷᵢ)²
```

其中yᵢ是真实值，ŷᵢ是预测值，n是样本数量。

特点：
- 对异常值敏感（因为平方项）
- 梯度计算简单
- 假设误差服从高斯分布

**交叉熵损失（Cross-Entropy Loss）**

交叉熵是分类问题的标准损失函数：

1. 二分类交叉熵：
   ```
   L = -[y log(ŷ) + (1-y) log(1-ŷ)]
   ```

2. 多分类交叉熵：
   ```
   L = -∑ yᵢ log(ŷᵢ)
   ```

特点：
- 与Softmax配合使用
- 梯度性质好，不会出现梯度消失
- 信息论解释：衡量两个概率分布的差异

**其他损失函数**

1. **Huber损失**：结合MSE和MAE的优点，对异常值鲁棒
   ```
   L = { 0.5(y - ŷ)², 如果|y - ŷ| ≤ δ
       { δ|y - ŷ| - 0.5δ², 否则
   ```

2. **Hinge损失**：用于SVM和最大间隔分类
   ```
   L = max(0, 1 - y·ŷ)
   ```

3. **KL散度**：衡量两个概率分布的差异，常用于VAE等生成模型

#### 反向传播算法

反向传播（Backpropagation）是训练神经网络的核心算法，通过链式法则高效计算损失函数对每个参数的梯度。

**链式法则（Chain Rule）**

对于复合函数f(g(x))，其导数为：
```
df/dx = (df/dg) · (dg/dx)
```

在神经网络中，损失函数L是多个函数的复合，因此需要多次应用链式法则。

**计算图（Computational Graph）**

计算图将数学表达式表示为有向无环图（DAG），其中：
- 节点表示变量或操作
- 边表示数据流

例如，对于表达式z = x · y + x²，计算图为：
```
x ──┬──→ [·] ──→ [+] ──→ z
    │      ↑        ↑
    └──→ [²] ──────┘
    y ──────┘
```

计算图的优势：
1. 可视化计算流程
2. 自动计算梯度
3. 支持动态图（如PyTorch）和静态图（如TensorFlow 1.x）

**自动微分（Automatic Differentiation）**

自动微分是计算导数的数值技术，结合了符号微分和数值微分的优点：

1. **前向模式**：从输入到输出计算导数，适合输入维度少的情况
2. **反向模式**：从输出到输入计算梯度，适合输出维度少的情况（神经网络通常损失函数是标量）

深度学习框架使用反向模式自动微分，只需一次前向传播和一次反向传播即可计算所有参数的梯度。

#### 优化算法

**梯度下降（Gradient Descent）**

最基本的优化算法，参数更新规则：
```
θ = θ - α · ∇L(θ)
```

其中α是学习率，∇L(θ)是损失函数对参数的梯度。

**随机梯度下降（Stochastic Gradient Descent, SGD）**

每次使用一个或一小批样本计算梯度：
```
θ = θ - α · ∇Lᵢ(θ)
```

优点：
- 计算效率高
- 有助于逃离局部最小值
- 内存需求低

缺点：
- 梯度估计噪声大
- 收敛不稳定

**动量优化（Momentum）**

引入动量项加速收敛：
```
v = βv + (1-β)∇L(θ)
θ = θ - α · v
```

其中β通常设为0.9。动量帮助优化器在相关方向上加速，抑制振荡。

**Adam优化器**

Adam结合了动量和自适应学习率，是目前最常用的优化器：

```
m = β₁m + (1-β₁)∇L(θ)      # 一阶矩估计（均值）
v = β₂v + (1-β₂)(∇L(θ))²   # 二阶矩估计（方差）
m̂ = m / (1-β₁ᵗ)             # 偏差修正
v̂ = v / (1-β₂ᵗ)             # 偏差修正
θ = θ - α · m̂ / (√v̂ + ε)
```

默认参数：β₁=0.9, β₂=0.999, ε=1e-8

优点：
- 自适应学习率
- 对超参数不敏感
- 适用于大多数问题

**学习率调度（Learning Rate Scheduling）**

学习率调度策略在训练过程中动态调整学习率：

1. **阶梯衰减**：每隔一定epoch将学习率乘以衰减因子
2. **余弦退火**：学习率按余弦函数从初始值衰减到最小值
3. **warmup**：训练初期线性增加学习率，然后保持或衰减
4. **ReduceLROnPlateau**：当验证损失停止改善时降低学习率

### 3. 正则化技术 (2周)

#### 过拟合与欠拟合

**过拟合（Overfitting）**

过拟合发生在模型在训练数据上表现很好，但在未见数据上表现差。症状：
- 训练损失低，验证损失高
- 模型复杂度相对于数据量过高

**欠拟合（Underfitting）**

欠拟合发生在模型无法捕捉数据中的模式。症状：
- 训练和验证损失都高
- 模型太简单或训练不充分

**偏差-方差权衡**

- 高偏差：欠拟合，模型太简单
- 高方差：过拟合，模型太复杂
- 目标：找到偏差和方差的平衡点

#### L1/L2正则化

**L2正则化（权重衰减）**

在损失函数中添加权重的L2范数惩罚：
```
L_regularized = L_original + λ ∑ wᵢ²
```

效果：
- 使权重趋向于较小的值
- 防止权重过大导致的过拟合
- 等价于在优化中添加权重衰减项

**L1正则化**

添加权重的L1范数惩罚：
```
L_regularized = L_original + λ ∑ |wᵢ|
```

效果：
- 产生稀疏权重（许多权重变为0）
- 自动特征选择
- 适用于特征选择场景

#### Dropout

Dropout是一种简单而有效的正则化技术。在训练过程中，以概率p随机将神经元的输出置为0。

实现方式：
```python
# 训练时
mask = np.random.binomial(1, 1-p, size=h.shape)
h = h * mask / (1-p)  # 缩放以保持期望值

# 测试时
# 不应用dropout，直接使用所有神经元
```

效果：
- 减少神经元之间的共适应
- 隐式集成多个子网络
- 显著降低过拟合

常用dropout率：隐藏层0.5，输入层0.2

#### 批归一化（Batch Normalization）

批归一化对每个小批量的输入进行归一化：

```
μ_B = (1/m) ∑ xᵢ                    # 批次均值
σ²_B = (1/m) ∑ (xᵢ - μ_B)²          # 批次方差
x̂ᵢ = (xᵢ - μ_B) / √(σ²_B + ε)      # 归一化
yᵢ = γx̂ᵢ + β                        # 缩放和平移
```

其中γ和β是可学习的参数。

优点：
1. 加速训练收敛
2. 允许使用更高的学习率
3. 减少对参数初始化的敏感性
4. 具有正则化效果

应用位置：通常在全连接层或卷积层之后，激活函数之前

#### 层归一化（Layer Normalization）

层归一化对单个样本的所有特征进行归一化：

```
μ = (1/H) ∑ xᵢ
σ² = (1/H) ∑ (xᵢ - μ)²
x̂ᵢ = (xᵢ - μ) / √(σ² + ε)
yᵢ = γx̂ᵢ + β
```

其中H是特征维度。

与批归一化的区别：
- 批归一化：跨批次归一化同一特征
- 层归一化：跨特征归一化同一样本

应用场景：
- 循环神经网络（RNN）
- Transformer架构
- 小批量场景

#### 早停法（Early Stopping）

早停法通过监控验证集性能来决定何时停止训练：

实现步骤：
1. 将数据分为训练集和验证集
2. 训练模型并记录每个epoch的验证损失
3. 当验证损失连续若干个epoch不再改善时停止训练
4. 保存验证损失最低时的模型参数

优点：
- 简单有效
- 无需额外超参数（除了patience）
- 防止过拟合

### 4. 深度学习框架 (3-4周)

#### PyTorch

PyTorch是Facebook开发的开源深度学习框架，以动态计算图和Python优先的设计著称。

**张量操作**

张量是PyTorch的基本数据结构，类似于NumPy的ndarray，但支持GPU加速和自动微分：

```python
import torch

# 创建张量
x = torch.tensor([1, 2, 3])
y = torch.randn(3, 4)  # 正态分布随机数
z = torch.zeros(2, 3)  # 零张量

# 张量操作
a = y + z          # 加法
b = y @ z.T        # 矩阵乘法
c = torch.relu(y)  # 激活函数
d = y.mean()       # 求均值

# GPU加速
if torch.cuda.is_available():
    x_gpu = x.to('cuda')
    y_gpu = y.cuda()
```

**自动微分**

PyTorch使用动态计算图实现自动微分：

```python
x = torch.tensor([2.0], requires_grad=True)
y = x ** 2 + 3 * x + 1
y.backward()  # 反向传播
print(x.grad)  # 输出: tensor([7.])  (2*2 + 3)
```

关键概念：
- `requires_grad=True`：标记需要计算梯度的张量
- `.backward()`：计算梯度
- `.grad`：存储计算得到的梯度
- `torch.no_grad()`：禁用梯度计算（用于推理）

**模型定义**

使用`nn.Module`定义神经网络：

```python
import torch.nn as nn

class MLP(nn.Module):
    def __init__(self, input_dim, hidden_dim, output_dim):
        super(MLP, self).__init__()
        self.fc1 = nn.Linear(input_dim, hidden_dim)
        self.fc2 = nn.Linear(hidden_dim, output_dim)
        self.relu = nn.ReLU()
        self.dropout = nn.Dropout(0.5)
    
    def forward(self, x):
        x = self.relu(self.fc1(x))
        x = self.dropout(x)
        x = self.fc2(x)
        return x

model = MLP(784, 256, 10)
```

**训练循环**

标准的PyTorch训练循环：

```python
criterion = nn.CrossEntropyLoss()
optimizer = torch.optim.Adam(model.parameters(), lr=0.001)

for epoch in range(num_epochs):
    model.train()
    for batch_x, batch_y in train_loader:
        # 前向传播
        outputs = model(batch_x)
        loss = criterion(outputs, batch_y)
        
        # 反向传播和优化
        optimizer.zero_grad()
        loss.backward()
        optimizer.step()
    
    # 验证
    model.eval()
    with torch.no_grad():
        val_loss = ...
        val_acc = ...
```

**GPU加速**

```python
device = torch.device('cuda' if torch.cuda.is_available() else 'cpu')
model = model.to(device)
data = data.to(device)
```

#### TensorFlow/Keras

TensorFlow是Google开发的开源深度学习框架，Keras是其高级API。

**Keras API**

Keras提供简洁的API来构建和训练模型：

```python
import tensorflow as tf
from tensorflow import keras

# Sequential API
model = keras.Sequential([
    keras.layers.Dense(256, activation='relu', input_shape=(784,)),
    keras.layers.Dropout(0.5),
    keras.layers.Dense(10, activation='softmax')
])

# Functional API（更灵活）
inputs = keras.Input(shape=(784,))
x = keras.layers.Dense(256, activation='relu')(inputs)
x = keras.layers.Dropout(0.5)(x)
outputs = keras.layers.Dense(10, activation='softmax')(x)
model = keras.Model(inputs=inputs, outputs=outputs)
```

**模型构建**

```python
# 编译模型
model.compile(
    optimizer='adam',
    loss='sparse_categorical_crossentropy',
    metrics=['accuracy']
)

# 查看模型摘要
model.summary()
```

**训练与评估**

```python
# 训练
history = model.fit(
    train_x, train_y,
    epochs=10,
    batch_size=32,
    validation_split=0.2,
    callbacks=[
        keras.callbacks.EarlyStopping(patience=3),
        keras.callbacks.ModelCheckpoint('best_model.h5', save_best_only=True)
    ]
)

# 评估
test_loss, test_acc = model.evaluate(test_x, test_y)

# 预测
predictions = model.predict(new_data)
```

**模型保存与加载**

```python
# 保存整个模型
model.save('my_model.h5')

# 加载模型
loaded_model = keras.models.load_model('my_model.h5')

# 仅保存权重
model.save_weights('model_weights.h5')
model.load_weights('model_weights.h5')
```

### 5. 实践技巧 (1-2周)

#### 数据增强（Data Augmentation）

数据增强通过对训练数据进行变换来增加数据多样性，是防止过拟合的有效方法。

**图像数据增强**

```python
from torchvision import transforms

train_transform = transforms.Compose([
    transforms.RandomHorizontalFlip(p=0.5),
    transforms.RandomRotation(10),
    transforms.RandomResizedCrop(224, scale=(0.8, 1.0)),
    transforms.ColorJitter(brightness=0.2, contrast=0.2, saturation=0.2),
    transforms.ToTensor(),
    transforms.Normalize(mean=[0.485, 0.456, 0.406], std=[0.229, 0.224, 0.225])
])

# 使用
dataset = ImageFolder('data/train', transform=train_transform)
```

**文本数据增强**

1. 同义词替换
2. 随机插入、删除、交换
3. 回译（Back Translation）
4. 使用语言模型生成

#### 模型初始化（Weight Initialization）

良好的权重初始化可以加速训练收敛。

**常用初始化方法**

1. **Xavier/Glorot初始化**：适用于Sigmoid和Tanh激活
   ```python
   nn.init.xavier_uniform_(layer.weight)
   ```

2. **He初始化**：适用于ReLU激活
   ```python
   nn.init.kaiming_uniform_(layer.weight, nonlinearity='relu')
   ```

3. **正交初始化**：适用于RNN
   ```python
   nn.init.orthogonal_(layer.weight)
   ```

**PyTorch默认初始化**
- 线性层：Kaiming均匀分布
- 卷积层：Kaiming均匀分布

#### 超参数选择

**学习率**

- 起始点：1e-3（Adam）或1e-2（SGD）
- 使用学习率查找器（Learning Rate Finder）
- 监控训练曲线调整

**批量大小（Batch Size）**

- 常用值：32, 64, 128, 256
- 大批量：训练稳定，但可能泛化差
- 小批量：正则化效果，但训练噪声大

**网络深度和宽度**

- 从较浅的网络开始
- 逐渐增加深度直到过拟合
- 使用正则化技术控制过拟合

**优化器选择**

- Adam：大多数情况的默认选择
- SGD + 动量：在计算机视觉任务中常用
- AdamW：权重衰减的Adam变体

#### 调试技巧

**常见问题诊断**

1. **损失不下降**
   - 检查学习率（可能太小或太大）
   - 检查数据预处理
   - 检查损失函数

2. **损失变为NaN或Inf**
   - 学习率过大
   - 数值不稳定（使用log_softmax代替log(softmax)）
   - 梯度爆炸（使用梯度裁剪）

3. **过拟合**
   - 增加数据量或数据增强
   - 添加正则化（Dropout, L2）
   - 减小模型复杂度

4. **欠拟合**
   - 增加模型复杂度
   - 训练更长时间
   - 检查特征工程

**梯度检查**

```python
# 检查梯度是否正确计算
def check_gradient(model, loss_fn, x, y, eps=1e-5):
    # 数值梯度
    numerical_grad = ...
    # 解析梯度
    analytical_grad = ...
    # 比较
    relative_error = abs(numerical_grad - analytical_grad) / (abs(numerical_grad) + abs(analytical_grad))
    assert relative_error < eps
```

#### 训练监控

**使用TensorBoard**

```python
from torch.utils.tensorboard import SummaryWriter

writer = SummaryWriter('runs/experiment_1')

for epoch in range(num_epochs):
    # 训练代码...
    
    # 记录指标
    writer.add_scalar('Loss/train', train_loss, epoch)
    writer.add_scalar('Loss/val', val_loss, epoch)
    writer.add_scalar('Accuracy/val', val_acc, epoch)
    
    # 记录直方图
    for name, param in model.named_parameters():
        writer.add_histogram(name, param, epoch)

writer.close()
```

**关键监控指标**

1. 训练损失和验证损失
2. 训练准确率和验证准确率
3. 学习率变化
4. 梯度分布
5. 权重分布

## 学习资源

### 推荐书籍

1. **《深度学习》（Deep Learning）**
   - 作者：Ian Goodfellow, Yoshua Bengio, Aaron Courville
   - 特点：深度学习领域的"圣经"，理论全面
   - 适合：希望深入理解理论的学习者

2. **《动手学深度学习》（Dive into Deep Learning）**
   - 作者：李沐等
   - 特点：理论与实践结合，有配套代码和视频
   - 适合：希望边学边做的学习者
   - 网址：https://d2l.ai/

3. **《PyTorch深度学习实战》**
   - 作者：Eli Stevens, Luca Antiga, Thomas Viehmann
   - 特点：PyTorch官方推荐，实践性强
   - 适合：希望掌握PyTorch的学习者

4. **《Python深度学习》（Deep Learning with Python）**
   - 作者：François Chollet（Keras创始人）
   - 特点：Keras API讲解清晰，示例丰富
   - 适合：初学者入门

### 推荐课程

1. **CS231n: Convolutional Neural Networks for Visual Recognition**
   - 来源：斯坦福大学
   - 讲师：Fei-Fei Li, Justin Johnson
   - 特点：计算机视觉深度学习的经典课程
   - 网址：http://cs231n.stanford.edu/

2. **CS224n: Natural Language Processing with Deep Learning**
   - 来源：斯坦福大学
   - 讲师：Christopher Manning
   - 特点：NLP深度学习的经典课程
   - 网址：http://web.stanford.edu/class/cs224n/

3. **Deep Learning Specialization**
   - 来源：Coursera
   - 讲师：Andrew Ng
   - 特点：系统性强，适合入门
   - 网址：https://www.coursera.org/specializations/deep-learning

4. **Fast.ai Practical Deep Learning for Coders**
   - 来源：fast.ai
   - 讲师：Jeremy Howard
   - 特点：自顶向下教学法，实践优先
   - 网址：https://course.fast.ai/

5. **MIT 6.S191: Introduction to Deep Learning**
   - 来源：MIT
   - 特点：紧凑高效，覆盖最新进展
   - 网址：http://introtodeeplearning.com/

### 官方文档

1. **PyTorch官方文档**
   - 网址：https://pytorch.org/docs/stable/
   - 特点：全面详细，有教程和示例

2. **TensorFlow官方文档**
   - 网址：https://www.tensorflow.org/guide
   - 特点：内容丰富，有中文版

3. **Keras官方文档**
   - 网址：https://keras.io/
   - 特点：API文档清晰，示例实用

4. **PyTorch Lightning**
   - 网址：https://www.pytorchlightning.ai/
   - 特点：简化PyTorch训练代码

## 实践项目

### 项目1：手写数字识别（MNIST）

**目标**：使用神经网络识别0-9的手写数字

**数据集**：MNIST（60,000训练样本，10,000测试样本）

**实现步骤**：

1. **数据加载和预处理**
```python
import torchvision
import torchvision.transforms as transforms

transform = transforms.Compose([
    transforms.ToTensor(),
    transforms.Normalize((0.1307,), (0.3081,))
])

train_dataset = torchvision.datasets.MNIST(root='./data', train=True, 
                                           download=True, transform=transform)
test_dataset = torchvision.datasets.MNIST(root='./data', train=False, 
                                          transform=transform)

train_loader = DataLoader(train_dataset, batch_size=64, shuffle=True)
test_loader = DataLoader(test_dataset, batch_size=1000, shuffle=False)
```

2. **模型定义**
```python
class MNISTNet(nn.Module):
    def __init__(self):
        super(MNISTNet, self).__init__()
        self.fc1 = nn.Linear(784, 256)
        self.fc2 = nn.Linear(256, 128)
        self.fc3 = nn.Linear(128, 10)
        self.dropout = nn.Dropout(0.2)
    
    def forward(self, x):
        x = x.view(-1, 784)
        x = torch.relu(self.fc1(x))
        x = self.dropout(x)
        x = torch.relu(self.fc2(x))
        x = self.dropout(x)
        x = self.fc3(x)
        return x
```

3. **训练和评估**

**预期结果**：测试准确率 > 98%

**扩展挑战**：
- 使用卷积神经网络（CNN）
- 实现数据增强
- 尝试不同的优化器和学习率调度

### 项目2：图像分类（CIFAR-10）

**目标**：对10类彩色图像进行分类

**数据集**：CIFAR-10（50,000训练样本，10,000测试样本）

**类别**：飞机、汽车、鸟、猫、鹿、狗、青蛙、马、船、卡车

**实现步骤**：

1. **数据增强**
```python
train_transform = transforms.Compose([
    transforms.RandomHorizontalFlip(),
    transforms.RandomCrop(32, padding=4),
    transforms.ToTensor(),
    transforms.Normalize((0.4914, 0.4822, 0.4465), (0.2023, 0.1994, 0.2010))
])
```

2. **CNN模型**
```python
class CIFAR10Net(nn.Module):
    def __init__(self):
        super(CIFAR10Net, self).__init__()
        self.conv1 = nn.Conv2d(3, 32, 3, padding=1)
        self.conv2 = nn.Conv2d(32, 64, 3, padding=1)
        self.conv3 = nn.Conv2d(64, 128, 3, padding=1)
        self.pool = nn.MaxPool2d(2, 2)
        self.fc1 = nn.Linear(128 * 4 * 4, 512)
        self.fc2 = nn.Linear(512, 10)
        self.dropout = nn.Dropout(0.25)
    
    def forward(self, x):
        x = self.pool(torch.relu(self.conv1(x)))
        x = self.pool(torch.relu(self.conv2(x)))
        x = self.pool(torch.relu(self.conv3(x)))
        x = x.view(-1, 128 * 4 * 4)
        x = self.dropout(torch.relu(self.fc1(x)))
        x = self.fc2(x)
        return x
```

**预期结果**：测试准确率 > 90%

**扩展挑战**：
- 使用ResNet架构
- 实现学习率调度
- 使用混合精度训练

### 项目3：文本分类（IMDb情感分析）

**目标**：判断电影评论是正面还是负面

**数据集**：IMDb（25,000训练样本，25,000测试样本）

**实现步骤**：

1. **数据预处理**
```python
from torchtext.data import Field, LabelField, BucketIterator

TEXT = Field(tokenize='spacy', tokenizer_language='en_core_web_sm')
LABEL = LabelField(dtype=torch.float)

# 加载数据
train_data, test_data = datasets.IMDB.splits(TEXT, LABEL)

# 构建词汇表
TEXT.build_vocab(train_data, max_size=25000, vectors="glove.6B.100d")
LABEL.build_vocab(train_data)
```

2. **RNN模型**
```python
class SentimentRNN(nn.Module):
    def __init__(self, vocab_size, embedding_dim, hidden_dim, output_dim):
        super(SentimentRNN, self).__init__()
        self.embedding = nn.Embedding(vocab_size, embedding_dim)
        self.rnn = nn.LSTM(embedding_dim, hidden_dim, num_layers=2, 
                           bidirectional=True, dropout=0.5)
        self.fc = nn.Linear(hidden_dim * 2, output_dim)
        self.dropout = nn.Dropout(0.5)
    
    def forward(self, x):
        embedded = self.dropout(self.embedding(x))
        output, (hidden, cell) = self.rnn(embedded)
        hidden = torch.cat((hidden[-2,:,:], hidden[-1,:,:]), dim=1)
        return self.fc(hidden.squeeze(0))
```

**预期结果**：测试准确率 > 85%

**扩展挑战**：
- 使用预训练词向量（GloVe, Word2Vec）
- 实现Transformer模型
- 处理更长的文本序列

## 学习检查点

完成本阶段学习后，您应该能够回答以下问题：

### 理论检查点

1. **神经网络基础**
   - [ ] 解释感知机的工作原理及其局限性
   - [ ] 比较不同激活函数的优缺点
   - [ ] 描述万能近似定理及其意义

2. **反向传播与优化**
   - [ ] 解释链式法则在反向传播中的应用
   - [ ] 比较不同优化算法的特点
   - [ ] 描述学习率调度策略

3. **正则化技术**
   - [ ] 解释过拟合和欠拟合的原因
   - [ ] 比较L1和L2正则化的区别
   - [ ] 描述Dropout的工作原理

### 实践检查点

4. **深度学习框架**
   - [ ] 使用PyTorch定义和训练神经网络
   - [ ] 使用TensorFlow/Keras构建模型
   - [ ] 实现完整的训练循环

5. **项目实践**
   - [ ] 完成至少一个图像分类项目
   - [ ] 完成至少一个文本分类项目
   - [ ] 使用TensorBoard监控训练过程

### 进阶准备

6. **扩展知识**
   - [ ] 了解卷积神经网络（CNN）的基本概念
   - [ ] 了解循环神经网络（RNN）的基本概念
   - [ ] 了解Transformer架构的基本思想

## 常见问题

### Q1: 应该选择PyTorch还是TensorFlow？

**PyTorch优势**：
- 动态计算图，调试方便
- Python优先，符合Python习惯
- 学术界主流，研究论文代码多
- 社区活跃，发展迅速

**TensorFlow优势**：
- 工业部署成熟（TF Serving, TF Lite）
- Keras API简洁易用
- 可视化工具强大（TensorBoard）
- 移动端支持好

**建议**：
- 初学者：先学PyTorch，再了解TensorFlow
- 研究方向：PyTorch
- 工业部署：TensorFlow
- 两者都要：掌握一个，了解另一个

### Q2: 如何选择合适的学习率？

**常用策略**：
1. **学习率查找器**：从很小的学习率开始，逐渐增加，观察损失变化
2. **默认值参考**：
   - Adam: 1e-3
   - SGD: 1e-2
   - AdamW: 1e-3
3. **监控训练曲线**：
   - 损失震荡：学习率太大
   - 损失下降慢：学习率太小
4. **使用学习率调度**：余弦退火、warmup等

### Q3: 如何处理类别不平衡问题？

**数据层面**：
1. 过采样少数类（如SMOTE）
2. 欠采样多数类
3. 数据增强少数类样本

**算法层面**：
1. 类别权重：在损失函数中为不同类别分配不同权重
   ```python
   class_weights = torch.tensor([1.0, 5.0])  # 少数类权重更高
   criterion = nn.CrossEntropyLoss(weight=class_weights)
   ```
2. Focal Loss：降低易分类样本的权重
3. 使用适合不平衡数据的评估指标（如F1-score, AUC-ROC）

### Q4: 模型训练很慢怎么办？

**优化策略**：
1. **数据加载**：
   - 使用多进程数据加载（`num_workers > 0`）
   - 使用内存映射或SSD存储数据
   - 预取数据（`prefetch_factor`）

2. **模型优化**：
   - 使用混合精度训练（FP16）
   - 减小批量大小
   - 简化模型架构

3. **硬件优化**：
   - 使用GPU
   - 使用多GPU并行（DataParallel或DistributedDataParallel）
   - 使用更快的硬件（如A100 GPU）

4. **训练策略**：
   - 使用梯度累积模拟大批量
   - 使用梯度检查点减少内存占用
   - 使用更高效的优化器

### Q5: 如何判断模型是否收敛？

**收敛指标**：
1. **损失曲线**：训练和验证损失都趋于平稳
2. **验证性能**：验证准确率不再提升
3. **梯度范数**：梯度范数趋近于0
4. **参数变化**：参数更新幅度很小

**停止标准**：
1. 达到预设的epoch数
2. 早停法：验证损失连续若干epoch不改善
3. 性能达标：达到目标准确率

### Q6: 如何处理过拟合？

**正则化技术**：
1. 增加训练数据
2. 数据增强
3. L1/L2正则化
4. Dropout
5. 批归一化
6. 早停法

**模型设计**：
1. 减少模型复杂度（层数、神经元数量）
2. 使用更简单的模型架构
3. 权重共享

**训练策略**：
1. 减小学习率
2. 使用更小的批量大小
3. 使用交叉验证

### Q7: 如何在生产环境部署深度学习模型？

**部署流程**：
1. **模型导出**：
   - PyTorch: TorchScript或ONNX
   - TensorFlow: SavedModel或TF Lite

2. **模型优化**：
   - 量化（FP32 → INT8）
   - 剪枝
   - 知识蒸馏

3. **服务部署**：
   - REST API（Flask, FastAPI）
   - 专用服务（TF Serving, TorchServe）
   - 云服务（AWS SageMaker, Google AI Platform）

4. **监控和维护**：
   - 性能监控
   - 数据漂移检测
   - 模型更新策略

---

## 学习建议

1. **循序渐进**：不要急于求成，扎实掌握每个概念
2. **动手实践**：理论学习后立即通过代码实践
3. **阅读论文**：从经典论文开始，了解领域发展
4. **参与社区**：加入学习社区，与他人交流
5. **持续学习**：深度学习领域发展迅速，保持学习习惯

## 下一步学习

完成本阶段后，您可以继续学习：
- **卷积神经网络（CNN）**：计算机视觉
- **循环神经网络（RNN/LSTM/GRU）**：序列数据
- **Transformer架构**：自然语言处理
- **生成对抗网络（GAN）**：生成模型
- **强化学习**：决策和控制

祝您学习顺利！