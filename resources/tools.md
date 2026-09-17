# AI学习资源 - 常用工具

## 概述

### 工具分类
AI工具可以分为以下几大类：
1. **编程语言与环境**：Python、R、Julia等
2. **深度学习框架**：PyTorch、TensorFlow、JAX等
3. **数据处理工具**：Pandas、NumPy、Polars等
4. **可视化工具**：Matplotlib、Seaborn、Plotly等
5. **开发环境**：Jupyter、VS Code、Colab等
6. **实验管理**：W&B、MLflow、TensorBoard等
7. **数据集工具**：Hugging Face Datasets、TensorFlow Datasets等
8. **模型部署**：Docker、Kubernetes、TensorFlow Serving等
9. **版本控制**：Git、DVC等
10. **协作平台**：GitHub、GitLab等

### 选择建议
- **初学者**：从Python + Jupyter Notebook开始，搭配Pandas和Matplotlib
- **研究者**：PyTorch + Jupyter + W&B + Git
- **工程师**：TensorFlow/Keras + Docker + Kubernetes + MLflow
- **数据科学家**：Python + Pandas + Seaborn + Scikit-learn

### 学习路径
1. **基础阶段**（1-2个月）：Python → NumPy → Pandas → Matplotlib
2. **进阶阶段**（2-3个月）：Scikit-learn → PyTorch/TensorFlow → Jupyter
3. **专业阶段**（3-6个月）：Docker → Git → 实验管理工具 → 部署工具
4. **高级阶段**（持续学习）：Kubernetes → CI/CD → 分布式训练 → 模型优化

---

## 编程语言

### Python

#### 版本选择
- **Python 3.8+**：推荐使用3.9或3.10，兼容性好且性能优化
- **Python 3.11**：最新版本，性能提升约10-60%
- **避免Python 2**：已停止支持，不推荐新项目使用

#### 包管理
1. **pip**：Python官方包管理器
   ```bash
   pip install package_name
   pip install -r requirements.txt
   pip list  # 查看已安装包
   ```

2. **conda**：Anaconda发行版的包管理器
   ```bash
   conda install package_name
   conda env create -f environment.yml
   conda activate env_name
   ```

3. **poetry**：现代Python包管理工具
   ```bash
   poetry init
   poetry add package_name
   poetry install
   ```

#### 虚拟环境
1. **venv**（Python内置）
   ```bash
   python -m venv myenv
   source myenv/bin/activate  # Linux/Mac
   myenv\Scripts\activate  # Windows
   ```

2. **conda环境**
   ```bash
   conda create -n myenv python=3.9
   conda activate myenv
   ```

3. **virtualenv**
   ```bash
   pip install virtualenv
   virtualenv myenv
   ```

### 其他语言

#### R
- **特点**：统计计算和图形显示的强大工具
- **适用场景**：统计分析、数据可视化、生物信息学
- **学习资源**：
  - R for Data Science
  - Advanced R
  - RStudio（推荐IDE）
- **常用包**：tidyverse、ggplot2、dplyr、caret

#### Julia
- **特点**：高性能科学计算语言，兼具Python的易用性和C的性能
- **适用场景**：数值计算、科学模拟、高性能计算
- **学习资源**：
  - Julia官方文档
  - JuliaAcademy
  - Think Julia
- **常用包**：Flux.jl（深度学习）、DataFrames.jl、Plots.jl

#### C++
- **特点**：高性能系统编程语言
- **适用场景**：深度学习框架底层实现、高性能推理引擎、游戏AI
- **学习资源**：
  - C++ Primer
  - Effective Modern C++
  - CUDA编程（GPU加速）
- **常用库**：Eigen、OpenCV、TensorRT、ONNX Runtime

---

## 深度学习框架

### PyTorch

#### 特点
1. **动态计算图**：运行时构建计算图，便于调试
2. **Python优先**：与Python生态无缝集成
3. **易于调试**：支持标准Python调试器
4. **丰富的生态系统**：torchvision、torchaudio、torchtext等
5. **强大的社区**：学术界广泛使用，论文实现丰富

#### 适用场景
- 学术研究和原型开发
- 需要灵活模型架构的场景
- 自然语言处理（Hugging Face Transformers）
- 计算机视觉（torchvision）
- 强化学习

