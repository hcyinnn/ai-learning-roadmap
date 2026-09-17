# AI学习路线图 - Python编程基础

> **阶段定位**：AI学习路径的第二阶段（入门核心）  
> **前置要求**：完成01阶段 - AI认知与学习规划  
> **预计时长**：6-9周（每周10-15小时）  
> **难度等级**：⭐⭐（零基础友好）

---

## 学习目标

完成本阶段学习后，你将能够：

1. **掌握Python基础语法**：能够独立编写包含变量、控制流、函数、类的Python程序，理解Python的核心编程范式
2. **熟悉常用数据结构**：熟练使用列表、字典、集合、元组等数据结构，并能根据场景选择合适的数据类型
3. **掌握NumPy、Pandas等数据处理库**：能够使用NumPy进行高效的数值计算，使用Pandas进行数据清洗、转换和分析
4. **学会使用Matplotlib进行数据可视化**：能够创建各类统计图表，将数据转化为直观的可视化呈现

这些技能是进入机器学习、深度学习领域的基石。Python作为AI领域的首选语言，其生态系统中的数据科学库为后续的模型训练和数据分析提供了强大支持。

---

## 学习内容

### 1. Python基础语法 (2-3周)

Python是AI和数据科学领域的通用语言，其简洁的语法和丰富的生态系统使其成为初学者的最佳选择。本节将系统地介绍Python的核心语法概念。

#### 1.1 变量与数据类型

**变量命名规则**
- 变量名只能包含字母、数字和下划线
- 不能以数字开头
- 区分大小写（`name`和`Name`是不同变量）
- 避免使用Python保留字（如`if`、`for`、`class`等）

```python
# 合法的变量名
user_name = "Alice"
age = 25
_private_var = 100
myList = [1, 2, 3]

# 非法的变量名（会报错）
# 2name = "Bob"      # 不能以数字开头
# my-name = "Charlie" # 不能包含连字符
# class = "Python"    # 不能使用保留字
```

**基本数据类型**

Python提供了多种内置数据类型，每种类型都有其特定的用途：

```python
# 整数 (int) - 没有大小限制
count = 42
negative_num = -10
big_number = 10 ** 100  # 支持大数运算

# 浮点数 (float) - 双精度浮点
price = 19.99
pi = 3.14159
scientific = 1.5e-10  # 科学计数法

# 字符串 (str) - 不可变序列
name = "Python"
multiline = """这是
一个多行
字符串"""
raw_path = r"C:\Users\test"  # 原始字符串

# 布尔值 (bool)
is_valid = True
has_error = False

# 空值 (None)
result = None
```

**类型转换**

```python
# 隐式类型转换
x = 10 + 3.14  # int自动转为float，结果为13.14

# 显式类型转换
num_str = "123"
num_int = int(num_str)      # 字符串转整数
num_float = float(num_str)  # 字符串转浮点数

str_num = str(456)          # 整数转字符串
bool_val = bool(1)          # 非零值转为True
```

**类型检查**

```python
x = 42
print(type(x))           # <class 'int'>
print(isinstance(x, int)) # True
print(isinstance(x, str)) # False
```

#### 1.2 控制流（if/else、循环）

**条件语句**

Python使用缩进来表示代码块，这是Python的重要特性之一。

```python
# 基本if语句
score = 85

if score >= 90:
    grade = "A"
elif score >= 80:
    grade = "B"
elif score >= 70:
    grade = "C"
elif score >= 60:
    grade = "D"
else:
    grade = "F"

print(f"成绩等级: {grade}")  # 输出: 成绩等级: B
```

**三元表达式**

```python
# 简洁的条件表达式
age = 20
status = "成年" if age >= 18 else "未成年"

# 嵌套三元表达式（适度使用）
score = 85
result = "优秀" if score >= 90 else ("良好" if score >= 80 else "一般")
```

**for循环**

```python
# 遍历列表
fruits = ["苹果", "香蕉", "橙子"]
for fruit in fruits:
    print(f"我喜欢{fruit}")

# 使用range()
for i in range(5):           # 0, 1, 2, 3, 4
    print(i)

for i in range(2, 10, 2):   # 2, 4, 6, 8
    print(i)

# 带索引遍历
for index, fruit in enumerate(fruits):
    print(f"{index}: {fruit}")

# 列表推导式
squares = [x**2 for x in range(10)]  # [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
even_squares = [x**2 for x in range(10) if x % 2 == 0]  # [0, 4, 16, 36, 64]
```

**while循环**

```python
# 基本while循环
count = 0
while count < 5:
    print(count)
    count += 1

# break和continue
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
for num in numbers:
    if num == 5:
        break          # 遇到5就停止
    if num % 2 == 0:
        continue       # 跳过偶数
    print(num)         # 输出: 1, 3

# while-else结构
i = 0
while i < 5:
    i += 1
else:
    print("循环正常结束")  # 循环完整执行后会执行else
```

#### 1.3 函数与模块

**函数定义与调用**

```python
# 基本函数
def greet(name):
    """向用户打招呼"""
    return f"你好，{name}！"

# 带默认参数的函数
def power(base, exponent=2):
    """计算幂"""
    return base ** exponent

print(power(3))      # 9 (使用默认指数2)
print(power(3, 3))   # 27

# 可变参数
def calculate_sum(*args):
    """计算任意数量参数的和"""
    return sum(args)

print(calculate_sum(1, 2, 3, 4, 5))  # 15

# 关键字参数
def print_info(**kwargs):
    """打印关键字参数"""
    for key, value in kwargs.items():
        print(f"{key}: {value}")

print_info(name="Alice", age=25, city="北京")
```

**Lambda函数**

```python
# Lambda函数 - 匿名函数
square = lambda x: x ** 2
print(square(5))  # 25

# 常用于排序和映射
students = [("Alice", 85), ("Bob", 92), ("Charlie", 78)]
students.sort(key=lambda s: s[1], reverse=True)  # 按成绩降序排序

# map和filter
numbers = [1, 2, 3, 4, 5]
squared = list(map(lambda x: x**2, numbers))     # [1, 4, 9, 16, 25]
evens = list(filter(lambda x: x % 2 == 0, numbers))  # [2, 4]
```

**模块导入**

```python
# 导入整个模块
import math
print(math.sqrt(16))  # 4.0

# 导入特定函数
from math import sqrt, pi
print(sqrt(25))  # 5.0

# 别名导入
import numpy as np
from pandas import DataFrame as df

# 自定义模块
# mymodule.py
def my_function():
    return "Hello from my module"

# main.py
import mymodule
print(mymodule.my_function())
```

#### 1.4 面向对象编程基础

**类与对象**

```python
class Dog:
    """狗类"""
    
    # 类变量（所有实例共享）
    species = "犬科"
    
    def __init__(self, name, age):
        """初始化方法"""
        self.name = name    # 实例变量
        self.age = age
    
    def bark(self):
        """实例方法"""
        return f"{self.name}说：汪汪！"
    
    def __str__(self):
        """字符串表示"""
        return f"狗的名字是{self.name}，年龄是{self.age}岁"

# 创建实例
my_dog = Dog("旺财", 3)
print(my_dog.bark())      # 旺财说：汪汪！
print(my_dog)              # 狗的名字是旺财，年龄是3岁
print(Dog.species)         # 犬科
```

**继承**

```python
class Animal:
    """动物基类"""
    def __init__(self, name):
        self.name = name
    
    def speak(self):
        raise NotImplementedError("子类必须实现此方法")

class Cat(Animal):
    """猫类继承自动物"""
    def speak(self):
        return f"{self.name}说：喵喵！"

class Dog(Animal):
    """狗类继承自动物"""
    def speak(self):
        return f"{self.name}说：汪汪！"

# 多态
animals = [Cat("小花"), Dog("旺财"), Cat("咪咪")]
for animal in animals:
    print(animal.speak())
```

**封装**

```python
class BankAccount:
    """银行账户类"""
    def __init__(self, balance=0):
        self.__balance = balance  # 私有属性
    
    def deposit(self, amount):
        """存款"""
        if amount > 0:
            self.__balance += amount
            return True
        return False
    
    def withdraw(self, amount):
        """取款"""
        if 0 < amount <= self.__balance:
            self.__balance -= amount
            return True
        return False
    
    def get_balance(self):
        """获取余额"""
        return self.__balance

account = BankAccount(1000)
account.deposit(500)
print(account.get_balance())  # 1500
# print(account.__balance)    # 报错：无法直接访问私有属性
```

