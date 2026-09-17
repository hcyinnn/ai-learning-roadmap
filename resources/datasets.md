# AI学习资源 - 常用数据集

## 概述

### 数据集分类

数据集是人工智能和机器学习研究的基础，根据不同的标准可以分为多种类型：

**按任务类型分类：**
- **监督学习数据集**：包含输入和对应的标签，如图像分类、文本分类等
- **无监督学习数据集**：只有输入数据，没有标签，用于聚类、降维等任务
- **强化学习数据集**：包含环境状态、动作和奖励信号
- **半监督学习数据集**：部分数据有标签，部分无标签
- **自监督学习数据集**：通过数据本身构造监督信号

**按数据类型分类：**
- **图像数据集**：用于计算机视觉任务
- **文本数据集**：用于自然语言处理任务
- **音频数据集**：用于语音识别、语音合成等任务
- **视频数据集**：用于视频理解、动作识别等任务
- **表格数据集**：用于传统机器学习任务
- **多模态数据集**：包含多种类型的数据

**按规模分类：**
- **小型数据集**：样本数在万级以下，适合学习和原型验证
- **中型数据集**：样本数在万级到百万级，适合大多数研究任务
- **大型数据集**：样本数在百万级以上，适合深度学习和大规模训练
- **超大规模数据集**：样本数在十亿级以上，适合大语言模型训练

### 选择建议

选择合适的数据集对于机器学习项目的成功至关重要：

1. **明确任务需求**：首先确定你的任务类型（分类、检测、分割等），然后选择对应领域的数据集
2. **考虑数据规模**：根据模型复杂度和计算资源选择合适规模的数据集
3. **评估数据质量**：检查数据的完整性、准确性和一致性
4. **关注数据分布**：确保数据集的分布与实际应用场景匹配
5. **考虑获取难度**：评估数据集的获取成本和使用限制
6. **查看基准结果**：了解数据集上的现有基准结果，便于比较

### 数据质量

高质量的数据集应具备以下特征：

- **完整性**：数据覆盖所有必要的类别和场景
- **准确性**：标签正确，数据无错误
- **一致性**：数据格式统一，标注标准一致
- **代表性**：数据能够代表实际应用场景
- **平衡性**：各类别样本数量相对均衡
- **时效性**：数据反映当前的实际情况

---

## 机器学习数据集

### 经典数据集

#### Iris（鸢尾花数据集）

**简介**：Iris数据集是机器学习领域最著名的数据集之一，由Fisher在1936年收集整理。该数据集包含150个样本，分为3个类别（Setosa、Versicolour、Virginica），每个类别50个样本。

**规模**：150个样本，4个特征

**特征**：
- 萼片长度（sepal length）
- 萼片宽度（sepal width）
- 花瓣长度（petal length）
- 花瓣宽度（petal width）

**格式**：CSV、ARFF

**用途**：
- 分类算法入门学习
- 模型性能基准测试
- 数据可视化教学

**获取方式**：
- scikit-learn内置：`from sklearn.datasets import load_iris`
- UCI机器学习仓库：https://archive.ics.uci.edu/ml/datasets/iris

**特点**：
- 数据量小，适合快速实验
- 类别平衡，无缺失值
- 特征维度低，易于可视化

#### Wine（葡萄酒数据集）

**简介**：Wine数据集来自UCI机器学习仓库，包含来自意大利同一地区三种不同葡萄酒的化学分析结果。

**规模**：178个样本，13个特征

**特征**：
- 酒精含量
- 苹果酸
- 灰分
- 灰分的碱度
- 镁
- 总酚含量
- 黄酮类化合物
- 非黄酮类酚类
- 原花青素
- 颜色强度
- 色调
- 稀释葡萄酒的OD280/OD315
- 脯氨酸

**格式**：CSV、ARFF

**用途**：
- 多分类算法测试
- 特征选择实验
- 数据标准化练习

**获取方式**：
- scikit-learn内置：`from sklearn.datasets import load_wine`
- UCI机器学习仓库：https://archive.ics.uci.edu/ml/datasets/wine

#### Boston Housing（波士顿房价数据集）

**简介**：Boston Housing数据集包含波士顿地区房屋的相关信息，用于预测房价中位数。该数据集由Harrison和Rubinfeld在1978年收集。

**规模**：506个样本，13个特征

**特征**：
- CRIM：城镇人均犯罪率
- ZN：占地面积超过25,000平方英尺的住宅用地比例
- INDUS：城镇非零售商业用地比例
- CHAS：查尔斯河虚拟变量（1 = 靠河；0 = 不靠河）
- NOX：一氧化氮浓度
- RM：每栋住宅的平均房间数
- AGE：1940年以前建成的自住单位比例
- DIS：到波士顿五个就业中心的加权距离
- RAD：径向公路的可达性指数
- TAX：每10,000美元的全额物业税率
- PTRATIO：城镇师生比例
- B：1000(Bk - 0.63)^2，其中Bk是城镇黑人比例
- LSTAT：人口中地位较低人群的百分比

**目标变量**：MEDV（自住房屋的中位数价格，单位：千美元）

**格式**：CSV

**用途**：
- 回归算法入门学习
- 房价预测模型开发
- 特征工程练习

**获取方式**：
- scikit-learn内置：`from sklearn.datasets import load_boston`
- UCI机器学习仓库

**注意**：由于该数据集存在一些伦理问题（如种族相关特征），在使用时需要注意。

#### MNIST（手写数字数据集）

**简介**：MNIST是一个大型的手写数字数据库，由NIST（美国国家标准与技术研究院）的Special Database 3和Special Database 1经过处理得到。它是机器学习领域最著名的基准数据集之一。

**规模**：70,000张图像（60,000训练 + 10,000测试）

**图像规格**：
- 尺寸：28×28像素
- 灰度图像
- 数字范围：0-9

**格式**：IDX格式（原始格式）、PNG、JPEG

**用途**：
- 图像分类入门学习
- 深度学习模型基准测试
- 神经网络架构比较

**获取方式**：
- 官方网站：http://yann.lecun.com/exdb/mnist/
- TensorFlow内置：`tf.keras.datasets.mnist`
- PyTorch内置：`torchvision.datasets.MNIST`
- Hugging Face：`datasets.load_dataset("mnist")`

**基准结果**：
- 线性分类器：约12%错误率
- K-Nearest Neighbors：约2.4%错误率
- 卷积神经网络：约0.5%错误率
- 人类性能：约2%错误率

#### CIFAR-10/100

**简介**：CIFAR-10和CIFAR-100是由加拿大高等研究院（CIFAR）收集整理的图像数据集，广泛用于计算机视觉研究。

**CIFAR-10**：
- **规模**：60,000张32×32彩色图像
- **类别**：10个类别（飞机、汽车、鸟、猫、鹿、狗、青蛙、马、船、卡车）
- **划分**：50,000训练 + 10,000测试
- **每类样本数**：6,000

**CIFAR-100**：
- **规模**：60,000张32×32彩色图像
- **类别**：100个类别，分为20个超类
- **划分**：50,000训练 + 10,000测试
- **每类样本数**：600

**格式**：Python pickle、PNG

**用途**：
- 图像分类研究
- 深度学习模型评估
- 数据增强技术验证

**获取方式**：
- 官方网站：https://www.cs.toronto.edu/~kriz/cifar.html
- TensorFlow内置：`tf.keras.datasets.cifar10` / `tf.keras.datasets.cifar100`
- PyTorch内置：`torchvision.datasets.CIFAR10` / `torchvision.datasets.CIFAR100`

**基准结果**（CIFAR-10）：
- VGG：约6.3%错误率
- ResNet-56：约6.97%错误率
- DenseNet：约3.46%错误率
- EfficientNet：约1.6%错误率

### 竞赛数据集

#### Kaggle数据集

**平台介绍**：Kaggle是全球最大的数据科学竞赛平台，提供大量高质量数据集和竞赛。

**热门数据集**：

1. **Titanic - Machine Learning from Disaster**
   - **简介**：泰坦尼克号乘客生存预测
   - **规模**：891训练样本 + 418测试样本
   - **特征**：乘客信息（年龄、性别、票价等）
   - **用途**：二分类入门学习

2. **House Prices - Advanced Regression Techniques**
   - **简介**：房价预测
   - **规模**：1,460训练样本 + 1,459测试样本
   - **特征**：80个房屋特征
   - **用途**：回归分析、特征工程

3. **Digit Recognizer**
   - **简介**：手写数字识别
   - **规模**：42,000训练样本 + 28,000测试样本
   - **格式**：CSV（像素值）
   - **用途**：图像分类

4. **Natural Language Processing with Disaster Tweets**
   - **简介**：灾难推文分类
   - **规模**：7,613训练样本 + 3,263测试样本
   - **用途**：文本分类、NLP入门

**获取方式**：
- 官网：https://www.kaggle.com/datasets
- Kaggle API：`kaggle datasets download -d <dataset-name>`

**使用建议**：
- 参与竞赛提升实战能力
- 阅读高分解决方案学习技巧
- 关注数据集讨论区获取见解

#### 天池数据集

**平台介绍**：天池是阿里巴巴集团旗下的大数据竞赛平台，提供丰富的中文数据集和竞赛。