#### 学习资源
1. **官方教程**：https://pytorch.org/tutorials/
2. **PyTorch Lightning**：简化训练流程
3. **fast.ai**：高级深度学习课程
4. **书籍**：
   - Deep Learning with PyTorch
   - Programming PyTorch for Deep Learning

#### 常用模块
```python
import torch
import torch.nn as nn
import torch.optim as optim
from torch.utils.data import DataLoader, Dataset
import torchvision
import torch.nn.functional as F
```

**核心组件**：
- `torch.Tensor`：多维数组，支持GPU加速和自动微分
- `torch.nn`：神经网络模块
- `torch.optim`：优化器
- `torch.utils.data`：数据加载工具
- `torch.autograd`：自动微分系统

### TensorFlow

#### 特点
1. **静态计算图**：TF 1.x默认，TF 2.x支持动态图（Eager Execution）
2. **生产就绪**：完善的部署工具链
3. **跨平台支持**：支持移动端、Web、嵌入式设备
4. **TensorFlow Extended (TFX)**：端到端机器学习平台
5. **强大的可视化**：TensorBoard

#### 适用场景
- 生产环境部署
- 大规模分布式训练
- 移动端和边缘设备
- TensorFlow Serving部署
- Google Cloud集成

#### 学习资源
1. **官方教程**：https://www.tensorflow.org/tutorials
2. **TensorFlow Certificate**：官方认证
3. **书籍**：
   - Hands-On Machine Learning with Scikit-Learn, Keras, and TensorFlow
   - Deep Learning with TensorFlow 2 and Keras

#### Keras API
```python
import tensorflow as tf
from tensorflow import keras
from tensorflow.keras import layers

# 序贯API
model = keras.Sequential([
    layers.Dense(64, activation='relu'),
    layers.Dense(10, activation='softmax')
])

# 函数式API
inputs = keras.Input(shape=(784,))
x = layers.Dense(64, activation='relu')(inputs)
outputs = layers.Dense(10, activation='softmax')(x)
model = keras.Model(inputs, outputs)

# 编译和训练
model.compile(optimizer='adam',
              loss='sparse_categorical_crossentropy',
              metrics=['accuracy'])
model.fit(x_train, y_train, epochs=10)
```

### 其他框架

#### JAX
- **特点**：Google开发的高性能数值计算库，支持自动微分和XLA编译
- **适用场景**：高性能研究、函数式编程风格、大规模科学计算
- **学习资源**：JAX官方文档、Google JAX教程
- **常用库**：Flax（神经网络库）、Optax（优化器）、Haiku

#### PaddlePaddle
- **特点**：百度开发的深度学习框架，中文文档完善
- **适用场景**：中文NLP、国内企业应用、百度云集成
- **学习资源**：PaddlePaddle官方文档、百度AI Studio
- **特点**：飞桨、PaddleOCR、PaddleNLP等丰富工具

#### MindSpore
- **特点**：华为主发的深度学习框架，支持全场景AI
- **适用场景**：华为昇腾芯片、端边云协同、国内生态
- **学习资源**：MindSpore官方文档、华为开发者社区
- **特点**：MindSpore GoldenStick（模型压缩）、MindSpore Serving

---

## 数据处理工具

### Pandas

#### 基本操作
```python
import pandas as pd

# 创建DataFrame
df = pd.DataFrame({
    'name': ['Alice', 'Bob', 'Charlie'],
    'age': [25, 30, 35],
    'city': ['New York', 'London', 'Paris']
})

# 读取数据
df = pd.read_csv('data.csv')
df = pd.read_excel('data.xlsx')
df = pd.read_sql(query, connection)

# 数据选择
df['name']  # 选择列
df.loc[0]  # 按标签选择行
df.iloc[0]  # 按位置选择行
df[df['age'] > 25]  # 条件筛选
```

#### 常用函数
1. **数据清洗**
   ```python
   df.dropna()  # 删除缺失值
   df.fillna(0)  # 填充缺失值
   df.drop_duplicates()  # 删除重复值
   df.astype({'age': 'int'})  # 类型转换
   ```