#### 1.5 异常处理

```python
# 基本异常处理
try:
    result = 10 / 0
except ZeroDivisionError as e:
    print(f"错误：{e}")  # 错误：division by zero
else:
    print("没有异常时执行")
finally:
    print("无论如何都会执行")

# 多种异常类型
try:
    num = int(input("请输入数字："))
    result = 100 / num
except ValueError:
    print("请输入有效的数字")
except ZeroDivisionError:
    print("不能除以零")
except Exception as e:
    print(f"未知错误：{e}")

# 自定义异常
class InsufficientFundsError(Exception):
    """余额不足异常"""
    def __init__(self, balance, amount):
        self.balance = balance
        self.amount = amount
        super().__init__(f"余额不足：余额{balance}，尝试取款{amount}")

def withdraw(balance, amount):
    if amount > balance:
        raise InsufficientFundsError(balance, amount)
    return balance - amount

try:
    new_balance = withdraw(100, 150)
except InsufficientFundsError as e:
    print(e)  # 余额不足：余额100，尝试取款150
```

#### 1.6 文件操作

```python
# 读取文件
with open("data.txt", "r", encoding="utf-8") as f:
    content = f.read()           # 读取全部内容
    # 或逐行读取
    # for line in f:
    #     print(line.strip())

# 写入文件
with open("output.txt", "w", encoding="utf-8") as f:
    f.write("第一行\n")
    f.write("第二行\n")

# 追加内容
with open("output.txt", "a", encoding="utf-8") as f:
    f.write("追加的内容\n")

# 使用pathlib（推荐）
from pathlib import Path

path = Path("data.txt")
if path.exists():
    content = path.read_text(encoding="utf-8")
    print(content)

# 创建目录
Path("new_directory").mkdir(exist_ok=True)

# 遍历目录
for file in Path(".").glob("*.py"):
    print(file.name)

# JSON文件操作
import json

data = {"name": "Alice", "age": 25, "scores": [85, 90, 78]}

# 写入JSON
with open("data.json", "w", encoding="utf-8") as f:
    json.dump(data, f, ensure_ascii=False, indent=2)

# 读取JSON
with open("data.json", "r", encoding="utf-8") as f:
    loaded_data = json.load(f)
    print(loaded_data)
```

---

### 2. 数据处理库 (2-3周)

数据处理是AI工作的核心环节。NumPy和Pandas是Python数据科学的基石库，掌握它们将大大提高数据处理效率。

#### 2.1 NumPy基础

NumPy（Numerical Python）是Python科学计算的基础包，提供了高性能的多维数组对象和用于处理这些数组的工具。

**数组创建与操作**

```python
import numpy as np

# 从列表创建数组
arr1d = np.array([1, 2, 3, 4, 5])           # 一维数组
arr2d = np.array([[1, 2, 3], [4, 5, 6]])    # 二维数组

# 特殊数组
zeros = np.zeros((3, 4))          # 3x4全零数组
ones = np.ones((2, 3))            # 2x3全一数组
eye = np.eye(3)                   # 3x3单位矩阵
random_arr = np.random.rand(3, 3) # 3x3随机数组（0-1之间）
range_arr = np.arange(0, 10, 2)   # [0, 2, 4, 6, 8]
linspace_arr = np.linspace(0, 1, 5) # [0. 0.25 0.5 0.75 1.]

# 数组属性
print(arr2d.shape)      # (2, 3) - 形状
print(arr2d.ndim)       # 2 - 维度数
print(arr2d.size)       # 6 - 元素总数
print(arr2d.dtype)      # int32 - 数据类型

# 数组索引与切片
arr = np.array([[1, 2, 3, 4],
                [5, 6, 7, 8],
                [9, 10, 11, 12]])

print(arr[0, 0])        # 1 - 第一行第一列
print(arr[1, :])        # [5 6 7 8] - 第二行所有列
print(arr[:, 2])        # [3 7 11] - 所有行第三列
print(arr[0:2, 1:3])    # [[2 3] [6 7]] - 子数组

# 布尔索引
data = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10])
mask = data > 5
print(data[mask])       # [6 7 8 9 10]
print(data[data % 2 == 0])  # [2 4 6 8 10]

# 花式索引
arr = np.array([10, 20, 30, 40, 50])
indices = [1, 3, 4]
print(arr[indices])     # [20 40 50]
```

**矩阵运算**

```python
import numpy as np

# 基本运算（逐元素）
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

print(a + b)        # [5 7 9]
print(a * b)        # [4 10 18]
print(a ** 2)       # [1 4 9]
print(np.sqrt(a))   # [1. 1.41421356 1.73205081]

# 矩阵乘法
A = np.array([[1, 2], [3, 4]])
B = np.array([[5, 6], [7, 8]])

# 方法1：使用dot()
C = np.dot(A, B)      # [[19 22] [43 50]]

# 方法2：使用@运算符
C = A @ B              # [[19 22] [43 50]]

# 方法3：使用matmul()
C = np.matmul(A, B)   # [[19 22] [43 50]]

# 转置
print(A.T)             # [[1 3] [2 4]]

# 求逆
A_inv = np.linalg.inv(A)
print(A @ A_inv)       # 接近单位矩阵

# 行列式
det = np.linalg.det(A)
print(det)             # -2.0

# 特征值和特征向量
eigenvalues, eigenvectors = np.linalg.eig(A)
print("特征值:", eigenvalues)
print("特征向量:", eigenvectors)

# 统计运算
data = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
print(np.mean(data))       # 5.0 - 全局均值
print(np.mean(data, axis=0))  # [4. 5. 6.] - 按列均值
print(np.mean(data, axis=1))  # [2. 5. 8.] - 按行均值
print(np.sum(data))        # 45 - 全局求和
print(np.std(data))        # 标准差
print(np.max(data))        # 最大值
print(np.min(data))        # 最小值
print(np.argmax(data))     # 最大值索引
```

**广播机制**

广播（Broadcasting）是NumPy中强大的机制，允许不同形状的数组进行运算。

```python
import numpy as np

# 广播规则：从尾部维度开始比较
# 1. 维度相等
# 2. 其中一个维度为1
# 3. 缺失的维度视为1

# 标量与数组运算
arr = np.array([1, 2, 3, 4, 5])
print(arr * 2)         # [2 4 6 8 10]

# 二维数组与一维数组
matrix = np.array([[1, 2, 3],
                   [4, 5, 6],
                   [7, 8, 9]])
vector = np.array([10, 20, 30])

# vector被广播到每一行
result = matrix + vector
print(result)
# [[11 22 33]
#  [14 25 36]
#  [17 28 39]]

# 列向量与行向量
col_vector = np.array([[1], [2], [3]])
row_vector = np.array([10, 20, 30])

# 生成3x3矩阵
result = col_vector * row_vector
print(result)
# [[10 20 30]
#  [20 40 60]
#  [30 60 90]]

# 实际应用：标准化数据
data = np.random.rand(5, 3)  # 5个样本，3个特征
mean = np.mean(data, axis=0)  # 每个特征的均值
std = np.std(data, axis=0)    # 每个特征的标准差

# 标准化：(x - mean) / std
normalized_data = (data - mean) / std  # 广播自动处理维度
print("标准化后的数据均值:", np.mean(normalized_data, axis=0))  # 接近0
print("标准化后的数据标准差:", np.std(normalized_data, axis=0))  # 接近1
```

#### 2.2 Pandas基础

Pandas是Python数据分析的核心库，提供了DataFrame和Series两种主要数据结构，使数据操作变得简单直观。

**Series与DataFrame**