**热门数据集**：

1. **阿里云天池大赛数据集**
   - 包含电商、金融、医疗等多个领域的数据集
   - 提供真实的业务场景数据

2. **中文NLP数据集**
   - 中文文本分类、情感分析、命名实体识别等
   - 数据质量高，标注规范

**获取方式**：
- 官网：https://tianchi.aliyun.com/dataset/

#### DataCastle数据集

**平台介绍**：DataCastle是国内专业的数据科学竞赛平台，提供多种类型的数据集。

**特点**：
- 专注于中文数据集
- 覆盖金融、医疗、教育等领域
- 提供详细的赛题说明和数据字典

**获取方式**：
- 官网：https://www.dcjingsai.com/

---

## 计算机视觉数据集

### 图像分类

#### ImageNet

**简介**：ImageNet是一个按照WordNet层次结构组织的大型图像数据库，是计算机视觉领域最重要的数据集之一。ImageNet大规模视觉识别挑战赛（ILSVRC）推动了深度学习的发展。

**规模**：
- 总图像数：超过1400万张
- ILSVRC子集：约120万张训练图像 + 50,000验证图像 + 100,000测试图像
- 类别数：1,000（ILSVRC）

**特点**：
- 高分辨率图像（通常缩放到224×224或299×299）
- 丰富的语义层次结构
- 包含边界框标注（部分数据）

**格式**：JPEG图像、XML标注

**用途**：
- 图像分类模型预训练
- 迁移学习基础模型
- 计算机视觉基准测试

**获取方式**：
- 官方网站：http://www.image-net.org/
- 需要申请访问权限
- 预训练模型可在PyTorch、TensorFlow等框架获取

**历史意义**：
- 2012年AlexNet在ImageNet上取得突破性成绩，开启了深度学习时代
- 推动了卷积神经网络的发展
- 催生了许多经典的网络架构

#### COCO（Common Objects in Context）

**简介**：COCO是一个大规模的目标检测、分割和图像描述数据集，由微软研究院发布。

**规模**：
- 训练集：118,287张图像
- 验证集：5,000张图像
- 测试集：40,670张图像
- 总标注数：超过250万个目标实例

**标注类型**：
- 目标检测（边界框）
- 实例分割（像素级掩码）
- 关键点检测（人体姿态）
- 图像描述（字幕）
- 全景分割

**类别**：80个常见物体类别

**格式**：JSON标注、JPEG图像

**用途**：
- 目标检测模型评估
- 实例分割研究
- 图像描述生成
- 多任务学习

**获取方式**：
- 官方网站：https://cocodataset.org/
- GitHub：https://github.com/cocodataset/cocoapi

**基准结果**：
- 目标检测：mAP约60%+（最先进模型）
- 实例分割：AP约50%+（最先进模型）

#### Open Images

**简介**：Open Images是谷歌发布的大型图像数据集，包含图像级别的标签、目标边界框、分割掩码和视觉关系。

**规模**：
- 总图像数：约900万张
- 标注图像：约200万张
- 类别数：600+目标类别
- 边界框数：约1,500万个

**特点**：
- 大规模、多样化
- 包含图像级标签和目标级标注
- 支持多种计算机视觉任务

**格式**：CSV、JSON

**用途**：
- 大规模图像分类
- 目标检测
- 视觉关系检测
- 图像分割

**获取方式**：
- 官方网站：https://storage.googleapis.com/openimages/web/index.html
- TensorFlow Datasets：`tfds.load('open_images_v4')`

#### Visual Genome

**简介**：Visual Genome是一个连接语言和视觉的大型数据集，包含详细的图像描述、目标、属性和关系。

**规模**：
- 图像数：108,249张
- 图像描述：4.2百万条
- 目标：1.8百万个
- 属性：1.7百万个
- 关系：2.3百万个

**特点**：
- 详细的场景图标注
- 密集的图像描述
- 支持视觉问答（VQA）

**格式**：JSON

**用途**：
- 图像描述生成
- 视觉问答
- 场景图生成
- 视觉推理

**获取方式**：
- 官方网站：http://visualgenome.org/
- API访问

### 目标检测

#### COCO Detection

**简介**：COCO Detection是COCO数据集的目标检测子集，是目标检测领域最权威的基准数据集之一。

**规模**：
- 训练集：118,287张图像
- 验证集：5,000张图像
- 测试集：40,670张图像
- 目标实例：超过250万个

**类别**：80个常见物体类别

**评估指标**：
- AP（Average Precision）：主要指标
- AP50、AP75：不同IoU阈值下的AP
- APs、APm、APl：不同尺度目标的AP

**基准结果**：
- 最先进模型：约60%+ mAP
- 两阶段检测器（Faster R-CNN系列）
- 单阶段检测器（YOLO、SSD系列）
- Transformer检测器（DETR系列）

**获取方式**：
- 官方网站：https://cocodataset.org/
- 使用COCO API

#### Pascal VOC（Visual Object Classes）

**简介**：Pascal VOC是目标检测和图像分割的经典数据集，从2005年到2012年每年举办挑战赛。

**规模**（VOC2012）：
- 训练集：5,717张图像
- 验证集：5,823张图像
- 测试集：10,991张图像（未公开标签）

**类别**：20个物体类别
- 人、鸟、猫、牛、狗、马、羊
- 飞机、自行车、船、巴士、汽车、摩托车、火车
- 瓶子、椅子、餐桌、盆栽植物、沙发、电视/显示器

**任务**：
- 分类
- 检测
- 分割
- 动作识别
- 人体布局

**格式**：XML标注、JPEG图像

**用途**：
- 目标检测入门学习
- 算法快速验证
- 教学和研究

**获取方式**：
- 官方网站：http://host.robots.ox.ac.uk/pascal/VOC/
- 可直接下载

#### Objects365

**简介**：Objects365是一个大规模目标检测数据集，包含365个类别，由旷视科技发布。

**规模**：
- 训练集：1,742,152张图像
- 验证集：80,000张图像
- 目标实例：超过1000万个

**类别**：365个物体类别

**特点**：
- 类别数量多，覆盖范围广
- 标注质量高
- 数据规模大

**格式**：JSON

**用途**：
- 大规模目标检测
- 模型预训练
- 通用目标检测器训练

**获取方式**：
- 官方网站：https://www.objects365.org/
- 需要申请下载

#### LVIS（Large Vocabulary Instance Segmentation）

**简介**：LVIS是一个大规模词汇实例分割数据集，旨在评估模型在长尾分布类别上的表现。

**规模**：
- 训练集：100,170张图像
- 验证集：19,822张图像
- 测试集：约20,000张图像

**类别**：1,203个物体类别

**特点**：
- 长尾分布：部分类别样本很少
- 细粒度标注
- 评估模型的泛化能力

**格式**：JSON

**用途**：
- 实例分割研究
- 长尾分布学习
- 开放词汇检测

**获取方式**：
- 官方网站：https://www.lvisdataset.org/
- 使用LVIS API

### 图像分割

#### COCO Segmentation

**简介**：COCO Segmentation包含实例分割和全景分割两种标注，是图像分割领域的重要基准。

**实例分割**：
- 提供每个目标实例的像素级掩码
- 用于评估模型区分不同实例的能力

**全景分割**：
- 同时包含 stuff（背景区域）和 thing（可数物体）
- 提供统一的分割评估

**评估指标**：
- 实例分割：AP（基于掩码IoU）
- 全景分割：PQ（Panoptic Quality）

#### Cityscapes

**简介**：Cityscapes是一个专注于城市街道场景理解的大规模数据集，由戴姆勒公司等机构发布。

**规模**：
- 精细标注：5,000张图像
- 粗略标注：20,000张图像
- 城市：50个欧洲城市

**类别**：
- 8个大类（平面、人、车辆、建筑、物体、自然、天空、空）
- 30个细分类别

**标注**：
- 像素级语义分割
- 实例分割
- 稠密深度估计

**图像规格**：
- 分辨率：2048×1024像素
- 格式：PNG

**用途**：
- 自动驾驶场景理解
- 城市街景分割
- 深度估计

**获取方式**：
- 官方网站：https://www.cityscapes-dataset.com/
- 需要注册申请

**基准结果**：
- 语义分割：mIoU约80%+（最先进模型）
- 实例分割：AP约40%+（最先进模型）

#### ADE20K

**简介**：ADE20K是由MIT发布的场景解析数据集，提供详细的场景语义标注。

**规模**：
- 训练集：20,210张图像
- 验证集：2,000张图像
- 测试集：3,000张图像

**类别**：
- 150个语义类别
- 包含物体和场景部件

**特点**：
- 标注详细，包含多个层次
- 覆盖室内外场景
- 支持场景解析任务

**格式**：PNG标注、JPEG图像

**用途**：
- 场景解析
- 语义分割
- 多尺度特征学习

**获取方式**：
- 官方网站：http://groups.csail.mit.edu/vision/datasets/ADE20K/
- 可直接下载

#### Mapillary Vistas

**简介**：Mapillary Vistas是一个大规模的街道级图像数据集，专注于自动驾驶场景理解。

**规模**：
- 训练集：18,000张图像
- 验证集：2,000张图像
- 测试集：5,000张图像