2. **数据转换**
   ```python
   df.groupby('city').mean()  # 分组聚合
   df.pivot_table(values='age', index='city')  # 透视表
   df.melt()  # 宽格式转长格式
   df.merge(df2, on='name')  # 合并数据
   ```

3. **数据统计**
   ```python
   df.describe()  # 描述性统计
   df.corr()  # 相关性分析
   df.value_counts()  # 值计数
   df.groupby('city')['age'].agg(['mean', 'std'])  # 多聚合
   ```

#### 性能优化
1. **使用适当的数据类型**
   ```python
   df['category'] = df['category'].astype('category')
   df['id'] = pd.to_numeric(df['id'], downcast='integer')
   ```

2. **向量化操作**：避免使用循环，使用内置函数
3. **使用eval和query**
   ```python
   df.eval('bmi = weight / (height ** 2)')
   df.query('age > 25 and city == "London"')
   ```

4. **分块处理大文件**
   ```python
   for chunk in pd.read_csv('large.csv', chunksize=10000):
       process(chunk)
   ```

### NumPy

#### 数组操作
```python
import numpy as np

# 创建数组
arr = np.array([1, 2, 3, 4, 5])
zeros = np.zeros((3, 4))
ones = np.ones((2, 3))
random = np.random.randn(3, 3)

# 数组操作
arr.reshape(5, 1)  # 改变形状
arr.flatten()  # 展平
np.concatenate([arr1, arr2])  # 连接
np.split(arr, 5)  # 分割
```

#### 矩阵运算
```python
# 矩阵乘法
a = np.array([[1, 2], [3, 4]])
b = np.array([[5, 6], [7, 8]])
c = np.dot(a, b)  # 或 a @ b

# 矩阵属性
np.linalg.inv(a)  # 逆矩阵
np.linalg.det(a)  # 行列式
np.linalg.eig(a)  # 特征值和特征向量
np.linalg.svd(a)  # 奇异值分解
```

#### 广播机制
NumPy的广播机制允许不同形状的数组进行运算：
```python
a = np.array([[1], [2], [3]])  # 形状 (3, 1)
b = np.array([10, 20, 30])     # 形状 (3,)
c = a + b  # 广播后形状 (3, 3)
```

**广播规则**：
1. 如果数组维度不同，小维度数组会在左边补1
2. 如果形状在任何维度上不匹配且都不为1，报错
3. 如果形状在维度上匹配或其中一个为1，可以广播

### 其他工具

#### Polars
- **特点**：高性能DataFrame库，用Rust编写，比Pandas快10-100倍
- **适用场景**：大数据处理、性能敏感场景
- **学习资源**：Polars官方文档
- **示例**：
  ```python
  import polars as pl
  df = pl.read_csv('data.csv')
  df.filter(pl.col('age') > 25).group_by('city').mean()
  ```

#### Dask
- **特点**：并行计算库，可扩展Pandas和NumPy
- **适用场景**：超出内存的大数据处理、分布式计算
- **学习资源**：Dask官方文档
- **示例**：
  ```python
  import dask.dataframe as dd
  ddf = dd.read_csv('large_*.csv')
  ddf.groupby('city').mean().compute()
  ```

#### Vaex
- **特点**：懒惰、内存映射的DataFrame库，处理十亿级数据
- **适用场景**：大数据探索、可视化
- **学习资源**：Vaex官方文档
- **特点**：内存效率高、支持表达式系统

---

## 可视化工具

### Matplotlib

#### 基本图表
```python
import matplotlib.pyplot as plt

# 折线图
plt.plot([1, 2, 3, 4], [1, 4, 2, 3])
plt.xlabel('X轴')
plt.ylabel('Y轴')
plt.title('折线图')
plt.show()

# 散点图
plt.scatter(x, y, c=colors, s=sizes, alpha=0.5)

# 柱状图
plt.bar(categories, values)

# 直方图
plt.hist(data, bins=30, edgecolor='black')

# 饼图
plt.pie(sizes, labels=labels, autopct='%1.1f%%')
```