```python
import pandas as pd
import numpy as np

# Series - 一维标签数组
s = pd.Series([1, 2, 3, 4, 5], index=['a', 'b', 'c', 'd', 'e'])
print(s)
# a    1
# b    2
# c    3
# d    4
# e    5

# 从字典创建Series
data = {'Alice': 85, 'Bob': 92, 'Charlie': 78}
scores = pd.Series(data)
print(scores)
# Alice      85
# Bob        92
# Charlie    78

# DataFrame - 二维标签数据结构
# 从字典创建
data = {
    '姓名': ['Alice', 'Bob', 'Charlie', 'David'],
    '年龄': [25, 30, 35, 28],
    '城市': ['北京', '上海', '广州', '深圳'],
    '薪资': [15000, 20000, 18000, 16000]
}
df = pd.DataFrame(data)
print(df)
#        姓名  年龄  城市    薪资
# 0    Alice   25  北京  15000
# 1      Bob   30  上海  20000
# 2  Charlie   35  广州  18000
# 3    David   28  深圳  16000

# 从NumPy数组创建
df = pd.DataFrame(
    np.random.randn(3, 4),
    columns=['A', 'B', 'C', 'D'],
    index=['x', 'y', 'z']
)

# DataFrame属性
print(df.shape)      # (3, 4) - 形状
print(df.dtypes)     # 每列数据类型
print(df.info())     # 详细信息
print(df.describe()) # 统计摘要
print(df.columns)    # 列名
print(df.index)      # 索引

# 访问列
print(df['姓名'])           # 返回Series
print(df[['姓名', '年龄']])  # 返回DataFrame

# 访问行
print(df.iloc[0])     # 按位置访问第一行
print(df.loc[0])      # 按标签访问索引为0的行

# 条件筛选
young_employees = df[df['年龄'] < 30]
high_salary = df[df['薪资'] > 17000]
print(young_employees)
```

**数据读取与清洗**

```python
import pandas as pd
import numpy as np

# 读取CSV文件
df = pd.read_csv('data.csv', encoding='utf-8')

# 读取Excel文件
df = pd.read_excel('data.xlsx', sheet_name='Sheet1')

# 读取JSON文件
df = pd.read_json('data.json')

# 读取SQL数据库
import sqlite3
conn = sqlite3.connect('database.db')
df = pd.read_sql('SELECT * FROM table_name', conn)

# 数据清洗 - 处理缺失值
# 检查缺失值
print(df.isnull().sum())          # 每列缺失值数量
print(df.isnull().sum().sum())    # 总缺失值数量

# 删除缺失值
df_cleaned = df.dropna()                    # 删除包含缺失值的行
df_cleaned = df.dropna(subset=['列名'])      # 只检查特定列
df_cleaned = df.dropna(thresh=2)            # 至少有2个非空值才保留

# 填充缺失值
df_filled = df.fillna(0)                    # 用0填充
df_filled = df.fillna(df.mean())            # 用均值填充
df_filled = df.fillna(method='ffill')       # 前向填充
df_filled = df.fillna(method='bfill')       # 后向填充

# 数据清洗 - 处理重复值
print(df.duplicated().sum())      # 重复行数量
df_unique = df.drop_duplicates()  # 删除重复行
df_unique = df.drop_duplicates(subset=['列名'])  # 基于特定列去重

# 数据清洗 - 数据类型转换
df['日期'] = pd.to_datetime(df['日期'])
df['数值'] = pd.to_numeric(df['数值'], errors='coerce')  # 无效值转为NaN

# 数据清洗 - 字符串处理
df['姓名'] = df['姓名'].str.strip()          # 去除首尾空格
df['邮箱'] = df['邮箱'].str.lower()          # 转为小写
df['电话'] = df['电话'].str.replace('-', '')  # 替换字符
```

**数据筛选与聚合**

```python
import pandas as pd
import numpy as np

# 创建示例数据
data = {
    '部门': ['技术', '市场', '技术', '市场', '技术', '市场'],
    '姓名': ['Alice', 'Bob', 'Charlie', 'David', 'Eve', 'Frank'],
    '薪资': [15000, 12000, 18000, 13000, 16000, 14000],
    '绩效': [85, 90, 88, 92, 87, 85]
}
df = pd.DataFrame(data)

# 条件筛选
high_salary = df[df['薪资'] > 15000]
tech_high_salary = df[(df['部门'] == '技术') & (df['薪资'] > 15000)]
print(tech_high_salary)

# isin筛选
selected_depts = df[df['部门'].isin(['技术', '市场'])]

# query方法（更直观）
result = df.query('薪资 > 15000 and 绩效 >= 88')

# 排序
df_sorted = df.sort_values('薪资', ascending=False)  # 按薪资降序
df_sorted = df.sort_values(['部门', '薪资'], ascending=[True, False])  # 多列排序

# 分组聚合
grouped = df.groupby('部门')
print(grouped['薪资'].mean())      # 每个部门的平均薪资
print(grouped['薪资'].agg(['mean', 'max', 'min']))  # 多个聚合函数

# 多列分组
multi_grouped = df.groupby(['部门', '绩效等级'])

# 自定义聚合函数
def salary_range(x):
    return x.max() - x.min()

print(grouped['薪资'].agg(salary_range))

# 透视表
pivot_table = df.pivot_table(
    values='薪资',
    index='部门',
    aggfunc=['mean', 'count']
)
print(pivot_table)

# 应用函数
df['薪资等级'] = df['薪资'].apply(lambda x: '高' if x > 15000 else '中' if x > 12000 else '低')

# apply多列
def calculate_bonus(row):
    return row['薪资'] * (row['绩效'] / 100)

df['奖金'] = df.apply(calculate_bonus, axis=1)
```

**数据合并与重塑**

```python
import pandas as pd

# 创建示例数据
df1 = pd.DataFrame({
    'ID': [1, 2, 3, 4],
    '姓名': ['Alice', 'Bob', 'Charlie', 'David']
})

df2 = pd.DataFrame({
    'ID': [2, 3, 4, 5],
    '薪资': [20000, 18000, 16000, 15000]
})

# merge - 类似SQL的JOIN
# 内连接（默认）
inner = pd.merge(df1, df2, on='ID', how='inner')
#    ID    姓名    薪资
# 0   2    Bob  20000
# 1   3  Charlie  18000
# 2   4  David  16000

# 左连接
left = pd.merge(df1, df2, on='ID', how='left')

# 右连接
right = pd.merge(df1, df2, on='ID', how='right')

# 外连接
outer = pd.merge(df1, df2, on='ID', how='outer')

# concat - 拼接
# 纵向拼接
vertical = pd.concat([df1, df2], axis=0)

# 横向拼接
horizontal = pd.concat([df1, df2], axis=1)

# 数据重塑 - pivot（长格式转宽格式）
long_data = pd.DataFrame({
    '日期': ['2024-01', '2024-01', '2024-02', '2024-02'],
    '产品': ['A', 'B', 'A', 'B'],
    '销量': [100, 150, 120, 180]
})

wide_data = long_data.pivot(index='日期', columns='产品', values='销量')
print(wide_data)
# 产品      A    B
# 日期
# 2024-01  100  150
# 2024-02  120  180

# melt（宽格式转长格式）
long_again = wide_data.reset_index().melt(
    id_vars='日期',
    value_vars=['A', 'B'],
    var_name='产品',
    value_name='销量'
)

# stack/unstack
df = pd.DataFrame({
    'A': [1, 2, 3],
    'B': [4, 5, 6]
}, index=['x', 'y', 'z'])

stacked = df.stack()    # 转为Series（多级索引）
unstacked = stacked.unstack()  # 转回DataFrame
```

---

### 3. 数据可视化 (1-2周)

数据可视化是理解数据、发现模式、传达结果的关键技能。Matplotlib和Seaborn是Python中最常用的可视化库。

#### 3.1 Matplotlib基础

Matplotlib是Python最基础的绑图库，提供了类似MATLAB的绑图接口。

**折线图、柱状图、散点图**

```python
import matplotlib.pyplot as plt
import numpy as np

# 设置中文字体（Windows系统）
plt.rcParams['font.sans-serif'] = ['SimHei']  # 用来正常显示中文标签
plt.rcParams['axes.unicode_minus'] = False    # 用来正常显示负号

# 折线图
x = np.linspace(0, 10, 100)
y1 = np.sin(x)
y2 = np.cos(x)

plt.figure(figsize=(10, 6))
plt.plot(x, y1, label='sin(x)', color='blue', linewidth=2)
plt.plot(x, y2, label='cos(x)', color='red', linewidth=2, linestyle='--')
plt.title('正弦和余弦函数', fontsize=16)
plt.xlabel('x', fontsize=12)
plt.ylabel('y', fontsize=12)
plt.legend(fontsize=12)
plt.grid(True, alpha=0.3)
plt.show()

# 柱状图
categories = ['Python', 'Java', 'C++', 'JavaScript', 'Go']
values = [85, 75, 60, 70, 45]

plt.figure(figsize=(10, 6))
bars = plt.bar(categories, values, color=['#2ecc71', '#3498db', '#e74c3c', '#f39c12', '#9b59b6'])
plt.title('编程语言流行度', fontsize=16)
plt.xlabel('编程语言', fontsize=12)
plt.ylabel('流行度评分', fontsize=12)

# 在柱子上添加数值
for bar in bars:
    height = bar.get_height()
    plt.text(bar.get_x() + bar.get_width()/2., height,
             f'{int(height)}',
             ha='center', va='bottom')

plt.show()

# 散点图
np.random.seed(42)
x = np.random.randn(100)
y = x * 0.5 + np.random.randn(100) * 0.3
colors = np.random.rand(100)
sizes = np.random.rand(100) * 200

plt.figure(figsize=(10, 6))
scatter = plt.scatter(x, y, c=colors, s=sizes, alpha=0.6, cmap='viridis')
plt.colorbar(scatter, label='颜色值')
plt.title('散点图示例', fontsize=16)
plt.xlabel('X值', fontsize=12)
plt.ylabel('Y值', fontsize=12)
plt.grid(True, alpha=0.3)
plt.show()
```