**类别**：
- 66个物体类别
- 包含实例级标注

**特点**：
- 高分辨率图像
- 多样化的拍摄条件
- 详细的标注

**格式**：PNG标注、JPEG图像

**用途**：
- 自动驾驶
- 街景理解
- 域适应研究

**获取方式**：
- 官方网站：https://www.mapillary.com/dataset/vistas
- 需要申请访问

### 人脸识别

#### LFW（Labeled Faces in the Wild）

**简介**：LFW是人脸识别领域最著名的基准数据集之一，用于评估无约束环境下的人脸识别算法。

**规模**：
- 图像数：13,233张
- 人数：5,749人
- 有两幅以上图像的人数：1,680人

**特点**：
- 自然环境下采集
- 光照、姿态、表情变化大
- 部分图像质量较低

**格式**：JPEG图像

**评估协议**：
- 6,000对人脸验证测试
- 报告平均准确率和标准差

**基准结果**：
- 人类性能：约97.53%
- 最先进深度学习模型：99.8%+

**获取方式**：
- 官方网站：http://vis-www.cs.umass.edu/lfw/
- 可直接下载

#### CelebA（CelebFaces Attributes）

**简介**：CelebA是一个大规模的人脸属性数据集，包含超过20万张名人图像和40个属性标注。

**规模**：
- 图像数：202,599张
- 人数：10,177人
- 属性数：40个

**属性**：
- 人口属性：性别、年龄等
- 面部特征：是否微笑、是否戴眼镜等
- 头部姿态：偏航角、俯仰角、翻滚角

**标注**：
- 5个关键点坐标
- 40个二值属性
- 边界框

**格式**：JPEG图像、TXT标注

**用途**：
- 人脸属性预测
- 人脸生成
- 人脸编辑
- 人脸重建

**获取方式**：
- 官方网站：http://mmlab.ie.cuhk.edu.hk/projects/CelebA.html
- 可直接下载

#### VGGFace

**简介**：VGGFace是由牛津大学VGG组发布的大规模人脸识别数据集，用于训练深度人脸识别模型。

**VGGFace1**：
- 图像数：2.6百万张
- 人数：2,622人

**VGGFace2**：
- 图像数：3.31百万张
- 人数：9,131人
- 每人平均362.6张图像

**特点**：
- 大规模、多样化
- 姿态、年龄变化大
- 包含不同种族

**格式**：JPEG图像

**用途**：
- 人脸识别模型训练
- 人脸验证
- 人脸聚类

**获取方式**：
- VGGFace2：http://www.robots.ox.ac.uk/~vgg/data/vgg_face2/
- 需要申请下载

#### MS-Celeb-1M

**简介**：MS-Celeb-1M是微软发布的大型人脸识别数据集，包含100万名人和1000万张图像。

**规模**：
- 人数：约100,000人
- 图像数：约10,000,000张

**特点**：
- 大规模、多样性
- 从网络爬取，包含噪声
- 需要清洗后使用

**格式**：JPEG图像

**用途**：
- 大规模人脸识别研究
- 人脸预训练模型

**获取方式**：
- 原始数据集已下架
- 可使用清洗后的子集

### 医学图像

#### ISIC（International Skin Imaging Collaboration）

**简介**：ISIC是皮肤镜图像数据集，用于皮肤病变分析和黑色素瘤检测。

**规模**：
- 训练集：25,331张图像
- 验证集：100张图像
- 测试集：1,000张图像

**类别**：
- 黑色素瘤
- 基底细胞癌
- 角化病
- 皮内痣
- 色素沉着

**格式**：JPEG图像、CSV标注

**用途**：
- 皮肤病变分类
- 黑色素瘤检测
- 医学图像分析入门

**获取方式**：
- 官方网站：https://challenge.isic-archive.com/
- 需要注册下载

#### ChestX-ray

**简介**：ChestX-ray是胸部X光数据集，由美国国立卫生研究院（NIH）发布，用于胸部疾病检测。

**规模**：
- 图像数：112,120张
- 人数：30,805人
- 疾病类别：14种

**疾病类别**：
- 肺不张
- 心脏肥大
- 胸腔积液
- 渗透
- 肺炎
- 气胸等

**格式**：PNG图像、CSV标注

**用途**：
- 胸部疾病分类
- 多标签分类
- 医学图像分析

**获取方式**：
- 官方网站：https://nihcc.app.box.com/v/ChestXray-NIHCC
- 可直接下载

#### MIMIC-CXR

**简介**：MIMIC-CXR是麻省理工学院发布的大型胸部X光数据集，包含放射学报告。

**规模**：
- 图像数：377,110张
- 报告数：227,835份
- 患者数：65,379人

**特点**：
- 包含完整的放射学报告
- 多标签分类
- 时间序列数据

**格式**：JPEG图像、JSON报告

**用途**：
- 医学图像-文本对齐
- 报告生成
- 多模态医学AI

**获取方式**：
- PhysioNet：https://physionet.org/content/mimic-cxr/
- 需要申请访问（需完成培训）

#### UK Biobank

**简介**：UK Biobank是一个大规模的生物医学数据库，包含50万英国参与者的健康数据。

**规模**：
- 参与者：500,000人
- 数据类型：基因组、影像、健康记录等

**影像数据**：
- 脑部MRI：约40,000人
- 心脏MRI：约40,000人
- 腹部MRI：约40,000人
- 骨密度扫描：约50,000人

**用途**：
- 疾病风险预测
- 医学影像分析
- 基因组学研究

**获取方式**：
- 官方网站：https://www.ukbiobank.ac.uk/
- 需要申请访问（研究用途）

---

## 自然语言处理数据集

### 文本分类

#### IMDB

**简介**：IMDB是电影评论情感分析数据集，是NLP领域最常用的基准数据集之一。

**规模**：
- 训练集：25,000条评论
- 测试集：25,000条评论
- 无标签数据：50,000条评论

**类别**：正面/负面情感（二分类）

**特点**：
- 长文本（平均约230词）
- 平衡的数据分布
- 包含无标签数据（可用于半监督学习）

**格式**：文本文件

**用途**：
- 情感分析入门
- 文本分类基准测试
- 迁移学习评估

**获取方式**：
- TensorFlow Datasets：`tfds.load('imdb_reviews')`
- Hugging Face：`datasets.load_dataset("imdb")`
- 官方网站：http://ai.stanford.edu/~amaas/data/sentiment/

**基准结果**：
- BERT：约95%准确率
- 人类性能：约90%准确率

#### Yelp Reviews

**简介**：Yelp Reviews是来自Yelp平台的商家评论数据集，用于情感分析和文本分类。

**规模**：
- 全量数据：约6,990,000条评论
- 分类子集：约560,000条评论（1-5星评分）

**特点**：
- 多类别分类（5个等级）
- 真实的用户评论
- 包含丰富的语言表达

**格式**：JSON

**用途**：
- 情感分析
- 评分预测
- 多类别文本分类

**获取方式**：
- Kaggle：https://www.kaggle.com/datasets/yelp-dataset/yelp-dataset
- 官方网站：https://www.yelp.com/dataset

#### Amazon Reviews

**简介**：Amazon Reviews是来自亚马逊平台的商品评论数据集，包含多个产品类别的评论。

**规模**：
- 总评论数：约2.33亿条
- 产品类别：29个
- 时间跨度：1996-2018年

**特点**：
- 大规模、多样化
- 包含评分和评论文本
- 包含产品元数据

**格式**：JSON、CSV

**用途**：
- 情感分析
- 产品推荐
- 文本分类
- 时序分析

**获取方式**：
- 官方网站：https://nijianmo.github.io/amazon/index.html
- 可直接下载

#### AG News

**简介**：AG News是新闻文章分类数据集，来源于AG's corpus of news articles。

**规模**：
- 训练集：120,000条新闻
- 测试集：7,600条新闻

**类别**：4个类别
- 世界新闻
- 体育新闻
- 财经新闻
- 科技新闻

**格式**：CSV

**用途**：
- 文本分类入门
- 快速模型验证
- 教学演示

**获取方式**：
- Hugging Face：`datasets.load_dataset("ag_news")`
- Kaggle

### 命名实体识别

#### CoNLL-2003

**简介**：CoNLL-2003是命名实体识别领域最著名的基准数据集，来源于路透社新闻。

**规模**：
- 训练集：14,987句子（203,621 tokens）
- 验证集：3,466句子（51,362 tokens）
- 测试集：3,684句子（46,435 tokens）

**实体类型**：
- PER（人名）
- ORG（组织名）
- LOC（地名）
- MISC（其他）

**格式**：CoNLL格式（每行一个token，空行分隔句子）

**用途**：
- NER模型基准测试
- 序列标注研究
- 预训练模型评估

**获取方式**：
- Hugging Face：`datasets.load_dataset("conll2003")`
- 需要注册（原始数据）

**基准结果**：
- BERT-large：约93% F1
- RoBERTa-large：约94% F1

#### OntoNotes

**简介**：OntoNotes是一个大规模多语言语料库，包含丰富的标注信息。

**规模**（英文）：
- 文档数：2,117
- 句子数：约175,000
- Token数：约2百万