#### 样式定制
```python
# 使用样式
plt.style.use('seaborn')  # 或 'ggplot', 'dark_background'等

# 自定义样式
plt.rcParams['figure.figsize'] = (10, 6)
plt.rcParams['font.size'] = 12
plt.rcParams['axes.grid'] = True

# 子图
fig, axes = plt.subplots(2, 2, figsize=(12, 8))
axes[0, 0].plot(x, y)
axes[0, 0].set_title('子图1')
```

#### 动画制作
```python
from matplotlib.animation import FuncAnimation

fig, ax = plt.subplots()
line, = ax.plot([], [])

def init():
    line.set_data([], [])
    return line,

def animate(i):
    x = np.linspace(0, 2*np.pi, 100)
    y = np.sin(x + i/10)
    line.set_data(x, y)
    return line,

ani = FuncAnimation(fig, animate, init_func=init, frames=200, interval=50)
ani.save('animation.mp4', writer='ffmpeg')
```

### Seaborn

#### 统计图表
```python
import seaborn as sns
import pandas as pd

# 加载内置数据集
tips = sns.load_dataset('tips')

# 分布图
sns.histplot(data=tips, x='total_bill', hue='time')
sns.kdeplot(data=tips, x='total_bill', hue='time')
sns.ecdfplot(data=tips, x='total_bill', hue='time')

# 关系图
sns.scatterplot(data=tips, x='total_bill', y='tip', hue='time')
sns.lineplot(data=tips, x='total_bill', y='tip', hue='time')
sns.regplot(data=tips, x='total_bill', y='tip')

# 分类图
sns.boxplot(data=tips, x='day', y='total_bill', hue='sex')
sns.violinplot(data=tips, x='day', y='total_bill', hue='sex')
sns.barplot(data=tips, x='day', y='total_bill', hue='sex')
```

#### 主题设置
```python
# 设置主题
sns.set_theme(style='darkgrid')  # whitegrid, dark, white, ticks
sns.set_context('notebook')  # paper, notebook, talk, poster
sns.set_palette('deep')  # deep, muted, pastel, bright, dark, colorblind

# 自定义调色板
sns.set_palette(['#FF6B6B', '#4ECDC4', '#45B7D1'])
```

#### 调色板
```python
# 查看调色板
sns.color_palette()

# 使用调色板
sns.set_palette('husl', 8)

# 创建自定义调色板
cmap = sns.light_palette('green', as_cmap=True)
sns.heatmap(data, cmap=cmap)
```

### 其他工具

#### Plotly
- **特点**：交互式可视化库，支持Web展示
- **适用场景**：Web应用、交互式仪表板、数据探索
- **学习资源**：Plotly官方文档、Dash教程
- **示例**：
  ```python
  import plotly.express as px
  fig = px.scatter(df, x='gdp per capita', y='life expectancy',
                   size='pop', color='continent', hover_name='country')
  fig.show()
  ```

#### Bokeh
- **特点**：交互式可视化库，支持大数据集
- **适用场景**：Web应用、实时数据流、大数据可视化
- **学习资源**：Bokeh官方文档
- **特点**：支持Bokeh Server、与Jupyter集成良好

#### Altair
- **特点**：声明式可视化库，基于Vega-Lite
- **适用场景**：统计可视化、快速探索
- **学习资源**：Altair官方文档
- **示例**：
  ```python
  import altair as alt
  chart = alt.Chart(df).mark_circle().encode(
      x='Horsepower',
      y='Miles_per_Gallon',
      color='Origin',
      tooltip=['Name', 'Origin']
  ).interactive()
  ```

---

## 开发环境

### Jupyter Notebook

#### 安装配置
```bash
# 安装
pip install jupyter

# 启动
jupyter notebook

# 安装扩展
pip install jupyter_contrib_nbextensions
jupyter contrib nbextension install --user
```

#### 常用插件
1. **Table of Contents**：自动生成目录
2. **Variable Inspector**：变量检查器
3. **Execute Time**：显示代码执行时间
4. **Code Folding**：代码折叠
5. **Hinterland**：自动补全
6. **Collapsible Headings**：可折叠标题

#### 最佳实践
1. **命名规范**：使用描述性名称，如 `01_data_preprocessing.ipynb`
2. **Markdown单元格**：清晰记录思路和步骤
3. **代码组织**：按功能分块，每个单元格完成一个任务
4. **重启内核测试**：定期重启内核并运行所有单元格
5. **版本控制**：使用 `nbstripout` 清理输出后提交到Git

