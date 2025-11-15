# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 项目概述

这是一个机器学习作业项目（HW3），专注于使用深度强化学习（DDQN - Double Deep Q-Network）进行配对交易策略开发。

### 核心任务

1. **模型设计**: 使用LLM建议10个DDQN模型用于配对交易，从中选择一个并生成代码
2. **数据处理**: 将数据分割为训练集和测试集
3. **模型训练**: 在训练集上训练DDQN模型
4. **预测与评估**: 使用训练好的模型在测试集上生成交易预测，并评估交易结果

## 开发环境

- **Python环境**: 使用conda管理虚拟环境
- **推荐环境**: 创建专门的conda环境用于深度学习（需要PyTorch/TensorFlow、NumPy、Pandas等）

## 项目结构建议

```
HW3/
├── data/              # 配对交易数据集
├── models/            # DDQN模型定义
├── training/          # 训练脚本
├── evaluation/        # 评估和回测脚本
├── notebooks/         # Jupyter notebooks（用于实验和可视化）
├── utils/             # 辅助工具函数
└── results/           # 训练结果和性能指标
```

## 关键技术要点

### DDQN模型特点
- 使用双Q网络减少过估计问题
- 适用于金融交易的离散动作空间
- 需要经验回放缓冲区和目标网络

### 配对交易策略
- 状态空间：价差、协整关系、技术指标等
- 动作空间：买入/卖出/持有配对头寸
- 奖励函数：交易收益、夏普比率等

### 数据要求
- 历史价格数据（至少两个相关资产）
- 技术指标计算
- 合适的训练/测试集分割比例（建议70-30或80-20）

## 常用命令

### 环境设置
```bash
# 创建conda环境（如需要）
conda create -n hw3_trading python=3.9
conda activate hw3_trading

# 安装依赖
pip install torch numpy pandas matplotlib sklearn
```

### 运行训练
```bash
# 训练模型
python training/train_ddqn.py --epochs 1000 --batch-size 64

# 评估模型
python evaluation/evaluate.py --model-path models/best_model.pth
```

### 数据处理
```bash
# 数据预处理
python utils/preprocess_data.py --input data/raw/ --output data/processed/
```

## 实现注意事项

1. **模型选择**: 在LLM建议的10个DDQN变体中，优先考虑：
   - 适合金融时间序列的网络架构
   - 计算效率与性能的平衡
   - 可解释性和可调试性

2. **训练策略**:
   - 使用足够大的经验回放缓冲区
   - 实现epsilon-greedy探索策略
   - 定期保存检查点
   - 监控训练/验证性能指标

3. **评估指标**:
   - 累计收益率
   - 夏普比率
   - 最大回撤
   - 胜率和盈亏比
   - 交易频率

4. **风险管理**:
   - 实现仓位限制
   - 止损/止盈逻辑
   - 考虑交易成本和滑点

## 文件命名约定

- 模型文件: `ddqn_v{version}.py` 或 `{model_name}_ddqn.py`
- 训练脚本: `train_*.py`
- 数据文件: `data_*.csv` 或 `*.parquet`
- 配置文件: `config.yaml` 或 `config.json`