**标注内容**：
- 命名实体识别（18种实体类型）
- 词性标注
- 句法分析
- 共指消解
- 语义角色标注

**格式**：CoNLL格式

**用途**：
- NER研究
- 共指消解
- 多任务学习

**获取方式**：
- LDC：https://catalog.ldc.upenn.edu/LDC2013T19
- 需要购买（学术用途有折扣）

#### WNUT（Noisy User Generated Text）

**简介**：WNUT专注于社交媒体等用户生成文本中的命名实体识别。

**WNUT-2017**：
- 训练集：3,394句子
- 验证集：1,009句子
- 测试集：1,287句子

**特点**：
- 社交媒体文本
- 语言不规范
- 实体稀疏

**格式**：CoNLL格式

**用途**：
- 社交媒体NER
- 噪声文本处理
- 域适应研究

**获取方式**：
- GitHub：https://github.com/leondz/emerging_entities_17

#### Few-NERD

**简介**：Few-NERD是一个大规模的少样本NER数据集，支持少样本和零样本学习。

**规模**：
- 实体数：188,238个
- 句子数：188,238个
- 类别数：66种细粒度实体类型

**任务**：
- Few-shot NER
- Zero-shot NER
- Supervised NER

**格式**：CoNLL格式

**用途**：
- 少样本学习
- 零样本学习
- 细粒度实体识别

**获取方式**：
- GitHub：https://github.com/thunlp/Few-NERD

### 机器翻译

#### WMT（Workshop on Machine Translation）

**简介**：WMT是机器翻译领域最重要的评测活动，提供多种语言对的平行语料。

**热门语言对**：
- English-German
- English-French
- English-Chinese
- English-Russian

**规模**：
- 训练数据：数百万句对
- 验证数据：数千句对
- 测试数据：数千句对

**特点**：
- 高质量的翻译数据
- 标准化的评测协议
- 包含多种测试集（新闻、通用领域等）

**格式**：文本文件（每行一个句子）

**用途**：
- 机器翻译研究
- 翻译模型评估
- 多语言模型训练

**获取方式**：
- 官方网站：http://statmt.org/wmt23/
- 可直接下载

#### IWSLT（International Conference on Spoken Language Translation）

**简介**：IWSLT专注于口语翻译，提供语音和文本的翻译数据。

**语言对**：
- English-German
- English-Chinese
- English-Arabic等

**特点**：
- 口语化文本
- 包含语音数据
- TED演讲风格

**格式**：文本文件、音频文件

**用途**：
- 口语翻译
- 语音翻译
- 跨模态翻译

**获取方式**：
- 官方网站：https://iwslt.org/
- 可直接下载

#### OPUS

**简介**：OPUS是一个大规模的平行语料库集合，包含多种语言对的翻译数据。

**规模**：
- 语言对：90+种
- 句对数：数十亿
- 来源：联合国、欧洲议会、字幕等

**特点**：
- 数据来源多样
- 包含对齐质量评分
- 持续更新

**格式**：文本文件、TMX格式

**用途**：
- 机器翻译训练
- 多语言研究
- 跨语言迁移学习

**获取方式**：
- 官方网站：http://opus.nlpl.eu/
- 可直接下载

#### UN Parallel Corpus

**简介**：联合国平行语料库包含联合国文档的六种官方语言翻译。

**语言**：阿拉伯文、中文、英文、法文、俄文、西班牙文

**规模**：
- 句对数：约1100万
- 文档数：约11,000份

**格式**：文本文件

**用途**：
- 多语言机器翻译
- 国际组织文档翻译

**获取方式**：
- GitHub：https://github.com/machinetranslator/un

### 问答

#### SQuAD（Stanford Question Answering Dataset）

**简介**：SQuAD是阅读理解领域最著名的数据集，由斯坦福大学发布。

**SQuAD 1.1**：
- 文章数：536篇
- 问题数：107,785个
- 答案：文章中的片段

**SQuAD 2.0**：
- 在SQuAD 1.1基础上增加无法回答的问题
- 问题数：150,000+个

**特点**：
- 答案是文章中的连续片段
- 包含无法回答的问题（2.0版本）
- 众包标注

**格式**：JSON

**评估指标**：
- Exact Match（EM）
- F1 Score

**基准结果**：
- BERT-large：约93% F1（1.1版本）
- ALBERT：约89% EM（2.0版本）

**获取方式**：
- 官方网站：https://rajpurkar.github.io/SQuAD-explorer/
- 可直接下载

#### Natural Questions

**简介**：Natural Questions是谷歌发布的大规模问答数据集，问题来源于真实的Google搜索。

**规模**：
- 训练集：307,373个问题
- 验证集：7,830个问题
- 测试集：7,842个问题

**特点**：
- 真实的用户问题
- 长答案（段落）和短答案（实体）
- Wikipedia作为知识来源

**格式**：JSONL

**用途**：
- 开放域问答
- 阅读理解
- 信息检索

**获取方式**：
- GitHub：https://github.com/google-research-datasets/natural-questions
- 可直接下载

#### TriviaQA

**简介**：TriviaQA是一个大规模的问答数据集，包含从网络收集的问答对。

**规模**：
- 训练集：约87,000个问题
- 验证集：约11,000个问题
- 测试集：约11,000个问题

**特点**：
- 问题来源多样（网络、维基百科）
- 包含证据文档
- 需要多跳推理

**格式**：JSON

**用途**：
- 开放域问答
- 信息检索
- 多文档阅读理解

**获取方式**：
- 官方网站：http://nlp.cs.washington.edu/triviaqa/
- 可直接下载

#### MS MARCO

**简介**：MS MARCO是微软发布的大规模阅读理解和问答数据集，问题来源于真实的Bing搜索日志。

**规模**：
- 文档数：3,563,535个
- 问题数：1,010,916个
- 排序任务：约900万相关性标注

**任务**：
- 段落排序
- 问答
- 生成式问答
- 摘要

**格式**：TSV

**用途**：
- 信息检索
- 阅读理解
- 问答系统

**获取方式**：
- 官方网站：https://microsoft.github.io/msmarco/
- 可直接下载

### 对话

#### Persona-Chat

**简介**：Persona-Chat是一个用于开放域对话的数据集，每个对话者都有一个角色描述。

**规模**：
- 对话数：10,907个
- 角色数：1,155个
- 角色描述数：4,184个

**特点**：
- 包含角色描述
- 鼓励个性化对话
- 自然的对话风格

**格式**：JSON

**用途**：
- 个性化对话系统
- 角色扮演对话
- 对话生成

**获取方式**：
- GitHub：https://github.com/facebookresearch/ParlAI
- ParlAI框架内置

#### DailyDialog

**简介**：DailyDialog是一个日常对话数据集，对话内容贴近日常生活。

**规模**：
- 对话数：13,118个
- 话语数：101,961个
- 平均每对话：7.9轮

**特点**：
- 日常话题
- 包含情感和意图标注
- 自然的对话风格

**标注**：
- 情感标签（7种）
- 对话行为标签（4种）

**格式**：TXT

**用途**：
- 日常对话系统
- 情感分析
- 对话行为识别

**获取方式**：
- 官方网站：http://yanran.li/dailydialog
- 可直接下载

#### Ubuntu Dialogue Corpus

**简介**：Ubuntu Dialogue Corpus是从Ubuntu聊天室收集的大规模对话数据集。

**规模**：
- 对话数：约100万个
- 话语数：约700万条
- 时间跨度：2004-2015年

**特点**：
- 技术支持对话
- 多轮对话
- 包含上下文

**格式**：CSV

**用途**：
- 多轮对话系统
- 对话检索
- 技术支持对话

**获取方式**：
- GitHub：https://github.com/rkadlec/ubuntu-ranking-dataset-creator
- 可直接下载

#### MultiWOZ

**简介**：MultiWOZ是一个大规模多领域任务型对话数据集。

**规模**：
- 对话数：10,438个
- 领域数：7个
- 平均每对话：13.7轮

**领域**：
- 餐厅
- 酒店
- 景点
- 出租车
- 火车
- 医院
- 警察局

**标注**：
- 对话状态
- 对话行为
- 目标

**格式**：JSON

**用途**：
- 任务型对话系统
- 对话状态跟踪
- 对话策略学习

**获取方式**：
- GitHub：https://github.com/budzianowski/multiwoz
- 可直接下载

### 大语言模型

#### The Pile

**简介**：The Pile是EleutherAI发布的大规模语言模型训练数据集，包含多样化的文本来源。

**规模**：
- 总大小：825 GB
- Token数：约3000亿
- 子集数：22个

**数据来源**：
- 学术论文（ArXiv、PubMed）
- 书籍（BookCorpus、Gutenberg）
- 代码（GitHub）
- 网页（CommonCrawl、WebText）
- 百科（Wikipedia）
- 对话（Ubuntu IRC）

**特点**：
- 数据来源多样
- 经过质量筛选
- 支持大规模语言模型训练

**格式**：JSONL、zst压缩

**用途**：
- 大语言模型预训练
- 数据混合研究
- 语言模型评估

**获取方式**：
- 官方网站：https://pile.eleuther.ai/
- Hugging Face：`datasets.load_dataset("the_pile")`