### VS Code

#### Python扩展
1. **Python**：Python语言支持
2. **Pylance**：智能代码补全和类型检查
3. **Python Debugger**：调试支持
4. **Jupyter**：Jupyter Notebook支持
5. **Python Indent**：智能缩进

#### Jupyter集成
1. **打开Notebook**：直接在VS Code中打开 `.ipynb` 文件
2. **交互式窗口**：运行Python代码片段
3. **变量资源管理器**：查看和管理变量
4. **Notebook调试**：在Notebook中设置断点
5. **导出功能**：导出为HTML、PDF等格式

#### 调试技巧
1. **设置断点**：点击行号左侧或按F9
2. **条件断点**：右键断点设置条件
3. **日志点**：不暂停执行的断点
4. **调试控制台**：交互式调试
5. **多进程调试**：支持调试多进程应用

### Google Colab

#### GPU使用
1. **启用GPU**：运行时 → 更改运行时类型 → GPU
2. **查看GPU信息**：
   ```python
   !nvidia-smi
   ```
3. **混合精度训练**：
   ```python
   policy = tf.keras.mixed_precision.Policy('mixed_float16')
   tf.keras.mixed_precision.set_global_policy(policy)
   ```

#### 代码执行
1. **快捷键**：
   - `Ctrl+Enter`：运行当前单元格
   - `Shift+Enter`：运行并移动到下一个
   - `Alt+Enter`：运行并在下方插入新单元格
2. **魔术命令**：
   ```python
   %timeit code  # 测量执行时间
   %matplotlib inline  # 内联显示图表
   %load_ext autoreload  # 自动重载模块
   ```

#### 文件管理
1. **上传文件**：
   ```python
   from google.colab import files
   uploaded = files.upload()
   ```
2. **下载文件**：
   ```python
   from google.colab import files
   files.download('output.csv')
   ```
3. **挂载Google Drive**：
   ```python
   from google.colab import drive
   drive.mount('/content/drive')
   ```

---

## 实验管理

### Weights & Biases

#### 实验追踪
```python
import wandb

# 初始化实验
wandb.init(project="my-project", name="experiment-1")

# 记录超参数
config = wandb.config
config.learning_rate = 0.001
config.batch_size = 32
config.epochs = 10

# 记录指标
for epoch in range(config.epochs):
    loss = train_epoch()
    accuracy = evaluate()
    wandb.log({"loss": loss, "accuracy": accuracy})

# 完成实验
wandb.finish()
```

#### 超参数优化
```python
# 使用Sweep
sweep_config = {
    'method': 'bayes',
    'metric': {'name': 'loss', 'goal': 'minimize'},
    'parameters': {
        'learning_rate': {'min': 0.0001, 'max': 0.1},
        'batch_size': {'values': [16, 32, 64, 128]}
    }
}

sweep_id = wandb.sweep(sweep_config, project="my-project")
wandb.agent(sweep_id, function=train, count=50)
```

#### 团队协作
1. **团队工作区**：创建团队并邀请成员
2. **报告**：创建交互式报告分享结果
3. **版本控制**：追踪数据集和模型版本
4. **警报**：设置指标警报

### MLflow

#### 实验管理
```python
import mlflow

# 开始实验
mlflow.set_experiment("my-experiment")

with mlflow.start_run():
    # 记录参数
    mlflow.log_param("learning_rate", 0.001)
    mlflow.log_param("batch_size", 32)

    # 训练模型
    model = train_model()

    # 记录指标
    mlflow.log_metric("loss", loss)
    mlflow.log_metric("accuracy", accuracy)

    # 记录模型
    mlflow.pytorch.log_model(model, "model")

    # 记录 artifacts
    mlflow.log_artifact("confusion_matrix.png")
```

#### 模型注册
```python
# 注册模型
mlflow.register_model(
    "runs:/<run_id>/model",
    "my-model"
)

# 加载模型
model = mlflow.pytorch.load_model("models:/my-model/Production")
```