**子图与布局**

```python
import matplotlib.pyplot as plt
import numpy as np

# 方法1：subplot
fig, axes = plt.subplots(2, 2, figsize=(12, 10))

# 子图1：折线图
x = np.linspace(0, 10, 100)
axes[0, 0].plot(x, np.sin(x))
axes[0, 0].set_title('正弦函数')
axes[0, 0].grid(True)

# 子图2：柱状图
categories = ['A', 'B', 'C', 'D']
values = [25, 40, 30, 55]
axes[0, 1].bar(categories, values, color='skyblue')
axes[0, 1].set_title('柱状图')

# 子图3：散点图
x = np.random.randn(50)
y = np.random.randn(50)
axes[1, 0].scatter(x, y, color='red', alpha=0.6)
axes[1, 0].set_title('散点图')

# 子图4：饼图
sizes = [35, 30, 20, 15]
labels = ['Python', 'Java', 'C++', '其他']
axes[1, 1].pie(sizes, labels=labels, autopct='%1.1f%%')
axes[1, 1].set_title('饼图')

plt.tight_layout()  # 自动调整布局
plt.show()

# 方法2：GridSpec（更灵活的布局）
from matplotlib.gridspec import GridSpec

fig = plt.figure(figsize=(12, 8))
gs = GridSpec(2, 2, figure=fig)

ax1 = fig.add_subplot(gs[0, :])  # 第一行占两列
ax2 = fig.add_subplot(gs[1, 0])  # 第二行第一列
ax3 = fig.add_subplot(gs[1, 1])  # 第二行第二列

ax1.plot([1, 2, 3, 4], [1, 4, 2, 3])
ax1.set_title('跨越两列的图')

ax2.bar([1, 2, 3], [3, 2, 5])
ax2.set_title('柱状图')

ax3.scatter([1, 2, 3], [1, 2, 3])
ax3.set_title('散点图')

plt.tight_layout()
plt.show()
```

**样式与美化**

```python
import matplotlib.pyplot as plt
import numpy as np

# 使用内置样式
plt.style.use('seaborn-v0_8-darkgrid')  # 或 'ggplot', 'fivethirtyeight' 等

# 自定义颜色方案
colors = ['#2ecc71', '#3498db', '#e74c3c', '#f39c12', '#9b59b6']

# 创建专业图表
fig, ax = plt.subplots(figsize=(10, 6))

x = np.linspace(0, 10, 50)
y1 = np.sin(x)
y2 = np.cos(x)
y3 = np.sin(x + 1)

ax.fill_between(x, y1, alpha=0.3, color=colors[0], label='sin(x)')
ax.fill_between(x, y2, alpha=0.3, color=colors[1], label='cos(x)')
ax.plot(x, y3, color=colors[2], linewidth=2, label='sin(x+1)')

ax.set_title('专业图表示例', fontsize=16, fontweight='bold')
ax.set_xlabel('X轴', fontsize=12)
ax.set_ylabel('Y轴', fontsize=12)
ax.legend(loc='upper right', frameon=True, shadow=True)
ax.grid(True, linestyle='--', alpha=0.7)

# 添加注释
ax.annotate('最大值', xy=(np.pi/2, 1), xytext=(np.pi/2 + 1, 0.8),
            arrowprops=dict(facecolor='black', shrink=0.05))

plt.tight_layout()
plt.show()

# 保存图表
fig.savefig('chart.png', dpi=300, bbox_inches='tight')  # PNG格式
fig.savefig('chart.pdf', bbox_inches='tight')            # PDF格式
fig.savefig('chart.svg', bbox_inches='tight')            # SVG格式
```

#### 3.2 Seaborn基础

Seaborn是基于Matplotlib的高级可视化库，提供了更美观的默认样式和更简洁的统计图表接口。

**统计图表**

```python
import seaborn as sns
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np

# 设置样式
sns.set_theme(style="whitegrid")

# 加载内置数据集
tips = sns.load_dataset("tips")
print(tips.head())

# 直方图
plt.figure(figsize=(10, 6))
sns.histplot(data=tips, x="total_bill", bins=20, kde=True)
plt.title("账单金额分布", fontsize=16)
plt.show()

# 核密度估计图
plt.figure(figsize=(10, 6))
sns.kdeplot(data=tips, x="total_bill", hue="time", fill=True)
plt.title("不同时间段的账单分布", fontsize=16)
plt.show()

# 箱线图
plt.figure(figsize=(10, 6))
sns.boxplot(x="day", y="total_bill", data=tips, palette="Set2")
plt.title("每天的账单分布", fontsize=16)
plt.show()

# 小提琴图
plt.figure(figsize=(10, 6))
sns.violinplot(x="day", y="total_bill", hue="sex", data=tips, split=True)
plt.title("每天不同性别的账单分布", fontsize=16)
plt.show()

# 计数图
plt.figure(figsize=(10, 6))
sns.countplot(x="day", hue="sex", data=tips, palette="pastel")
plt.title("每天不同性别的顾客数量", fontsize=16)
plt.show()
```

**热力图**

```python
import seaborn as sns
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd

# 创建相关矩阵数据
np.random.seed(42)
data = pd.DataFrame({
    '数学': np.random.randint(60, 100, 50),
    '物理': np.random.randint(60, 100, 50),
    '化学': np.random.randint(60, 100, 50),
    '英语': np.random.randint(60, 100, 50),
    '语文': np.random.randint(60, 100, 50)
})

# 添加一些相关性
data['物理'] = data['数学'] * 0.8 + np.random.randn(50) * 5
data['化学'] = data['物理'] * 0.7 + np.random.randn(50) * 5

# 计算相关矩阵
corr_matrix = data.corr()

# 绘制热力图
plt.figure(figsize=(10, 8))
sns.heatmap(
    corr_matrix,
    annot=True,           # 显示数值
    fmt='.2f',            # 数值格式
    cmap='coolwarm',      # 颜色映射
    center=0,             # 中心值
    square=True,          # 正方形格子
    linewidths=1,         # 网格线宽度
    cbar_kws={"shrink": 0.8}  # 颜色条设置
)
plt.title('科目成绩相关性热力图', fontsize=16)
plt.tight_layout()
plt.show()

# 聚类热力图
plt.figure(figsize=(10, 8))
sns.clustermap(
    corr_matrix,
    annot=True,
    fmt='.2f',
    cmap='coolwarm',
    figsize=(10, 8)
)
plt.title('聚类热力图', fontsize=16)
plt.show()
```

**分布图**

```python
import seaborn as sns
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd

# 创建示例数据
np.random.seed(42)
n = 200
data = pd.DataFrame({
    'x': np.concatenate([np.random.normal(0, 1, n), np.random.normal(3, 1.5, n)]),
    'y': np.concatenate([np.random.normal(0, 1, n), np.random.normal(2, 1, n)]),
    'group': ['A'] * n + ['B'] * n
})

# 联合分布图
plt.figure(figsize=(10, 8))
sns.jointplot(
    data=data,
    x='x',
    y='y',
    hue='group',
    kind='scatter',      # 'scatter', 'kde', 'hist', 'hex'
    marginal_kws=dict(fill=True)
)
plt.suptitle('联合分布图', y=1.02, fontsize=16)
plt.show()

# 配对图
iris = sns.load_dataset("iris")
plt.figure(figsize=(12, 10))
sns.pairplot(iris, hue="species", diag_kind="kde", palette="husl")
plt.suptitle('鸢尾花数据配对图', y=1.02, fontsize=16)
plt.show()

# 回归图
plt.figure(figsize=(10, 6))
sns.regplot(
    data=data,
    x='x',
    y='y',
    scatter_kws={'alpha': 0.5},
    line_kws={'color': 'red'}
)
plt.title('回归图', fontsize=16)
plt.show()

# 分面网格图
g = sns.FacetGrid(tips, col="time", row="sex", margin_titles=True)
g.map_dataframe(sns.histplot, x="total_bill", bins=15)
g.set_axis_labels("账单金额", "数量")
g.set_titles(col_template="{col_name}时间", row_template="{row_name}性")
plt.show()
```

