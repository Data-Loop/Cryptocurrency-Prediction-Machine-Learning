加密货币价格趋势预测系统

项目简介

本项目构建了一个基于机器学习的加密货币价格趋势预测系统。通过分析历史交易数据，利用多种机器学习算法对加密货币价格趋势进行预测，并通过多种优化方法提升模型性能。该系统不仅实现了基础的二分类预测，还开发了更细致的四分类预测模型，并通过多种优化方案显著提升了预测准确率和类别平衡性。

数据集

基本信息

数据来源：Kaggle加密货币市场数据集

样本数量：10,422条记录

特征维度：9个关键特征

时间范围：包含多个时间观察角度的价格变化率

特征列表

特征名称

描述

单位

Price

当前价格

USD

Volume (24h)

24小时交易量

USD

Market Cap

市值

USD

Num Market Pairs

市场交易对数

个

1h %

1小时价格变化率

%

24h %

24小时价格变化率

%

7d %

7天价格变化率

%

60d %

60天价格变化率

%

90d %

90天价格变化率

%

主要功能

1. 二分类预测

预测价格涨跌方向

基于24小时价格变化率

适用于短期交易决策

2. 四分类预测

类别细分为四种情况：

大跌（≤-5%）

小跌（-5%至0%）

小涨（0%至5%）

大涨（>5%）

提供更精细的市场趋势判断

3. 多种模型实现

基础模型

支持向量机(SVM)

使用RBF核函数

适合非线性分类问题

决策树

可解释性强

适合特征间存在交互作用的场景

XGBoost

集成学习方法

优秀的预测性能

随机森林

降低过拟合风险

提供特征重要性评估

优化方案

类别权重调整

解决类别不平衡问题

提高少数类别预测准确率

SMOTETomek平衡采样

生成合成样本

清理类别边界

改善数据分布

集成学习

结合多个基础模型

提高预测稳定性

降低单一模型风险

技术栈

开发环境

Python 3.8+

Jupyter Notebook

核心依赖库

scikit-learn==1.0.2
xgboost==1.5.0
imbalanced-learn==0.8.1
pandas==1.3.3
numpy==1.21.2
matplotlib==3.4.3
seaborn==0.11.2

主要结果

1. 基础模型性能

模型

准确率

F1分数

召回率

SVM

80.48%

0.79

0.80

决策树

75.32%

0.75

0.75

XGBoost

82.15%

0.82

0.82

随机森林

81.94%

0.81

0.82

2. 优化后性能

加权随机森林：

上涨预测准确率：64.2%

下跌预测准确率：63.8%

整体类别平衡性显著提升

SMOTETomek_XGBoost：

整体准确率：73.86%

F1分数：0.74

类别平衡性最优

快速开始

1. 环境配置

# 克隆项目
克隆项目

# 创建虚拟环境
python -m venv venv
source venv/bin/activate # Linux/Mac
venv\Scripts\activate # Windows

# 安装依赖
pip install -r requirements.txt

2. 数据预处理

from models.binary_classification import preprocess_data

# 加载并预处理数据
X_train, X_test, y_train, y_test = preprocess_data('data/crypto_data.csv')

3. 模型训练

from models.binary_classification import train_model

# 训练模型
model = train_model(X_train, y_train, model_type='xgboost')

4. 预测

# 进行预测
predictions = model.predict(X_test)

性能优化建议

1. 特征工程

添加技术指标（RSI、MACD等）

构建时间序列特征

考虑市场情绪因素

添加完善经济指标

2. 模型调优

使用网格搜索优化超参

尝试深度学习模型（LSTM、Transformer）

集成更多基础模型

优化采样策略

3. 系统优化

实现实时预测功能

添加风险控制模块

优化模型部署效率

增加可视化监控

贡献指南

Fork 项目

创建特性分支

提交更改

推送到分支

创建 Pull Request

联系方式

作者：loop

邮箱：aacha@foxmail.com

致谢

感谢Kaggle提供的优质数据集

感谢所有开源库的贡献者

感谢项目指导老师的悉心指导

特别感谢在项目开发过程中提供支持的团队成员和朋友