#### RedPajama

**简介**：RedPajama是开源的LLM训练数据集，旨在复现LLaMA的训练数据。

**规模**：
- 总Token数：约1.2万亿
- 版本：v1和v2

**数据来源**：
- CommonCrawl
- C4
- GitHub
- ArXiv
- Wikipedia
- Books
- StackExchange

**特点**：
- 开源、可复现
- 经过质量过滤
- 支持大规模训练

**格式**：JSONL、parquet

**用途**：
- 大语言模型预训练
- 开源LLM研究

**获取方式**：
- GitHub：https://github.com/togethercomputer/RedPajama-Data
- Hugging Face

#### SlimPajama

**简介**：SlimPajama是RedPajama的清洗版本，经过进一步的质量过滤。

**规模**：
- 总Token数：约6270亿
- 去重后数据

**特点**：
- 更高质量
- 更小规模
- 训练效率更高

**格式**：JSONL

**用途**：
- 高效LLM训练
- 质量敏感的预训练

**获取方式**：
- Hugging Face：`Cerebras/SlimPajama-627B`

#### Dolma

**简介**：Dolma是AI2发布的开放预训练数据集，用于OLMo模型训练。

**规模**：
- 总Token数：约3万亿
- 文档数：约30亿

**数据来源**：
- Web
- 学术论文
- 代码
- 书籍
- 百科

**特点**：
- 完全开源
- 详细的处理文档
- 可复现

**格式**：JSONL

**用途**：
- 开放语言模型研究
- 数据质量研究

**获取方式**：
- GitHub：https://github.com/allenai/dolma
- Hugging Face

---

## 语音数据集

### 语音识别

#### LibriSpeech

**简介**：LibriSpeech是一个大规模的英语语音识别数据集，来源于有声读物。

**规模**：
- 训练集：960小时（clean-100 + clean-360 + other-500）
- 验证集：5小时（clean）+ 5小时（other）
- 测试集：5小时（clean）+ 5小时（other）

**特点**：
- 高质量录音
- 朗读语音
- 包含转录文本

**格式**：FLAC音频、TXT转录

**评估指标**：
- WER（Word Error Rate）

**基准结果**：
- 传统GMM-HMM：约15% WER
- 深度学习模型：约3% WER
- 最先进模型：约2% WER

**获取方式**：
- 官方网站：http://www.openslr.org/12
- OpenSLR可直接下载

#### Common Voice

**简介**：Common Voice是Mozilla发起的众包语音数据集，支持多种语言。

**规模**：
- 语言数：100+
- 总时长：超过2,500小时
- 英语：约2,000小时

**特点**：
- 多语言支持
- 众包录制
- 包含说话人信息
- 包含人口统计信息

**格式**：MP3音频、TSV转录

**用途**：
- 多语言语音识别
- 语音模型预训练
- 说话人识别

**获取方式**：
- 官方网站：https://commonvoice.mozilla.org/
- 可直接下载

#### AISHELL

**简介**：AISHELL是中文语音识别数据集，由北京希尔贝壳科技有限公司发布。

**AISHELL-1**：
- 时长：约178小时
- 说话人：400人
- 句子数：152,326句

**AISHELL-2**：
- 时长：约1000小时
- 说话人：1991人
- 句子数：486,547句

**特点**：
- 中文普通话
- 高质量录音
- 包含拼音标注

**格式**：WAV音频、TXT转录

**用途**：
- 中文语音识别
- 语音模型研究

**获取方式**：
- OpenSLR：http://www.openslr.org/33/
- 需要申请下载

#### THCHS-30

**简介**：THCHS-30是清华大学发布的中文语音数据集。

**规模**：
- 时长：约30小时
- 说话人：60人
- 句子数：13,689句

**特点**：
- 安静环境录制
- 标准普通话
- 包含声学和语言模型

**格式**：WAV音频、TXT转录

**用途**：
- 中文语音识别入门
- 语音识别教学

**获取方式**：
- GitHub：https://github.com/SpanQAQ/THCHS-30
- 可直接下载

### 语音合成

#### LJSpeech

**简介**：LJSpeech是英语语音合成领域最常用的数据集，由单一女性说话人录制。

**规模**：
- 时长：约24小时
- 句子数：13,100句
- 采样率：22,050 Hz

**特点**：
- 单一说话人
- 高质量录音
- 覆盖多种句式

**格式**：WAV音频、TXT转录

**用途**：
- TTS（Text-to-Speech）模型训练
- 语音合成基准测试

**获取方式**：
- 官方网站：https://keithito.com/LJ-Speech-Dataset/
- 可直接下载

**基准结果**：
-  MOS评分：约4.0+（最先进模型）

#### VCTK

**简介**：VCTK是多说话人英语语音合成数据集。

**规模**：
- 说话人：110人
- 时长：约44小时
- 句子数：44,238句

**特点**：
- 多说话人
- 包含不同口音
- 包含说话人信息

**格式**：WAV音频、TXT转录

**用途**：
- 多说话人TTS
- 说话人转换
- 语音克隆

**获取方式**：
- 官方网站：http://www.udialogue.org/download/cstr-vctk-corpus.html
- 可直接下载

#### LibriTTS

**简介**：LibriTTS是从LibriSpeech派生的语音合成数据集。

**规模**：
- 时长：约585小时
- 说话人：2,456人
- 句子数：约150万句

**特点**：
- 多说话人
- 高质量录音
- 包含时间戳

**格式**：WAV音频、TXT转录

**用途**：
- 多说话人TTS
- 大规模语音合成

**获取方式**：
- 官方网站：http://www.openslr.org/60/
- OpenSLR可直接下载

#### AISHELL-3

**简介**：AISHELL-3是中文多说话人语音合成数据集。

**规模**：
- 时长：约85小时
- 说话人：218人
- 句子数：约12万句

**特点**：
- 中文普通话
- 多说话人
- 包含情感多样性

**格式**：WAV音频、TXT转录

**用途**：
- 中文TTS
- 多说话人语音合成

**获取方式**：
- OpenSLR：http://www.openslr.org/93/
- 需要申请下载

### 音乐

#### MAESTRO

**简介**：MAESTRO是钢琴音乐数据集，由谷歌Magenta团队发布。

**规模**：
- 时长：约200小时
- 表演数：1,276场
- 时间跨度：2004-2018年

**特点**：
- 专业钢琴演奏
- 包含MIDI和音频对齐
- 包含表演者信息

**格式**：WAV音频、MIDI

**用途**：
- 音乐生成
- 音乐转录
- 音乐信息检索

**获取方式**：
- 官方网站：https://magenta.tensorflow.org/datasets/maestro
- 可直接下载

#### NSynth

**简介**：NSynth是大规模的乐器音色数据集，由谷歌Magenta团队发布。

**规模**：
- 样本数：305,979个
- 乐器数：1,006种
- 音高范围：88个

**特点**：
- 单音音色
- 包含音高、速度、音色信息
- 高质量音频

**格式**：WAV音频、TFRecord

**用途**：
- 音色合成
- 音乐生成
- 音频分析

**获取方式**：
- 官方网站：https://magenta.tensorflow.org/datasets/nsynth
- 可直接下载

#### FMA（Free Music Archive）

**简介**：FMA是一个大规模的音乐数据集，包含多种音乐风格。

**规模**：
- 曲目数：106,574首
- 时长：约899小时
- 风格数：161种

**特点**：
- 免费音乐
- 包含元数据
- 包含特征提取

**格式**：MP3音频、CSV元数据

**用途**：
- 音乐分类
- 音乐推荐
- 音乐信息检索

**获取方式**：
- GitHub：https://github.com/mdeff/fma
- 可直接下载

#### Million Song Dataset

**简介**：Million Song Dataset是大规模的音乐信息检索数据集。

**规模**：
- 曲目数：100万首
- 大小：约280 GB

**特点**：
- 包含音频特征
- 包含元数据
- 包含用户行为数据

**格式**：HDF5

**用途**：
- 音乐推荐
- 音乐信息检索
- 音乐分析

**获取方式**：
- 官方网站：https://labrosa.ee.columbia.edu/millionsong/
- 可直接下载

---

## 推荐系统数据集

### 电影推荐

#### MovieLens

**简介**：MovieLens是推荐系统领域最著名的数据集，由明尼苏达大学GroupLens研究组发布。

**MovieLens 100K**：
- 评分记录：100,000条
- 用户数：943人
- 电影数：1,682部
- 评分范围：1-5星

**MovieLens 1M**：
- 评分记录：1,000,209条
- 用户数：6,040人
- 电影数：3,706部
- 评分范围：1-5星

**MovieLens 10M**：
- 评分记录：10,000,054条
- 用户数：69,878人
- 电影数：10,677部

**MovieLens 25M**：
- 评分记录：25,000,095条
- 用户数：162,541人
- 电影数：62,423部

**格式**：CSV、DAT

**用途**：
- 协同过滤研究
- 推荐算法评估
- 推荐系统入门

**获取方式**：
- 官方网站：https://grouplens.org/datasets/movielens/
- 可直接下载

#### Netflix Prize

**简介**：Netflix Prize是Netflix举办的推荐系统竞赛数据集。