---

### 4. 开发环境 (1周)

选择合适的开发环境能大大提高学习和开发效率。本节介绍常用的Python开发工具。

#### 4.1 Jupyter Notebook使用

Jupyter Notebook是数据科学领域最流行的开发环境，支持交互式编程和实时可视化。

**安装与启动**

```bash
# 安装Jupyter
pip install jupyter

# 或使用Anaconda（推荐初学者）
# 下载地址：https://www.anaconda.com/download

# 启动Jupyter Notebook
jupyter notebook

# 启动JupyterLab（更现代的界面）
pip install jupyterlab
jupyter lab
```

**基本操作**

1. **单元格类型**：
   - Code：编写和执行代码
   - Markdown：编写文档和说明
   - Raw：原始文本

2. **快捷键**：
   - `Shift + Enter`：执行当前单元格
   - `Ctrl + Enter`：在当前单元格执行
   - `A`：在上方插入单元格
   - `B`：在下方插入单元格
   - `DD`：删除当前单元格
   - `M`：转为Markdown单元格
   - `Y`：转为Code单元格
   - `L`：显示/隐藏行号

3. **魔术命令**：
```python
%timeit sum(range(1000))        # 测量执行时间
%matplotlib inline               # 内联显示图表
%load_ext autoreload             # 自动重载模块
%autoreload 2
%pwd                             # 显示当前目录
%ls                              # 列出文件
%run script.py                   # 运行Python脚本
```

4. **Markdown语法**：
```markdown
# 一级标题
## 二级标题
### 三级标题

**粗体** *斜体* ~~删除线~~

- 无序列表
1. 有序列表

> 引用

`代码` ```代码块```

[链接](https://www.example.com)
![图片](image.png)
```

**最佳实践**

1. **命名规范**：使用描述性的文件名，如`01-data-analysis.ipynb`
2. **文档说明**：在Notebook开头添加标题和说明
3. **分节组织**：使用Markdown标题分隔不同部分
4. **清理输出**：分享前清理不必要的输出
5. **版本控制**：使用`nbstripout`工具处理Notebook的版本控制

#### 4.2 Google Colab使用

Google Colab是免费的云端Jupyter Notebook环境，无需配置即可使用GPU。

**主要优势**

- 免费使用GPU和TPU
- 无需本地安装
- 支持多人协作
- 集成Google Drive
- 预装常用库

**使用步骤**

1. 访问 https://colab.research.google.com
2. 登录Google账号
3. 创建新Notebook或打开现有文件
4. 选择运行时类型（CPU/GPU/TPU）

**常用功能**

```python
# 安装额外的库
!pip install package_name

# 挂载Google Drive
from google.colab import drive
drive.mount('/content/drive')

# 访问Google Drive文件
import os
os.chdir('/content/drive/My Drive/your_folder')

# 上传文件
from google.colab import files
uploaded = files.upload()

# 下载文件
from google.colab import files
files.download('output.csv')

# 检查GPU信息
!nvidia-smi

# 使用TensorBoard
%load_ext tensorboard
%tensorboard --logdir logs/
```

#### 4.3 VS Code配置

Visual Studio Code是轻量级但功能强大的代码编辑器，支持Python开发。

**安装Python扩展**

1. 打开VS Code
2. 按`Ctrl + Shift + X`打开扩展面板
3. 搜索并安装：
   - Python (Microsoft)
   - Pylance
   - Jupyter
   - Python Indent

**配置Python环境**

1. 按`Ctrl + Shift + P`打开命令面板
2. 输入"Python: Select Interpreter"
3. 选择Python解释器

**推荐设置**

```json
// settings.json
{
    "python.linting.enabled": true,
    "python.linting.pylintEnabled": true,
    "python.formatting.provider": "black",
    "python.formatting.blackArgs": ["--line-length", "88"],
    "editor.formatOnSave": true,
    "editor.codeActionsOnSave": {
        "source.organizeImports": true
    },
    "jupyter.askForKernelRestart": false,
    "python.analysis.typeCheckingMode": "basic"
}
```

**常用快捷键**

- `Ctrl + Shift + P`：命令面板
- `Ctrl + P`：快速打开文件
- `Ctrl + Shift + ``：打开终端
- `F5`：运行调试
- `F12`：转到定义
- `Ctrl + Space`：代码补全

**调试配置**

```json
// launch.json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Python: Current File",
            "type": "python",
            "request": "launch",
            "program": "${file}",
            "console": "integratedTerminal",
            "cwd": "${workspaceFolder}",
            "env": {
                "PYTHONPATH": "${workspaceFolder}"
            }
        }
    ]
}
```

#### 4.4 虚拟环境管理

虚拟环境是Python开发的最佳实践，可以隔离不同项目的依赖。

**venv（内置工具）**

```bash
# 创建虚拟环境
python -m venv myenv

# 激活虚拟环境
# Windows
myenv\Scripts\activate

# macOS/Linux
source myenv/bin/activate

# 退出虚拟环境
deactivate

# 导出依赖
pip freeze > requirements.txt

# 安装依赖
pip install -r requirements.txt
```

**conda（Anaconda/Miniconda）**

```bash
# 创建环境
conda create -n myenv python=3.11

# 激活环境
conda activate myenv

# 退出环境
conda deactivate

# 安装包
conda install numpy pandas matplotlib

# 导出环境
conda env export > environment.yml

# 从文件创建环境
conda env create -f environment.yml

# 列出所有环境
conda env list

# 删除环境
conda env remove -n myenv
```

**pipenv**

```bash
# 安装pipenv
pip install pipenv

# 创建环境并安装包
pipenv install numpy pandas

# 激活环境
pipenv shell

# 安装开发依赖
pipenv install --dev pytest black

# 生成lock文件
pipenv lock

# 从lock文件安装
pipenv install --ignore-pipfile
```

**Poetry（现代工具）**

```bash
# 安装Poetry
curl -sSL https://install.python-poetry.org | python3 -

# 创建新项目
poetry new myproject

# 添加依赖
poetry add numpy pandas

# 添加开发依赖
poetry add --group dev pytest black

# 安装所有依赖
poetry install

# 运行命令
poetry run python script.py

