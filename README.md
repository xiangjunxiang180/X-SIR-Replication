# X-SIR: Semantic-Invariant Robust Watermarking for Large Language Models
## 项目完整复现 | KGW/SIR/X-SIR 三大算法对比验证

---

## 📖 项目简介
本项目是对顶会论文 **X-SIR: Semantic-Invariant Robust Watermarking for Large Language Models** 的完整工程复现，从零实现并对比了**3种主流大语言模型水印算法**，并完成了翻译攻击场景下的鲁棒性验证，完整覆盖「水印嵌入-水印检测-性能评估-攻击验证」全流程。

### 核心实现内容
- ✅ **KGW (Kirchenbauer et al.)**：传统词级硬水印算法，作为基线对比
- ✅ **SIR (Semantic-Invariant Robust)**：全局语义级鲁棒水印算法
- ✅ **X-SIR (Chunk-based Semantic-Invariant Robust)**：论文核心创新，分块语义级鲁棒水印算法（终极版）
- ✅ 翻译攻击场景下的抗攻击能力完整对比验证

---

## 📊 核心实验结果（真实复现数据）
### 1. 干净文本（无攻击）检测性能
| 算法  | AUC  | TPR@FPR=0.1 | TPR@FPR=0.01 | F1@FPR=0.1 | F1@FPR=0.01 |
|-------|------|-------------|--------------|------------|-------------|
| KGW   | 1.000 | 0.998       | 0.998        | -          | -           |
| SIR   | 0.993 | 0.980       | 0.910        | 0.946      | 0.948       |
| X-SIR | 0.994 | 0.994       | 0.862        | 0.955      | 0.921       |

### 2. 翻译攻击后（英文→中文）检测性能
| 算法  | 攻击后 AUC | 性能保留率 | 核心结论 |
|-------|------------|------------|----------|
| KGW   | 0.445      | 0%         | 水印完全失效，等同于随机猜测 |
| SIR   | 0.993      | 100%       | 水印完全保留，抗翻译攻击能力极强 |
| X-SIR | 0.993      | 99.9%      | 水印几乎无损，分块语义设计带来极致鲁棒性 |

---

## 🛠️ 实验环境
- 基础大模型：`baichuan-inc/Baichuan-7B`
- 操作系统：Windows 10/11
- Python 版本：Python 3.9
- 核心依赖：PyTorch, HuggingFace Transformers, Sentence-BERT
- 测试数据集：MC4 英文通用文本数据集

---