**规模**：
- 评分记录：100,480,507条
- 用户数：480,189人
- 电影数：17,770部
- 时间跨度：1999-2005年

**格式**：TXT

**用途**：
- 推荐系统研究
- 竞赛基准

**获取方式**：
- 原始数据已不再公开
- 可使用公开的子集或类似数据

#### TMDB（The Movie Database）

**简介**：TMDB是一个社区驱动的电影数据库，包含丰富的电影元数据。

**规模**：
- 电影数：约100万部
- 包含演员、导演、剧情简介等

**特点**：
- 实时更新
- 包含海报、剧照
- API访问

**格式**：JSON、CSV

**用途**：
- 电影推荐
- 内容分析
- 知识图谱构建

**获取方式**：
- 官方网站：https://www.themoviedb.org/
- API：https://developers.themoviedb.org/

#### IMDB

**简介**：IMDB是互联网电影数据库，包含电影、电视节目的详细信息和用户评分。

**规模**：
- 电影数：约50万部
- 评分记录：数百万条

**特点**：
- 权威的电影信息
- 用户评分
- 详细元数据

**格式**：TSV

**用途**：
- 电影推荐
- 情感分析
- 内容过滤

**获取方式**：
- 官方网站：https://www.imdb.com/interfaces/
- 可直接下载

### 电商推荐

#### Amazon Product

**简介**：Amazon Product数据集包含亚马逊平台的商品评论和元数据。

**规模**：
- 评论数：约2.33亿条
- 产品类别：29个
- 时间跨度：1996-2018年

**特点**：
- 包含评分、评论、购买行为
- 包含产品元数据
- 时间序列数据

**格式**：JSON、CSV

**用途**：
- 产品推荐
- 情感分析
- 市场分析

**获取方式**：
- 官方网站：https://nijianmo.github.io/amazon/index.html
- 可直接下载

#### Alibaba

**简介**：阿里巴巴提供的电商推荐数据集，来源于真实业务场景。

**数据集**：
- Tmall数据集
- Taobao数据集
- Alimama数据集

**特点**：
- 真实的业务数据
- 包含用户行为序列
- 包含丰富的上下文信息

**格式**：CSV、JSON

**用途**：
- 电商推荐
- 行为预测
- 广告推荐

**获取方式**：
- 天池平台：https://tianchi.aliyun.com/dataset/

#### Retailrocket

**简介**：Retailrocket是电商网站的用户行为数据集。

**规模**：
- 事件数：2,756,101条
- 用户数：1,407,580人
- 商品数：220,853个

**事件类型**：
- 查看
- 加入购物车
- 交易

**格式**：CSV

**用途**：
- 行为预测
- 推荐系统
- 转化率预测

**获取方式**：
- Kaggle：https://www.kaggle.com/retailrocket/ecommerce-dataset

### 其他推荐

#### Last.fm

**简介**：Last.fm是音乐推荐数据集，包含用户的听歌记录。

**规模**：
- 用户数：约36万人
- 艺术家数：约18万
- 听歌记录：约1900万条

**特点**：
- 包含用户听歌历史
- 包含艺术家标签
- 包含社交关系

**格式**：CSV、JSON

**用途**：
- 音乐推荐
- 标签推荐
- 社交推荐

**获取方式**：
- GroupLens：https://grouplens.org/datasets/lastfm/
- Kaggle

#### Yelp

**简介**：Yelp数据集包含商家信息和用户评论，可用于推荐系统研究。

**规模**：
- 商家数：约15万家
- 评论数：约699万条
- 用户数：约199万人

**特点**：
- 包含地理位置信息
- 包含用户社交关系
- 包含丰富的元数据

**格式**：JSON

**用途**：
- 商家推荐
- 位置推荐
- 社交推荐

**获取方式**：
- 官方网站：https://www.yelp.com/dataset
- 可直接下载

#### Goodreads

**简介**：Goodreads是图书推荐数据集，包含用户的阅读记录和评分。

**规模**：
- 用户数：约600万人
- 书籍数：约100万本
- 评分记录：约2.28亿条

**特点**：
- 包含用户书架信息
- 包含用户评论
- 包含书籍元数据

**格式**：CSV、JSON

**用途**：
- 图书推荐
- 阅读兴趣分析
- 社交推荐

**获取方式**：
- Kaggle：https://www.kaggle.com/jealousleopard/goodreadsbooks

---

## 强化学习数据集

### 游戏

#### Atari

**简介**：Atari是强化学习领域最经典的游戏环境之一，包含多种雅达利游戏。

**游戏数量**：57种游戏（Atari 2600）

**特点**：
- 离散动作空间
- 像素级观测
- 稀疏奖励

**格式**：ROM文件、图像帧

**用途**：
- 强化学习入门
- 深度强化学习研究
- 算法比较

**获取方式**：
- OpenAI Gym：`gym.make('Breakout-v0')`
- ALE（Arcade Learning Environment）

**经典游戏**：
- Breakout（打砖块）
- Pong（乒乓球）
- Space Invaders（太空侵略者）
- Qbert（跳方块）

#### OpenAI Gym

**简介**：OpenAI Gym是一个强化学习环境库，提供多种标准环境。

**环境类型**：
- 经典控制：CartPole、MountainCar、Pendulum等
- Atari游戏
- 2D/3D机器人仿真
- MuJoCo物理引擎

**特点**：
- 标准化的API
- 丰富的环境
- 社区贡献

**格式**：Python包

**用途**：
- 强化学习算法开发
- 算法评估
- 教学演示

**获取方式**：
- PyPI：`pip install gym`
- GitHub：https://github.com/openai/gym

#### MuJoCo

**简介**：MuJoCo是一个物理引擎，用于机器人和生物力学仿真。

**特点**：
- 高精度物理仿真
- 快速渲染
- 支持复杂动力学

**环境**：
- 机器人控制
- 人体运动
- 物体操作

**格式**：XML模型文件

**用途**：
- 机器人强化学习
- 运动控制
- 物理仿真

**获取方式**：
- 官方网站：https://mujoco.org/
- DeepMind Control Suite

#### StarCraft

**简介**：StarCraft是即时战略游戏，是多智能体强化学习的重要测试平台。

**环境**：
- PySC2（DeepMind）
- SMAC（StarCraft Multi-Agent Challenge）

**特点**：
- 复杂的状态空间
- 多智能体协作
- 长期规划

**格式**：游戏环境

**用途**：
- 多智能体强化学习
- 战略规划
- 团队协作

**获取方式**：
- PySC2：https://github.com/deepmind/pysc2
- SMAC：https://github.com/oxwhirl/smac

### 机器人

#### RoboTurk

**简介**：RoboTurk是一个大规模的机器人操作数据集，通过众包方式收集。

**规模**：
- 演示数：超过2,000个
- 任务：多种操作任务

**特点**：
- 真实的人类演示
- 多样化的任务
- 机器人操作数据

**格式**：HDF5

**用途**：
- 模仿学习
- 机器人操作
- 任务规划

**获取方式**：
- 官方网站：http://roboturk.stanford.edu/

#### D4RL

**简介**：D4RL是离线强化学习基准数据集，包含多种环境的专家数据。

**环境**：
- MuJoCo任务
- Flow交通仿真
- AntMaze导航

**特点**：
- 离线数据
- 多种质量水平
- 标准化基准

**格式**：HDF5

**用途**：
- 离线强化学习
- 策略评估
- 算法比较

**获取方式**：
- GitHub：https://github.com/rail-berkeley/d4rl

#### RL Unplugged

**简介**：RL Unplugged是DeepMind发布的离线强化学习数据集。

**规模**：
- 环境数：15种
- 数据量：TB级

**特点**：
- 高质量数据
- 多种环境
- 标准化格式

**格式**：TFRecord

**用途**：
- 离线强化学习研究
- 大规模训练

**获取方式**：
- GitHub：https://github.com/deepmind/deepmind-research/tree/master/rl_unplugged

---

## 时间序列数据集

### 金融

#### Yahoo Finance

**简介**：Yahoo Finance提供全球金融市场的历史数据。

**数据类型**：
- 股票价格
- 指数数据
- 基金数据
- 期货数据

**特点**：
- 实时更新
- 全球市场覆盖
- 免费API访问

**格式**：CSV、JSON

**用途**：
- 股票预测
- 金融分析
- 量化交易

**获取方式**：
- 官方网站：https://finance.yahoo.com/
- Python库：`yfinance`

#### Quandl

**简介**：Quandl是金融和经济数据平台，提供多种数据源。

**数据类型**：
- 金融数据
- 经济指标
- 人口统计数据
- 能源数据

**特点**：
- 数据质量高
- API访问
- 包含多种数据源

**格式**：CSV、JSON

**用途**：
- 金融分析
- 经济研究
- 数据科学

**获取方式**：
- 官方网站：https://www.quandl.com/
- Python库：`quandl`

#### Kaggle Financial

**简介**：Kaggle提供多种金融相关的数据集和竞赛。

**热门数据集**：
- Jigsaw Toxic Comment Classification
- Two Sigma Financial Modeling Challenge
- Jane Street Market Prediction

**格式**：CSV

**用途**：
- 金融预测
- 风险管理
- 量化交易