# 激活虚拟环境
poetry shell
```

**最佳实践**

1. **每个项目一个环境**：避免依赖冲突
2. **使用requirements.txt或pyproject.toml**：记录项目依赖
3. **版本锁定**：使用`pip freeze`或`poetry.lock`锁定版本
4. **忽略虚拟环境目录**：在`.gitignore`中添加`venv/`、`.venv/`、`env/`
5. **文档说明**：在README中说明如何设置环境

---

## 学习资源

### 推荐书籍

#### 入门级
1. **《Python编程：从入门到实践》**（第3版）
   - 作者：Eric Matthes
   - 适合零基础，包含三个实战项目
   - 涵盖Python基础和数据可视化

2. **《笨办法学Python 3》**
   - 作者：Zed Shaw
   - 通过练习学习，适合动手实践型学习者

3. **《利用Python进行数据分析》**（第3版）
   - 作者：Wes McKinney（Pandas创始人）
   - 专注数据处理和分析

#### 进阶级
4. **《Python Cookbook》**（第3版）
   - 作者：David Beazley, Brian K. Jones
   - 包含大量实用技巧和最佳实践

5. **《流畅的Python》**（第2版）
   - 作者：Luciano Ramalho
   - 深入理解Python特性

6. **《Python数据科学手册》**
   - 作者：Jake VanderPlas
   - 全面覆盖NumPy、Pandas、Matplotlib、Scikit-learn

### 推荐课程

#### 免费课程
1. **Python for Everybody** (Coursera)
   - 密歇根大学，Charles Severance教授
   - 适合完全零基础
   - 网址：https://www.py4e.com

2. **Introduction to Computer Science and Programming Using Python** (edX)
   - MIT公开课
   - 计算机科学入门
   - 网址：https://www.edx.org/course/introduction-to-computer-science-and-programming-7

3. **Kaggle Learn**
   - 免费微课程，包括Python、Pandas、Data Visualization等
   - 网址：https://www.kaggle.com/learn

4. **Real Python**
   - 高质量教程和文章
   - 网址：https://realpython.com

#### 付费课程
5. **2024 Complete Python Bootcamp** (Udemy)
   - Jose Portilla主讲
   - 从零到精通

6. **Python for Data Science and Machine Learning Bootcamp** (Udemy)
   - Jose Portilla主讲
   - 数据科学方向

7. **DataCamp**
   - 交互式学习平台
   - 网址：https://www.datacamp.com

### 在线教程

1. **官方文档**
   - Python官方文档：https://docs.python.org/zh-cn/3/
   - NumPy官方文档：https://numpy.org/doc/
   - Pandas官方文档：https://pandas.pydata.org/docs/
   - Matplotlib官方文档：https://matplotlib.org/stable/

2. **W3Schools Python教程**
   - 网址：https://www.w3schools.com/python/
   - 简单易懂，适合快速查阅

3. **GeeksforGeeks**
   - 网址：https://www.geeksforgeeks.org/python-programming-language/
   - 丰富的示例和练习

4. **LeetCode**
   - 算法练习平台
   - 网址：https://leetcode.com

5. **HackerRank**
   - 编程挑战平台
   - 网址：https://www.hackerrank.com

---

## 实践项目

实践是掌握编程技能的最佳方式。以下是三个由浅入深的项目，帮助你巩固所学知识。

### 项目1：数据清洗练习

**目标**：处理真实世界中的脏数据，学习数据清洗技巧

**数据集**：泰坦尼克号乘客数据（可从Kaggle下载）

**任务清单**：

```python
import pandas as pd
import numpy as np

# 1. 加载数据
df = pd.read_csv('titanic.csv')

# 2. 探索性分析
print(df.head())
print(df.info())
print(df.describe())
print(df.isnull().sum())

# 3. 处理缺失值
# Age: 使用中位数填充
df['Age'].fillna(df['Age'].median(), inplace=True)

# Embarked: 使用众数填充
df['Embarked'].fillna(df['Embarked'].mode()[0], inplace=True)

# Cabin: 删除或创建新特征
df['Has_Cabin'] = df['Cabin'].notna().astype(int)
df.drop('Cabin', axis=1, inplace=True)

# 4. 数据类型转换
df['Pclass'] = df['Pclass'].astype('category')
df['Survived'] = df['Survived'].astype('bool')

# 5. 特征工程
df['FamilySize'] = df['SibSp'] + df['Parch'] + 1
df['IsAlone'] = (df['FamilySize'] == 1).astype(int)

# 6. 处理异常值
# 检测票价异常值
Q1 = df['Fare'].quantile(0.25)
Q3 = df['Fare'].quantile(0.75)
IQR = Q3 - Q1
lower_bound = Q1 - 1.5 * IQR
upper_bound = Q3 + 1.5 * IQR

# 处理异常值（截断或删除）
df['Fare'] = df['Fare'].clip(lower_bound, upper_bound)

# 7. 保存清洗后的数据
df.to_csv('titanic_cleaned.csv', index=False)

# 8. 生成数据质量报告
def data_quality_report(df):
    report = pd.DataFrame({
        '数据类型': df.dtypes,
        '非空数量': df.count(),
        '缺失数量': df.isnull().sum(),
        '缺失比例': df.isnull().sum() / len(df) * 100,
        '唯一值数量': df.nunique()
    })
    return report

print(data_quality_report(df))
```

**学习成果**：
- 掌握缺失值处理的多种方法
- 学会检测和处理异常值
- 理解数据类型转换的重要性
- 掌握基本的特征工程技巧

### 项目2：数据可视化项目

**目标**：创建专业的数据可视化报告

**数据集**：全球COVID-19数据（可从Johns Hopkins GitHub获取）

**任务清单**：

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np

# 设置样式
plt.style.use('seaborn-v0_8-whitegrid')
sns.set_palette("husl")

# 1. 加载数据
confirmed = pd.read_csv('time_series_covid19_confirmed_global.csv')
deaths = pd.read_csv('time_series_covid19_deaths_global.csv')

# 2. 数据预处理
# 转换为长格式
confirmed_long = confirmed.melt(
    id_vars=['Province/State', 'Country/Region', 'Lat', 'Long'],
    var_name='Date',
    value_name='Confirmed'
)
confirmed_long['Date'] = pd.to_datetime(confirmed_long['Date'])

# 3. 创建可视化

# 图表1：全球累计确诊病例趋势
global_daily = confirmed_long.groupby('Date')['Confirmed'].sum().reset_index()

fig, ax = plt.subplots(figsize=(12, 6))
ax.plot(global_daily['Date'], global_daily['Confirmed'], linewidth=2)
ax.fill_between(global_daily['Date'], global_daily['Confirmed'], alpha=0.3)
ax.set_title('全球COVID-19累计确诊病例', fontsize=16)
ax.set_xlabel('日期', fontsize=12)
ax.set_ylabel('累计确诊数', fontsize=12)
ax.yaxis.set_major_formatter(plt.FuncFormatter(lambda x, p: format(int(x), ',')))
plt.xticks(rotation=45)
plt.tight_layout()
plt.savefig('global_cases.png', dpi=300)
plt.show()

# 图表2：Top10国家确诊数对比
latest_date = confirmed_long['Date'].max()
top10 = confirmed_long[confirmed_long['Date'] == latest_date].nlargest(10, 'Confirmed')

fig, ax = plt.subplots(figsize=(12, 6))
bars = ax.barh(top10['Country/Region'], top10['Confirmed'], color=sns.color_palette("viridis", 10))
ax.set_title(f'Top 10国家累计确诊数 ({latest_date.strftime("%Y-%m-%d")})', fontsize=16)
ax.set_xlabel('累计确诊数', fontsize=12)
ax.xaxis.set_major_formatter(plt.FuncFormatter(lambda x, p: format(int(x), ',')))

# 添加数值标签
for bar in bars:
    width = bar.get_width()
    ax.text(width, bar.get_y() + bar.get_height()/2,
            f'{int(width):,}',
            ha='left', va='center', fontsize=10)

plt.tight_layout()
plt.savefig('top10_countries.png', dpi=300)
plt.show()

# 图表3：每日新增病例（7日移动平均）
global_daily['New_Confirmed'] = global_daily['Confirmed'].diff()
global_daily['MA7'] = global_daily['New_Confirmed'].rolling(window=7).mean()

fig, ax = plt.subplots(figsize=(12, 6))
ax.bar(global_daily['Date'], global_daily['New_Confirmed'], alpha=0.3, label='每日新增')
ax.plot(global_daily['Date'], global_daily['MA7'], color='red', linewidth=2, label='7日移动平均')
ax.set_title('全球每日新增COVID-19病例', fontsize=16)
ax.set_xlabel('日期', fontsize=12)
ax.set_ylabel('新增病例数', fontsize=12)
ax.legend()
plt.xticks(rotation=45)
plt.tight_layout()
plt.savefig('daily_new_cases.png', dpi=300)
plt.show()

# 图表4：热力图 - 各大洲每月确诊数
confirmed_long['Month'] = confirmed_long['Date'].dt.to_period('M')
confirmed_long['Continent'] = confirmed_long['Country/Region'].map(get_continent)  # 需要定义映射函数

heatmap_data = confirmed_long.groupby(['Continent', 'Month'])['Confirmed'].sum().unstack()
heatmap_data = heatmap_data.diff(axis=1)  # 转为新增

plt.figure(figsize=(14, 6))
sns.heatmap(heatmap_data, cmap='YlOrRd', annot=False, fmt='.0f')
plt.title('各大洲每月新增确诊病例热力图', fontsize=16)
plt.xlabel('月份', fontsize=12)
plt.ylabel('大洲', fontsize=12)
plt.xticks(rotation=45)
plt.tight_layout()
plt.savefig('continent_heatmap.png', dpi=300)
plt.show()
```