#### 部署工具
```bash
# 启动MLflow服务器
mlflow server --host 0.0.0.0 --port 5000

# 部署模型
mlflow models serve -m "models:/my-model/Production" -p 1234

# 使用Docker部署
mlflow models build-docker -m "models:/my-model/Production" -n "my-model"
```

### 其他工具

#### Neptune
- **特点**：轻量级实验追踪工具，UI友好
- **适用场景**：团队协作、实验管理
- **学习资源**：Neptune官方文档

#### Comet ML
- **特点**：全功能实验管理平台
- **适用场景**：企业级实验管理、模型监控
- **特点**：支持模型生产监控

#### TensorBoard
- **特点**：TensorFlow官方可视化工具
- **适用场景**：TensorFlow/PyTorch训练可视化
- **使用**：
  ```python
  from torch.utils.tensorboard import SummaryWriter
  writer = SummaryWriter('runs/experiment-1')
  writer.add_scalar('Loss/train', loss, epoch)
  writer.close()
  ```
  ```bash
  tensorboard --logdir=runs
  ```

---

## 数据集工具

### Hugging Face Datasets

#### 数据集加载
```python
from datasets import load_dataset

# 加载数据集
dataset = load_dataset('imdb')
dataset = load_dataset('csv', data_files='data.csv')
dataset = load_dataset('json', data_files='data.json')

# 查看数据集
print(dataset)
print(dataset['train'][0])
print(dataset['train'].features)
```

#### 数据处理
```python
# 映射函数
def tokenize(example):
    return tokenizer(example['text'], truncation=True, padding='max_length')

tokenized_dataset = dataset.map(tokenize, batched=True)

# 过滤
filtered_dataset = dataset.filter(lambda x: len(x['text']) > 100)

# 选择列
dataset = dataset.remove_columns(['unused_column'])
dataset = dataset.rename_column('old_name', 'new_name')
```

#### 数据集共享
```python
# 上传数据集
from datasets import Dataset
dataset = Dataset.from_dict({'text': ['hello', 'world']})
dataset.push_to_hub('my-dataset')

# 使用私有数据集
dataset = load_dataset('username/dataset_name', use_auth_token=True)
```

### 其他工具

#### TensorFlow Datasets
- **特点**：TensorFlow官方数据集库
- **适用场景**：TensorFlow项目
- **示例**：
  ```python
  import tensorflow_datasets as tfds
  dataset, info = tfds.load('mnist', with_info=True, as_supervised=True)
  ```

#### PyTorch Dataset
- **特点**：PyTorch数据集抽象类
- **适用场景**：自定义数据集
- **示例**：
  ```python
  from torch.utils.data import Dataset, DataLoader

  class CustomDataset(Dataset):
      def __init__(self, data):
          self.data = data

      def __len__(self):
          return len(self.data)

      def __getitem__(self, idx):
          return self.data[idx]

  dataset = CustomDataset(data)
  dataloader = DataLoader(dataset, batch_size=32, shuffle=True)
  ```

#### WebDataset
- **特点**：基于tar文件的数据集格式，支持流式读取
- **适用场景**：大规模数据集、分布式训练
- **示例**：
  ```python
  import webdataset as wds
  dataset = wds.WebDataset('data-{000000..000099}.tar')
  ```

---

## 模型部署工具

### Docker

#### 容器化基础
```bash
# 拉取镜像
docker pull python:3.9-slim

# 运行容器
docker run -it python:3.9-slim bash

# 查看容器
docker ps
docker ps -a

# 停止容器
docker stop container_id
```

#### Dockerfile编写
```dockerfile
# Python应用示例
FROM python:3.9-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install -r requirements.txt

COPY . .

EXPOSE 8000

CMD ["python", "app.py"]
```

```dockerfile
# PyTorch模型服务
FROM pytorch/pytorch:1.9.0-cuda11.1-cudnn8-runtime

WORKDIR /app

COPY requirements.txt .
RUN pip install -r requirements.txt

COPY model.pth .
COPY app.py .

EXPOSE 8080

CMD ["python", "app.py"]
```

