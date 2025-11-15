# HW3: 基于Dueling DDQN的配对交易策略

## 📚 项目说明

本项目使用深度强化学习（Dueling DDQN）实现配对交易策略，所有代码和说明都整合在一个 Jupyter Notebook 文件中。

## 🚀 快速开始

### 1. 安装依赖

```bash
pip install -r requirements.txt
```

### 2. 运行Notebook

```bash
jupyter notebook HW3.ipynb
```

或使用VS Code、JupyterLab等打开 `HW3.ipynb` 文件。

### 3. 执行所有单元格

在Notebook中依次执行所有代码单元格，或使用 "Run All" 功能。

## 📁 文件说明

### 核心文件

- **`HW3.ipynb`** - 主要提交文件（自包含，包含所有代码和说明）
  - Part 1: 10个DDQN模型建议
  - Part 2: 环境配置
  - Part 3: 核心代码实现
  - Part 4: 数据准备和分割
  - Part 5: 模型训练
  - Part 6: 测试集预测
  - Part 7: 交易结果评估
  - Part 8: 总结

### 配置文件

- **`requirements.txt`** - Python依赖列表
- **`.gitignore`** - Git忽略规则

### 参考文档（可选）

- `docs/01_DDQN模型建议.md` - 10个模型的详细分析
- `docs/02_实现说明.md` - 实现细节说明
- `docs/项目完成总结.md` - 完成情况总结

## ⚙️ 配置选项

在Notebook的Part 2中可以选择运行模式：

```python
QUICK_MODE = True   # 快速模式: 50 episodes（5-10分钟）
QUICK_MODE = False  # 完整模式: 500 episodes（30-60分钟）
```

**建议**：首次运行使用快速模式验证流程，确认无误后再使用完整模式。

## 📊 输出结果

运行Notebook后会生成：

- `data/` - 训练和测试数据
- `results/` - 可能的模型保存文件
- 多个可视化图表（内嵌在Notebook中）
- 详细的性能指标输出

## ✅ 作业完成情况

| 任务 | 完成情况 | 对应Notebook部分 |
|------|---------|-----------------|
| 任务1: 使用LLM建议10个DDQN模型 | ✅ | Part 1 |
| 任务2: 选择模型并生成代码 | ✅ | Part 1 & 3 |
| 任务3: 分割数据并训练模型 | ✅ | Part 4 & 5 |
| 任务4: 测试集预测 | ✅ | Part 6 |
| 任务5: 评估交易结果 | ✅ | Part 7 |

## 🎯 技术要点

### 选择的模型: Dueling DDQN
- 分离状态价值V(s)和动作优势A(s,a)
- 公式: `Q(s,a) = V(s) + (A(s,a) - mean(A(s,a)))`
- 优势: 更准确的Q值估计，训练更稳定

### 实现特点
- **状态空间**: 11维（z-score, 价差统计, 持仓等）
- **动作空间**: 4个（平仓/做多/做空/持有）
- **环境**: 真实交易成本建模（0.1%）
- **评估**: 多维度性能指标和可视化

## 💻 环境要求

- Python 3.8+
- Jupyter Notebook / JupyterLab
- 至少4GB内存
- （可选）NVIDIA GPU用于加速训练

## 🐛 故障排查

### 问题：导入错误
```bash
# 解决方案
pip install -r requirements.txt
```

### 问题：Jupyter未安装
```bash
# 解决方案
pip install jupyter
```

### 问题：CUDA内存不足
```python
# 在Notebook中设置
import os
os.environ['CUDA_VISIBLE_DEVICES'] = ''  # 使用CPU
```

## 📖 使用建议

1. **首次运行**: 使用快速模式（50 episodes）验证流程
2. **完整训练**: 确认无误后，修改为完整模式（500 episodes）
3. **查看结果**: 所有图表和指标都内嵌在Notebook中
4. **保存工作**: Jupyter会自动保存，也可手动保存Notebook

## 📝 提交说明

作业提交时，只需提交：
- `HW3.ipynb` - 包含所有代码、说明和输出结果
- `requirements.txt` - 方便环境配置
- （可选）`docs/` 文件夹 - 参考文档

## 🎓 学习资源

- [Dueling Network Architectures (论文)](https://arxiv.org/abs/1511.06581)
- [Deep Reinforcement Learning with Double Q-learning](https://arxiv.org/abs/1509.06461)
- [Human-level control through deep RL](https://www.nature.com/articles/nature14236)

---

**开始使用Jupyter Notebook完成作业！** 🚀

```bash
jupyter notebook HW3.ipynb
```