**学习成果**：
- 掌握多种图表类型的选择和使用
- 学会创建专业的可视化报告
- 理解数据可视化的设计原则
- 掌握图表的美化和导出技巧

### 项目3：简单数据分析

**目标**：完成一个完整的数据分析流程

**数据集**：电商销售数据（可自行创建或从Kaggle获取）

**任务清单**：

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from datetime import datetime, timedelta

# 1. 数据生成（模拟电商数据）
np.random.seed(42)
n_records = 1000

start_date = datetime(2023, 1, 1)
dates = [start_date + timedelta(days=np.random.randint(0, 365)) for _ in range(n_records)]

categories = ['电子产品', '服装', '食品', '家居', '图书']
regions = ['华东', '华南', '华北', '华中', '西南']

data = {
    '订单日期': dates,
    '商品类别': np.random.choice(categories, n_records, p=[0.3, 0.25, 0.2, 0.15, 0.1]),
    '销售区域': np.random.choice(regions, n_records),
    '销售额': np.random.exponential(500, n_records).round(2),
    '数量': np.random.randint(1, 10, n_records),
    '客户ID': np.random.randint(1000, 2000, n_records)
}

df = pd.DataFrame(data)
df['单价'] = (df['销售额'] / df['数量']).round(2)
df['月份'] = df['订单日期'].dt.month
df['季度'] = df['订单日期'].dt.quarter

# 2. 数据概览
print("=" * 50)
print("数据概览")
print("=" * 50)
print(f"数据时间范围: {df['订单日期'].min()} 至 {df['订单日期'].max()}")
print(f"总订单数: {len(df):,}")
print(f"总销售额: ¥{df['销售额'].sum():,.2f}")
print(f"平均订单金额: ¥{df['销售额'].mean():,.2f}")
print(f"客户数量: {df['客户ID'].nunique()}")

# 3. 销售趋势分析
# 月度销售趋势
monthly_sales = df.groupby(df['订单日期'].dt.to_period('M'))['销售额'].sum()

fig, ax = plt.subplots(figsize=(12, 6))
monthly_sales.plot(kind='line', marker='o', ax=ax)
ax.set_title('月度销售趋势', fontsize=16)
ax.set_xlabel('月份', fontsize=12)
ax.set_ylabel('销售额 (¥)', fontsize=12)
ax.yaxis.set_major_formatter(plt.FuncFormatter(lambda x, p: f'¥{x:,.0f}'))
plt.xticks(rotation=45)
plt.grid(True, alpha=0.3)
plt.tight_layout()
plt.savefig('monthly_sales_trend.png', dpi=300)
plt.show()

# 4. 类别分析
category_analysis = df.groupby('商品类别').agg({
    '销售额': ['sum', 'mean', 'count'],
    '数量': 'sum'
}).round(2)

category_analysis.columns = ['总销售额', '平均订单金额', '订单数', '总销量']
category_analysis = category_analysis.sort_values('总销售额', ascending=False)

print("\n" + "=" * 50)
print("商品类别分析")
print("=" * 50)
print(category_analysis)

# 可视化
fig, axes = plt.subplots(1, 2, figsize=(14, 6))

# 饼图 - 销售额占比
axes[0].pie(category_analysis['总销售额'], labels=category_analysis.index,
            autopct='%1.1f%%', startangle=90, colors=sns.color_palette("Set2"))
axes[0].set_title('各类别销售额占比', fontsize=14)

# 柱状图 - 订单数
axes[1].bar(category_analysis.index, category_analysis['订单数'],
            color=sns.color_palette("Set2"))
axes[1].set_title('各类别订单数', fontsize=14)
axes[1].set_ylabel('订单数')

plt.tight_layout()
plt.savefig('category_analysis.png', dpi=300)
plt.show()

# 5. 区域分析
region_analysis = df.groupby('销售区域').agg({
    '销售额': 'sum',
    '订单日期': 'count',
    '客户ID': 'nunique'
}).rename(columns={'订单日期': '订单数', '客户ID': '客户数'})

region_analysis['客单价'] = (region_analysis['销售额'] / region_analysis['订单数']).round(2)

print("\n" + "=" * 50)
print("区域分析")
print("=" * 50)
print(region_analysis.sort_values('销售额', ascending=False))

# 6. 客户分析
customer_analysis = df.groupby('客户ID').agg({
    '订单日期': 'count',
    '销售额': 'sum'
}).rename(columns={'订单日期': '订单数', '销售额': '总消费'})

# RFM分析简化版
customer_analysis['平均订单金额'] = (customer_analysis['总消费'] / customer_analysis['订单数']).round(2)

# 客户分层
customer_analysis['客户等级'] = pd.cut(
    customer_analysis['总消费'],
    bins=[0, 500, 2000, 5000, float('inf')],
    labels=['普通', '中等', '重要', 'VIP']
)

customer_segments = customer_analysis['客户等级'].value_counts()
print("\n" + "=" * 50)
print("客户分层分析")
print("=" * 50)
print(customer_segments)

# 7. 生成分析报告
report = f"""
# 电商销售数据分析报告

## 数据概览
- 分析时间范围: {df['订单日期'].min().strftime('%Y-%m-%d')} 至 {df['订单日期'].max().strftime('%Y-%m-%d')}
- 总订单数: {len(df):,}
- 总销售额: ¥{df['销售额'].sum():,.2f}
- 平均订单金额: ¥{df['销售额'].mean():,.2f}
- 独立客户数: {df['客户ID'].nunique()}

## 关键发现
1. **最畅销类别**: {category_analysis.index[0]}，销售额占比{category_analysis.iloc[0]['总销售额']/category_analysis['总销售额'].sum()*100:.1f}%
2. **最佳销售区域**: {region_analysis['销售额'].idxmax()}，销售额¥{region_analysis['销售额'].max():,.2f}
3. **VIP客户数量**: {customer_segments.get('VIP', 0)}人

## 建议
1. 加强{category_analysis.index[0]}类别的库存和营销
2. 深耕{region_analysis['销售额'].idxmax()}市场，扩大优势
3. 针对VIP客户制定专属优惠策略
"""

# 保存报告
with open('sales_analysis_report.md', 'w', encoding='utf-8') as f:
    f.write(report)

print("\n" + "=" * 50)
print("分析完成！报告已保存为 sales_analysis_report.md")
print("=" * 50)
```

**学习成果**：
- 掌握完整的数据分析流程
- 学会从数据中提取商业洞察
- 理解业务指标的计算和分析
- 能够生成专业的分析报告

---

## 学习检查点

完成每个阶段后，检查自己是否达到了学习目标。

### ✅ Python基础语法检查点

完成以下测试，确保掌握基础概念：

```python
# 测试1：变量与数据类型
# 创建一个包含姓名、年龄、成绩的字典，并打印类型
student = {"name": "Alice", "age": 20, "score": 95.5}
for key, value in student.items():
    print(f"{key}: {value} (类型: {type(value).__name__})")

# 测试2：控制流
# 编写程序判断一个数是否为素数
def is_prime(n):
    if n < 2:
        return False
    for i in range(2, int(n**0.5) + 1):
        if n % i == 0:
            return False
    return True

print(is_prime(17))  # True
print(is_prime(24))  # False

# 测试3：函数
# 编写一个函数，接受任意数量的数字参数，返回它们的平均值
def average(*args):
    if not args:
        return 0
    return sum(args) / len(args)

print(average(1, 2, 3, 4, 5))  # 3.0

# 测试4：面向对象
# 创建一个"银行账户"类，支持存款、取款、查询余额
class BankAccount:
    def __init__(self, balance=0):
        self._balance = balance
    
    def deposit(self, amount):
        if amount > 0:
            self._balance += amount
            return True
        return False
    
    def withdraw(self, amount):
        if 0 < amount <= self._balance:
            self._balance -= amount
            return True
        return False
    
    def get_balance(self):
        return self._balance

account = BankAccount(1000)
account.deposit(500)
account.withdraw(200)
print(f"余额: {account.get_balance()}")  # 1300

# 测试5：异常处理
# 编写一个安全的整数输入函数
def safe_input_int(prompt):
    while True:
        try:
            return int(input(prompt))
        except ValueError:
            print("请输入有效的整数！")

# 测试6：文件操作
# 读取一个文本文件，统计行数、单词数和字符数
def file_stats(filename):
    try:
        with open(filename, 'r', encoding='utf-8') as f:
            content = f.read()
            lines = content.splitlines()
            words = content.split()
            return {
                'lines': len(lines),
                'words': len(words),
                'characters': len(content)
            }
    except FileNotFoundError:
        return None