#### Docker Compose
```yaml
# docker-compose.yml
version: '3.8'

services:
  web:
    build: .
    ports:
      - "8000:8000"
    volumes:
      - .:/app
    environment:
      - DATABASE_URL=postgresql://user:pass@db:5432/db

  db:
    image: postgres:13
    environment:
      - POSTGRES_USER=user
      - POSTGRES_PASSWORD=pass
      - POSTGRES_DB=db
    volumes:
      - postgres_data:/var/lib/postgresql/data

volumes:
  postgres_data:
```

### Kubernetes

#### 基本概念
1. **Pod**：最小部署单元，包含一个或多个容器
2. **Service**：Pod的网络代理
3. **Deployment**：管理Pod的部署和更新
4. **ConfigMap**：存储配置数据
5. **Secret**：存储敏感数据

#### 部署配置
```yaml
# deployment.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: model-server
spec:
  replicas: 3
  selector:
    matchLabels:
      app: model-server
  template:
    metadata:
      labels:
        app: model-server
    spec:
      containers:
      - name: model-server
        image: model-server:latest
        ports:
        - containerPort: 8080
        resources:
          requests:
            memory: "1Gi"
            cpu: "500m"
          limits:
            memory: "2Gi"
            cpu: "1000m"
```

```yaml
# service.yaml
apiVersion: v1
kind: Service
metadata:
  name: model-service
spec:
  selector:
    app: model-server
  ports:
  - port: 80
    targetPort: 8080
  type: LoadBalancer
```

#### 扩缩容
```bash
# 手动扩缩容
kubectl scale deployment model-server --replicas=5

# 自动扩缩容
kubectl autoscale deployment model-server --min=3 --max=10 --cpu-percent=80
```

### 其他工具

#### TensorFlow Serving
- **特点**：TensorFlow模型服务系统
- **适用场景**：TensorFlow模型生产部署
- **使用**：
  ```bash
  tensorflow_model_server --port=8501 --rest_api_port=8500 \
    --model_name=my_model --model_base_path=/models/my_model
  ```

#### TorchServe
- **特点**：PyTorch模型服务系统
- **适用场景**：PyTorch模型生产部署
- **使用**：
  ```bash
  torch-model-archiver --model-name my_model \
    --version 1.0 --serialized-file model.pth \
    --handler image_classifier
  torchserve --start --model-store model_store \
    --models my_model.mar
  ```

#### Triton
- **特点**：NVIDIA推理服务器，支持多种框架
- **适用场景**：高性能推理、多模型服务
- **特点**：支持TensorFlow、PyTorch、ONNX等

---

## 版本控制

### Git

#### 基本操作
```bash
# 初始化仓库
git init

# 克隆仓库
git clone https://github.com/user/repo.git

# 添加文件
git add .  # 添加所有文件
git add file.py  # 添加特定文件

# 提交
git commit -m "feat: 添加新功能"

# 查看状态
git status

# 查看历史
git log
git log --oneline
git log --graph
```

#### 分支管理
```bash
# 创建分支
git branch feature-branch

# 切换分支
git checkout feature-branch
git switch feature-branch  # Git 2.23+

# 创建并切换
git checkout -b feature-branch
git switch -c feature-branch

# 合并分支
git checkout main
git merge feature-branch

# 删除分支
git branch -d feature-branch
git branch -D feature-branch  # 强制删除
```

#### 协作流程
```bash
# 拉取远程更新
git pull origin main

# 推送到远程
git push origin main

# 创建Pull Request
# 在GitHub/GitLab网页上操作

# 解决冲突
git merge feature-branch
# 编辑冲突文件
git add resolved-file.py
git commit -m "merge: 解决冲突"
```

### DVC

#### 数据版本控制
```bash
# 初始化DVC
dvc init

# 添加数据文件
dvc add data/train.csv

# 推送到远程存储
dvc push

# 拉取数据
dvc pull

# 查看数据版本
dvc dag
```

#### 模型版本控制
```bash
# 添加模型文件
dvc add model.pth

# 远程存储配置
dvc remote add -d myremote s3://mybucket/dvcstore
dvc remote modify myremote access_key_id 'xxx'
dvc remote modify myremote secret_access_key 'xxx'

# 推送模型
dvc push
```

#### 管道管理
```yaml
# dvc.yaml
stages:
  prepare:
    cmd: python prepare.py
    deps:
      - data/raw
    outs:
      - data/processed

  train:
    cmd: python train.py
    deps:
      - data/processed
      - train.py
    outs:
      - model.pth
    metrics:
      - metrics.json:
          cache: false
```