**获取方式**：
- Kaggle：https://www.kaggle.com/datasets?search=finance

### 气象

#### NOAA（National Oceanic and Atmospheric Administration）

**简介**：NOAA提供全球气象和海洋数据。

**数据类型**：
- 地面观测
- 卫星数据
- 海洋数据
- 气候数据

**特点**：
- 数据权威
- 时间跨度长
- 全球覆盖

**格式**：CSV、NetCDF

**用途**：
- 天气预报
- 气候研究
- 环境监测

**获取方式**：
- 官方网站：https://www.noaa.gov/
- Climate Data Online

#### ERA5

**简介**：ERA5是欧洲中期天气预报中心（ECMWF）发布的全球再分析数据集。

**规模**：
- 时间跨度：1979年至今
- 空间分辨率：0.25°×0.25°
- 时间分辨率：1小时

**特点**：
- 高分辨率
- 全球覆盖
- 多种变量

**格式**：NetCDF、GRIB

**用途**：
- 天气预报
- 气候研究
- 可再生能源分析

**获取方式**：
- CDS：https://cds.climate.copernicus.eu/
- 需要注册

#### WeatherBench

**简介**：WeatherBench是天气预报基准数据集，用于评估机器学习天气预报模型。

**特点**：
- 标准化评估
- 包含多种变量
- 便于模型比较

**格式**：NetCDF

**用途**：
- 天气预报研究
- 机器学习模型评估

**获取方式**：
- GitHub：https://github.com/pangeo-data/WeatherBench

### 医疗

#### MIMIC-III

**简介**：MIMIC-III是麻省理工学院发布的重症监护数据库。

**规模**：
- 患者数：约40,000人
- 住院次数：约53,000次
- 时间跨度：2001-2012年

**数据类型**：
- 生命体征
- 实验室检查
- 用药记录
- 诊断编码
- 医疗记录

**格式**：CSV

**用途**：
- 临床预测
- 患者监护
- 医学研究

**获取方式**：
- PhysioNet：https://physionet.org/content/mimiciii/
- 需要申请访问（需完成培训）

#### PhysioNet

**简介**：PhysioNet是生理信号数据库，提供多种医疗数据集。

**数据类型**：
- 心电图（ECG）
- 脑电图（EEG）
- 血压
- 血氧

**特点**：
- 数据质量高
- 包含临床数据
- 开放获取

**格式**：WFDB、CSV

**用途**：
- 生理信号分析
- 疾病预测
- 医学研究

**获取方式**：
- 官方网站：https://physionet.org/
- 可直接下载（部分数据需要申请）

#### eICU

**简介**：eICU是多中心ICU数据库，包含来自美国多个ICU的数据。

**规模**：
- 患者数：约139,000人
- ICU停留数：约200,000次

**特点**：
- 多中心数据
- 实时生命体征
- 丰富的临床数据

**格式**：CSV

**用途**：
- 临床预测
- 多中心研究
- 医学AI

**获取方式**：
- PhysioNet：https://physionet.org/content/eicu-crd/
- 需要申请访问

---

## 多模态数据集

### 图文

#### COCO Captions

**简介**：COCO Captions是COCO数据集的图像描述子集，每张图像有5个人工编写的描述。

**规模**：
- 图像数：约120,000张
- 描述数：约600,000条

**特点**：
- 高质量的自然语言描述
- 详细的场景描述
- 多样化的表达

**格式**：JSON

**用途**：
- 图像描述生成
- 视觉问答
- 图文匹配

**获取方式**：
- 官方网站：https://cocodataset.org/
- 使用COCO API

#### Flickr30k

**简介**：Flickr30k是从Flickr收集的图像描述数据集。

**规模**：
- 图像数：31,783张
- 描述数：158,915条

**特点**：
- 自然图像
- 详细的描述
- 包含实体关系

**格式**：JSON、TXT

**用途**：
- 图像描述
- 图文检索
- 视觉语言预训练

**获取方式**：
- 官方网站：http://shannon.cs.illinois.edu/DenotationGraph/
- 需要申请

#### Visual Genome

**简介**：Visual Genome是一个连接语言和视觉的大型数据集，包含详细的场景图和描述。

**规模**：
- 图像数：108,249张
- 描述数：4.2百万条
- 场景图：108,249个

**特点**：
- 详细的场景图
- 密集的描述
- 包含关系和属性

**格式**：JSON

**用途**：
- 场景图生成
- 视觉推理
- 视觉问答

**获取方式**：
- 官方网站：http://visualgenome.org/
- API访问

#### CC3M（Conceptual Captions）

**简介**：CC3M是谷歌发布的大规模图像描述数据集，数据来源于网络。

**规模**：
- 图像数：约330万张
- 描述数：约330万条

**特点**：
- 大规模
- 网络来源
- 自动收集

**格式**：TSV

**用途**：
- 大规模预训练
- 图文对齐
- 视觉语言模型

**获取方式**：
- GitHub：https://github.com/google-research-datasets/conceptual-captions
- 需要申请

### 视频

#### Kinetics

**简介**：Kinetics是大规模的人类动作视频数据集，由DeepMind发布。

**Kinetics-400**：
- 视频数：约300,000个
- 类别数：400个
- 每类样本数：约400个

**Kinetics-600**：
- 视频数：约480,000个
- 类别数：600个

**Kinetics-700**：
- 视频数：约650,000个
- 类别数：700个

**特点**：
- 人类动作
- 多样化场景
- 短视频（10秒）

**格式**：MP4视频

**用途**：
- 动作识别
- 视频分类
- 视频理解

**获取方式**：
- GitHub：https://github.com/activitynet/ActivityNet
- 需要申请

#### UCF101

**简介**：UCF101是动作识别领域的经典数据集。

**规模**：
- 视频数：13,320个
- 类别数：101个
- 平均每类：约130个视频

**类别**：
- 人与物体交互
- 身体运动
- 人与人交互
- 弹奏乐器
- 体育运动

**格式**：AVI视频

**用途**：
- 动作识别入门
- 视频分类
- 时空特征学习

**获取方式**：
- 官方网站：https://www.crcv.ucf.edu/data/UCF101.php
- 可直接下载

#### ActivityNet

**简介**：ActivityNet是大规模的活动识别数据集。

**规模**：
- 视频数：约100,000个
- 活动类别：200个
- 总时长：约849小时

**特点**：
- 长视频
- 时间定位
- 丰富的活动类别

**格式**：MP4视频、JSON标注

**用途**：
- 活动识别
- 时间定位
- 视频摘要

**获取方式**：
- 官方网站：http://activity-net.org/
- 需要申请

#### Something-Something

**简介**：Something-Something是物体交互动作视频数据集。

**Something-Something V1**：
- 视频数：108,499个
- 类别数：174个

**Something-Something V2**：
- 视频数：220,847个
- 类别数：174个

**特点**：
- 物体交互动作
- 简单背景
- 需要理解动作语义

**格式**：MP4视频

**用途**：
- 动作识别
- 物体交互理解
- 视频生成

**获取方式**：
- 官方网站：https://20bn.com/datasets/something-something
- 需要申请

---

## 数据集获取

### 公开数据平台

#### Kaggle

**简介**：Kaggle是全球最大的数据科学竞赛和数据集平台。

**特点**：
- 超过100,000个数据集
- 涵盖多个领域
- 社区讨论和笔记本
- 免费使用

**获取方式**：
- 官网：https://www.kaggle.com/datasets
- API：`kaggle datasets list`
- Python库：`kaggle` package

**使用建议**：
- 参与竞赛提升能力
- 阅读高分解决方案
- 关注数据集质量

#### Hugging Face

**简介**：Hugging Face是NLP和机器学习社区平台，提供大量预训练模型和数据集。

**特点**：
- 超过100,000个数据集
- 标准化的数据加载
- 社区贡献
- 免费使用

**获取方式**：
- 官网：https://huggingface.co/datasets
- Python库：`datasets`
- 简单加载：`datasets.load_dataset("dataset_name")`

**使用建议**：
- 使用`datasets`库快速加载
- 查看数据集卡片了解详情
- 参与社区讨论

#### Papers with Code

**简介**：Papers with Code是机器学习论文、代码和数据集的聚合平台。

**特点**：
- 超过5000个数据集
- 包含基准结果
- 链接到论文和代码
- 便于复现研究

**获取方式**：
- 官网：https://paperswithcode.com/datasets
- 可按任务、领域筛选

#### Google Dataset Search

**简介**：Google Dataset Search是谷歌推出的专门用于搜索数据集的搜索引擎。

**特点**：
- 搜索范围广
- 支持多种数据格式
- 免费使用

**获取方式**：
- 官网：https://datasetsearch.research.google.com/

### 学术数据集

#### UCI（University of California, Irvine）

**简介**：UCI机器学习仓库是历史最悠久的机器学习数据集仓库之一。

**特点**：
- 超过600个数据集
- 涵盖多个领域
- 包含数据集描述
- 学术研究常用

**获取方式**：
- 官网：https://archive.ics.uci.edu/ml/index.php
- 可直接下载

**经典数据集**：
- Iris
- Wine
- Boston Housing
- Adult

#### OpenML

