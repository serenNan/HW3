# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 项目概述

这是一个机器学习作业项目（HW3），专注于使用深度强化学习（DDQN - Double Deep Q-Network）进行配对交易策略开发。

### ✅ 项目状态：已完成

所有作业要求已完成，所有代码和说明整合在 `HW3.ipynb` 文件中：
1. ✅ 使用LLM建议了10个DDQN模型（Notebook Part 1）
2. ✅ 选择Dueling DDQN并生成完整代码（Notebook Part 3）
3. ✅ 实现数据分割和训练流程（Notebook Part 4-5）
4. ✅ 在测试集上生成预测（Notebook Part 6）
5. ✅ 完整的交易结果评估系统（Notebook Part 7）

### 核心任务

1. **模型设计**: 使用LLM建议10个DDQN模型用于配对交易，从中选择一个并生成代码
2. **数据处理**: 将数据分割为训练集和测试集
3. **模型训练**: 在训练集上训练DDQN模型
4. **预测与评估**: 使用训练好的模型在测试集上生成交易预测，并评估交易结果

## 开发环境

- **Python环境**: 使用conda管理虚拟环境
- **推荐环境**: 创建专门的conda环境用于深度学习（需要PyTorch、NumPy、Pandas等）
- **依赖安装**: `pip install -r requirements.txt`

## 项目结构

```
HW3/
├── HW3.ipynb          # 主要提交文件（包含所有代码和说明）
├── requirements.txt   # Python依赖列表
├── README.md          # 快速开始指南
├── CLAUDE.md          # 本文件
└── docs/              # 参考文档
    ├── 01_DDQN模型建议.md
    ├── 02_实现说明.md
    └── 项目完成总结.md
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
# 安装依赖
pip install -r requirements.txt

# 或使用conda环境
conda create -n hw3_trading python=3.9
conda activate hw3_trading
pip install -r requirements.txt
```

### 运行Notebook
```bash
# 启动Jupyter Notebook
jupyter notebook HW3.ipynb

# 或使用JupyterLab
jupyter lab HW3.ipynb
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

## 使用说明

1. 打开 `HW3.ipynb` 文件
2. 在 Part 2 中设置运行模式：
   - `QUICK_MODE = True`：快速模式（50 episodes，约5-10分钟）
   - `QUICK_MODE = False`：完整模式（500 episodes，约30-60分钟）
3. 依次执行所有代码单元格，或使用 "Run All" 功能
4. 查看训练过程、性能指标和可视化结果
- 代码和注释使用英文，只有和我的对话保持中文