---

## 协作工具

### GitHub

#### 代码托管
1. **创建仓库**：在GitHub网页上创建新仓库
2. **克隆仓库**：`git clone https://github.com/user/repo.git`
3. **推送代码**：`git push origin main`
4. **分支保护**：设置分支保护规则

#### Issue管理
1. **创建Issue**：描述问题或功能请求
2. **标签管理**：使用标签分类Issue
3. **里程碑**：将Issue组织到里程碑中
4. **模板**：创建Issue模板

#### CI/CD
```yaml
# .github/workflows/python-app.yml
name: Python application

on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2

    - name: Set up Python
      uses: actions/setup-python@v2
      with:
        python-version: '3.9'

    - name: Install dependencies
      run: |
        python -m pip install --upgrade pip
        pip install -r requirements.txt

    - name: Lint with flake8
      run: |
        flake8 . --count --select=E9,F63,F7,F82 --show-source --statistics

    - name: Test with pytest
      run: |
        pytest
```

### GitLab

#### 私有部署
1. **安装GitLab**：使用Docker或Omnibus安装包
2. **配置**：设置域名、SSL证书、邮件服务
3. **用户管理**：创建用户、组、项目
4. **权限控制**：设置项目访问权限

#### CI/CD
```yaml
# .gitlab-ci.yml
stages:
  - test
  - build
  - deploy

test:
  stage: test
  script:
    - python -m pytest
  only:
    - merge_requests

build:
  stage: build
  script:
    - docker build -t my-image .
    - docker push my-image
  only:
    - main

deploy:
  stage: deploy
  script:
    - kubectl apply -f k8s/
  only:
    - main
```

#### 项目管理
1. **看板**：使用看板管理任务
2. **里程碑**：设置项目里程碑
3. **时间追踪**：记录任务时间
4. **Wiki**：项目文档

---

## 学习建议

### 工具选择
1. **初学者**：
   - 编程语言：Python
   - 数据处理：Pandas + NumPy
   - 可视化：Matplotlib + Seaborn
   - 开发环境：Jupyter Notebook
   - 版本控制：Git基础

2. **进阶者**：
   - 深度学习框架：PyTorch或TensorFlow
   - 实验管理：Weights & Biases
   - 开发环境：VS Code + Jupyter
   - 数据集：Hugging Face Datasets

3. **专业者**：
   - 部署工具：Docker + Kubernetes
   - 模型服务：TensorFlow Serving或TorchServe
   - CI/CD：GitHub Actions或GitLab CI
   - 监控：Prometheus + Grafana

### 学习顺序
1. **第1-2周**：Python基础 + NumPy + Pandas
2. **第3-4周**：Matplotlib + Seaborn + Jupyter
3. **第5-8周**：Scikit-learn + 机器学习基础
4. **第9-12周**：PyTorch或TensorFlow + 深度学习
5. **第13-16周**：Git + GitHub + 实验管理
6. **第17-20周**：Docker + 部署基础
7. **第21-24周**：项目实战 + 简历优化

### 实践方法
1. **项目驱动学习**：
   - 从简单项目开始（如房价预测）
   - 逐步增加复杂度（如图像分类、文本生成）
   - 完整走完数据收集、训练、部署全流程

2. **参与开源项目**：
   - 从文档改进开始
   - 修复简单bug
   - 实现小功能
   - 参与代码审查

3. **竞赛参与**：
   - Kaggle竞赛
   - 天池大赛
   - DataCastle
   - 和鲸社区

4. **社区交流**：
   - Stack Overflow提问和回答
   - GitHub Issues讨论
   - Reddit r/MachineLearning
   - 知乎、CSDN技术分享

5. **持续学习**：
   - 订阅技术博客（如Distill.pub、Towards Data Science）
   - 参加学术会议（如NeurIPS、ICML、CVPR）
   - 阅读最新论文
   - 参加在线课程和研讨会

---

**总计字数：约8500字**

**最后更新时间**：2024年

**维护者**：AI学习路线图项目组

**反馈渠道**：如有问题或建议，请提交Issue或Pull Request