```

### ✅ 数据处理库检查点

```python
import numpy as np
import pandas as pd

# 测试1：NumPy基础
# 创建一个5x5的随机矩阵，计算其转置、行列式和逆矩阵
matrix = np.random.rand(5, 5)
transpose = matrix.T
determinant = np.linalg.det(matrix)
try:
    inverse = np.linalg.inv(matrix)
    print("矩阵可逆")
except np.linalg.LinAlgError:
    print("矩阵不可逆")

# 测试2：NumPy广播
# 标准化一个矩阵（每列减去均值，除以标准差）
data = np.random.rand(10, 5)
mean = np.mean(data, axis=0)
std = np.std(data, axis=0)
normalized = (data - mean) / std
print(f"标准化后均值: {np.mean(normalized, axis=0)}")  # 接近0
print(f"标准化后标准差: {np.std(normalized, axis=0)}")  # 接近1

# 测试3：Pandas基础
# 创建一个DataFrame，进行数据清洗和分析
df = pd.DataFrame({
    'name': ['Alice', 'Bob', 'Charlie', 'David', None],
    'age': [25, 30, None, 28, 35],
    'salary': [15000, 20000, 18000, 16000, 22000]
})

# 处理缺失值
df['name'].fillna('Unknown', inplace=True)
df['age'].fillna(df['age'].median(), inplace=True)

# 添加新列
df['salary_level'] = df['salary'].apply(lambda x: 'High' if x > 18000 else 'Medium' if x > 15000 else 'Low')

# 分组统计
print(df.groupby('salary_level')['age'].mean())
```

### ✅ 数据可视化检查点

```python
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np

# 测试1：创建多子图布局
fig, axes = plt.subplots(2, 2, figsize=(12, 10))

# 折线图
x = np.linspace(0, 10, 100)
axes[0, 0].plot(x, np.sin(x))
axes[0, 0].set_title('Sine Wave')

# 柱状图
categories = ['A', 'B', 'C', 'D']
values = [25, 40, 30, 55]
axes[0, 1].bar(categories, values)
axes[0, 1].set_title('Bar Chart')

# 散点图
axes[1, 0].scatter(np.random.randn(50), np.random.randn(50))
axes[1, 0].set_title('Scatter Plot')

# 直方图
axes[1, 1].hist(np.random.randn(100), bins=20)
axes[1, 1].set_title('Histogram')

plt.tight_layout()
plt.show()

# 测试2：Seaborn统计图
tips = sns.load_dataset("tips")
plt.figure(figsize=(10, 6))
sns.boxplot(x="day", y="total_bill", data=tips)
plt.title('Box Plot')
plt.show()

# 测试3：热力图
data = np.random.rand(10, 10)
plt.figure(figsize=(8, 6))
sns.heatmap(data, annot=True, cmap='coolwarm')
plt.title('Heatmap')
plt.show()
```

---

## 常见问题

### Q1: 我应该使用Python 2还是Python 3？

**A**: 毫无疑问，选择**Python 3**。Python 2已于2020年1月1日停止支持，不再接收安全更新。所有现代库和框架都已迁移到Python 3。建议使用Python 3.8或更高版本。

### Q2: 我应该使用Anaconda还是pip安装Python？

**A**: 推荐初学者使用**Anaconda**或**Miniconda**：
- **Anaconda**：包含Python、常用库和图形界面，适合初学者
- **Miniconda**：更轻量，只包含Python和conda，适合有经验的用户
- **pip**：Python内置包管理器，需要手动管理环境

对于AI学习，Anaconda预装了NumPy、Pandas、Matplotlib等常用库，省去很多安装麻烦。

### Q3: 如何选择IDE或编辑器？

**A**: 根据需求选择：
- **Jupyter Notebook**：适合数据分析、探索性编程、学习
- **VS Code**：轻量、扩展丰富，适合各种开发
- **PyCharm**：功能强大的专业IDE，适合大型项目
- **Google Colab**：免费云端环境，适合没有本地GPU的情况

建议：学习阶段使用Jupyter Notebook，项目开发使用VS Code。

### Q4: 学习Python需要多长时间？

**A**: 取决于学习目标和投入时间：
- **基础语法**：2-4周（每天2-3小时）
- **数据处理**：2-3周
- **数据可视化**：1-2周
- **达到入门AI水平**：2-3个月

关键是**持续练习**，而不是追求速度。

### Q5: 我遇到了"ModuleNotFoundError"怎么办？

**A**: 这个错误表示缺少所需的库。解决方法：
```bash
# 安装单个库
pip install numpy

# 安装多个库
pip install numpy pandas matplotlib seaborn

# 使用requirements.txt安装
pip install -r requirements.txt

# 如果使用conda
conda install numpy pandas matplotlib
```

### Q6: 如何处理中文编码问题？

**A**: Python 3默认使用UTF-8编码，但仍可能遇到问题：
```python
# 读取文件时指定编码
with open('file.txt', 'r', encoding='utf-8') as f:
    content = f.read()

# 如果还是乱码，尝试其他编码
with open('file.txt', 'r', encoding='gbk') as f:
    content = f.read()

# Matplotlib显示中文
plt.rcParams['font.sans-serif'] = ['SimHei']  # Windows
plt.rcParams['font.sans-serif'] = ['Arial Unicode MS']  # macOS
plt.rcParams['axes.unicode_minus'] = False
```

### Q7: 如何提高代码运行效率？

**A**: 多种优化方法：
1. **使用向量化操作**：NumPy比纯Python循环快100倍以上
2. **避免循环**：使用Pandas的apply、向量化操作
3. **使用适当的数据类型**：如category类型节省内存
4. **使用更高效的库**：如Polars替代Pandas处理大数据
5. **并行处理**：使用multiprocessing或joblib

```python
# 示例：向量化 vs 循环
import numpy as np

# 慢：Python循环
result = [x**2 for x in range(1000000)]

# 快：NumPy向量化
result = np.arange(1000000) ** 2
```

### Q8: 我应该先学数据分析还是机器学习？

**A**: 建议按以下顺序：
1. **Python基础**（必须）
2. **数据分析**（NumPy、Pandas、Matplotlib）
3. **统计学基础**（概率、假设检验、回归）
4. **机器学习**（Scikit-learn）
5. **深度学习**（TensorFlow、PyTorch）

数据分析是机器学习的基础，不理解数据就无法建立好的模型。

### Q9: 如何保持学习动力？

**A**: 多种方法：
1. **设定明确目标**：如"3个月内完成一个数据分析项目"
2. **动手实践**：每学一个概念就写代码练习
3. **参与社区**：加入Python学习群、论坛
4. **做项目**：从简单项目开始，逐步增加难度
5. **记录进步**：写学习笔记、博客
6. **找到学习伙伴**：互相督促、交流

### Q10: 遇到错误怎么办？

**A**: 解决错误的步骤：
1. **仔细阅读错误信息**：Python的错误提示通常很明确
2. **Google搜索**：将错误信息复制到搜索引擎
3. **查看官方文档**：了解函数的正确用法
4. **使用调试器**：如pdb或IDE的调试功能
5. **提问求助**：在Stack Overflow或社区提问时，提供完整代码和错误信息

```python
# 调试技巧
import pdb; pdb.set_trace()  # 设置断点

# 或使用print调试
print(f"变量x的值: {x}")
print(f"变量类型: {type(x)}")
```

---

## 下一步学习

完成本阶段后，你已经掌握了Python编程和数据处理的基础技能。接下来可以进入：

**03阶段 - 机器学习基础**
- 学习Scikit-learn库
- 理解监督学习和无监督学习
- 掌握常用算法（线性回归、决策树、SVM等）
- 完成机器学习项目

**预习建议**：
1. 复习线性代数基础（矩阵运算）
2. 学习概率统计基础
3. 了解机器学习的基本概念

---

> **学习建议**：编程是一项实践性很强的技能，光看书或视频是不够的。每天至少花1-2小时写代码，从模仿开始，逐步独立解决问题。遇到困难不要气馁，每个程序员都是从错误中学习成长的。

---

**文档版本**：v1.0  
**最后更新**：2024年  
**适用对象**：AI学习路径入门阶段  
**预计学习时长**：6-9周（每周10-15小时）