**简介**：OpenML是一个开放的机器学习平台，提供数据集、实验和结果。

**特点**：
- 超过100,000个数据集
- 标准化的API
- 包含实验结果
- 支持自动化机器学习

**获取方式**：
- 官网：https://www.openml.org/
- Python库：`openml`

#### Academic Torrents

**简介**：Academic Torrents是学术数据的分布式存储平台。

**特点**：
- 大规模数据集
- 分布式下载
- 学术社区贡献
- 免费使用

**获取方式**：
- 官网：https://academictorrents.com/
- BitTorrent协议

---

## 数据预处理

### 数据清洗

#### 缺失值处理

**常见方法**：

1. **删除法**
   - 删除包含缺失值的样本
   - 适用于缺失比例较低的情况

2. **填充法**
   - 均值/中位数/众数填充
   - 前向/后向填充（时间序列）
   - 插值法
   - 模型预测填充

3. **标记法**
   - 将缺失值作为特殊类别
   - 创建缺失值指示变量

**Python实现**：
```python
# 删除缺失值
df.dropna()

# 均值填充
df.fillna(df.mean())

# 中位数填充
df.fillna(df.median())

# 众数填充
df.fillna(df.mode()[0])
```

#### 异常值检测

**常见方法**：

1. **统计方法**
   - Z-score方法
   - IQR方法
   - 箱线图

2. **机器学习方法**
   - Isolation Forest
   - LOF（Local Outlier Factor）
   - One-Class SVM

**处理策略**：
- 删除异常值
- 替换为边界值
- 单独处理

**Python实现**：
```python
# Z-score方法
from scipy import stats
import numpy as np

z_scores = np.abs(stats.zscore(data))
filtered_data = data[(z_scores < 3).all(axis=1)]

# IQR方法
Q1 = data.quantile(0.25)
Q3 = data.quantile(0.75)
IQR = Q3 - Q1
filtered_data = data[~((data < (Q1 - 1.5 * IQR)) | (data > (Q3 + 1.5 * IQR))).any(axis=1)]
```

#### 数据标准化

**常见方法**：

1. **Min-Max标准化**
   - 将数据缩放到[0,1]区间
   - 公式：X_scaled = (X - X_min) / (X_max - X_min)

2. **Z-score标准化**
   - 将数据转换为均值为0，标准差为1的分布
   - 公式：X_scaled = (X - μ) / σ

3. **Robust标准化**
   - 使用中位数和IQR
   - 对异常值更鲁棒

**Python实现**：
```python
from sklearn.preprocessing import MinMaxScaler, StandardScaler, RobustScaler

# Min-Max标准化
scaler = MinMaxScaler()
data_scaled = scaler.fit_transform(data)

# Z-score标准化
scaler = StandardScaler()
data_scaled = scaler.fit_transform(data)

# Robust标准化
scaler = RobustScaler()
data_scaled = scaler.fit_transform(data)
```

### 数据增强

#### 图像增强

**常见方法**：

1. **几何变换**
   - 翻转（水平/垂直）
   - 旋转
   - 缩放
   - 平移
   - 裁剪

2. **颜色变换**
   - 亮度调整
   - 对比度调整
   - 饱和度调整
   - 色相调整

3. **噪声添加**
   - 高斯噪声
   - 椒盐噪声

4. **高级方法**
   - Mixup
   - Cutout
   - CutMix
   - AutoAugment

**Python实现（使用torchvision）**：
```python
from torchvision import transforms

transform = transforms.Compose([
    transforms.RandomHorizontalFlip(),
    transforms.RandomRotation(10),
    transforms.ColorJitter(brightness=0.2, contrast=0.2, saturation=0.2),
    transforms.RandomResizedCrop(224),
    transforms.ToTensor(),
    transforms.Normalize(mean=[0.485, 0.456, 0.406], std=[0.229, 0.224, 0.225])
])
```

#### 文本增强

**常见方法**：

1. **同义词替换**
   - 使用同义词词典
   - 使用词向量找近义词

2. **随机插入**
   - 随机插入同义词
   - 增加文本多样性

3. **随机交换**
   - 随机交换词语位置
   - 增加模型鲁棒性

4. **随机删除**
   - 随机删除词语
   - 正则化效果

5. **回译**
   - 翻译到其他语言再翻译回来
   - 生成新的表达

**Python实现**：
```python
import nlpaug.augmenter.word as naw
import nlpaug.augmenter.char as nac

# 同义词替换
aug = naw.SynonymAug(aug_src='wordnet')
augmented_text = aug.augment(text)

# 随机删除
aug = naw.RandomWordAug()
augmented_text = aug.augment(text)

# 回译
aug = naw.BackTranslationAug(from_model_name='transformer.wmt19.en-de', to_model_name='transformer.wmt19.de-en')
augmented_text = aug.augment(text)
```

#### 音频增强

**常见方法**：

1. **时间拉伸**
   - 改变语速
   - 保持音高

2. **音高偏移**
   - 改变音高
   - 保持语速

3. **添加噪声**
   - 环境噪声
   - 背景音乐

4. **时间偏移**
   - 随机裁剪
   - 时间平移

**Python实现**：
```python
import librosa
import numpy as np

# 时间拉伸
y_stretched = librosa.effects.time_stretch(y, rate=1.1)

# 音高偏移
y_shifted = librosa.effects.pitch_shift(y, sr=sr, n_steps=2)

# 添加噪声
noise = np.random.randn(len(y))
y_noisy = y + 0.005 * noise
```

---

## 数据集使用建议

### 数据划分

**常见划分策略**：

1. **随机划分**
   - 简单随机抽样
   - 适用于数据独立同分布的情况

2. **分层划分**
   - 按类别比例划分
   - 保持各类别在各集合中的分布一致

3. **时间划分**
   - 按时间顺序划分
   - 适用于时间序列数据

4. **组划分**
   - 按组（如用户、设备）划分
   - 避免数据泄露

**Python实现**：
```python
from sklearn.model_selection import train_test_split

# 随机划分
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# 分层划分
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, stratify=y, random_state=42)
```

**划分比例建议**：
- 训练集：60-80%
- 验证集：10-20%
- 测试集：10-20%

### 数据采样

**常见采样方法**：

1. **欠采样**
   - 减少多数类样本
   - 适用于类别不平衡严重的情况
   - 可能丢失信息

2. **过采样**
   - 增加少数类样本
   - 保留所有信息
   - 可能过拟合

3. **SMOTE**
   - 合成少数类样本
   - 基于K近邻生成新样本
   - 平衡类别分布

4. **ADASYN**
   - 自适应合成采样
   - 关注难以学习的样本

**Python实现**：
```python
from imblearn.over_sampling import SMOTE, ADASYN
from imblearn.under_sampling import RandomUnderSampler

# SMOTE过采样
smote = SMOTE(random_state=42)
X_resampled, y_resampled = smote.fit_resample(X, y)

# ADASYN过采样
adasyn = ADASYN(random_state=42)
X_resampled, y_resampled = adasyn.fit_resample(X, y)

# 随机欠采样
rus = RandomUnderSampler(random_state=42)
X_resampled, y_resampled = rus.fit_resample(X, y)
```

### 数据版本控制

**版本控制工具**：

1. **DVC（Data Version Control）**
   - 专门用于数据版本控制
   - 支持多种存储后端
   - 与Git集成

2. **Git LFS**
   - 大文件存储
   - 与Git无缝集成
   - 适合中等规模数据

3. **MLflow**
   - 机器学习生命周期管理
   - 支持数据版本跟踪
   - 集成实验管理

**DVC使用示例**：
```bash
# 初始化DVC
dvc init

# 添加数据文件
dvc add data/train.csv

# 提交到Git
git add data/train.csv.dvc .gitignore
git commit -m "Add training data"

# 推送到远程存储
dvc push

# 切换到特定版本
git checkout v1.0
dvc checkout
```

**最佳实践**：
- 为每个数据集创建独立的版本
- 记录数据来源和处理过程
- 使用语义化版本号
- 保持数据和代码版本同步
- 定期清理旧版本数据

---

## 总结

本文档详细介绍了AI学习过程中常用的各类数据集，涵盖了机器学习、计算机视觉、自然语言处理、语音处理、推荐系统、强化学习、时间序列和多模态等多个领域。

**关键要点**：

1. **选择合适的数据集**：根据任务需求、数据规模、数据质量等因素选择合适的数据集
2. **理解数据集特点**：了解每个数据集的规模、格式、标注方式和评估指标
3. **掌握预处理技术**：学会数据清洗、增强和标准化等预处理技术
4. **合理划分数据**：采用合适的划分策略，避免数据泄露
5. **版本控制数据**：使用DVC等工具进行数据版本管理

**学习建议**：

1. 从经典数据集开始学习，逐步过渡到大规模数据集
2. 参与竞赛和项目，积累实战经验
3. 关注数据集的最新发展和更新
4. 学习数据预处理和增强技术
5. 建立自己的数据集收藏和管理流程

通过系统地学习和使用这些数据集，你将能够更好地理解和应用人工智能技术，为实际项目和研究打下坚实的基础。

---

*最后更新：2024年*
*文档维护：AI学习资源团队*