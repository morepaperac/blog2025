# 🖥️ Code Repository

```bash
$ neofetch --ascii
       _____          __
      / ___/__  ___/ /__
     / /__/ _ \/ _  / -_)
     \___/\___/\_,_/\__/
     
     @jasoncc's code vault
     ━━━━━━━━━━━━━━━━━━━━━
     OS      → Algorithm & AI
     Lang    → Python / C++ / Go
     Focus   → LLM / RecSys / Leetcode
     Status  → Always Learning...
```

<div align="center">

[![GitHub](https://img.shields.io/badge/GitHub-AI--code-181717?style=for-the-badge&logo=github)](https://github.com/morepaperac/AI-code)
[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://github.com/morepaperac/AI-code)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.0+-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)](https://github.com/morepaperac/AI-code)

</div>

> 💡 **Mission**: 把学到的算法，用代码实现一遍，才算真正掌握。

---

## 📚 Leetcode 专区

```python
class Solution:
    """刷题记录与经典算法实现"""
    topics = ["DataStructure", "DP", "TwoPointers", "Graph"]
```

| 模块 | 说明 | 链接 |
| :---: | :--- | :---: |
| 🏗️ **数据结构** | 链表、树、图、堆、栈等基础数据结构实现 | [→](https://github.com/morepaperac/AI-code/tree/main/Leetcode/DataStructure) |
| 📊 **动态规划** | 背包、子序列、区间 DP、状态压缩 | [→](https://github.com/morepaperac/AI-code/tree/main/Leetcode/DP) |
| 👆 **双指针/滑窗** | 双指针、滑动窗口、快慢指针 | [→](https://github.com/morepaperac/AI-code/tree/main/Leetcode/TwoPointers) |
| 🕸️ **图论算法** | DFS、BFS、Dijkstra、拓扑排序 | [→](https://github.com/morepaperac/AI-code/tree/main/Leetcode/Graph) |

---

## 🤖 LLM 专区

```python
class Transformer(nn.Module):
    """大语言模型核心组件"""
    def __init__(self):
        self.attention = MultiHeadAttention()  # <- 从这里开始
        self.norm = RMSNorm()
        self.pos_enc = RoPE()
```

| 模块 | 说明 | API | 链接 |
| :---: | :--- | :--- | :---: |
| ⚡ **MHA** | 多头注意力 + FlashAttention | `x:(B,T,C)` | [→](https://github.com/morepaperac/AI-code/tree/main/LLM/MHA) |
| 🔀 **GQA** | 分组查询注意力 (Llama2) | `x:(B,T,C)` | [→](https://github.com/morepaperac/AI-code/tree/main/LLM/GQA) |
| 🎯 **MQA** | 多查询注意力 (Falcon) | `x:(B,T,C)` | [→](https://github.com/morepaperac/AI-code/tree/main/LLM/MQA) |
| 🪟 **SWA** | 滑动窗口注意力 (Mistral) | `x:(B,T,C)` | [→](https://github.com/morepaperac/AI-code/tree/main/LLM/SWA) |
| 🌀 **MoBA** | Kimi 稀疏注意力 | `x:(B,T,C)` | [→](https://github.com/morepaperac/AI-code/tree/main/LLM/MoBA) |
| 📍 **PosEncoding** | RoPE / AbsPE / LearnedPE | `x:(B,T,C)` | [→](https://github.com/morepaperac/AI-code/tree/main/LLM/PosEncoding) |
| 📏 **Norm** | LayerNorm / RMSNorm / BatchNorm | `(B,T,C)` | [→](https://github.com/morepaperac/AI-code/tree/main/LLM/Norm) |

---

## 🎯 搜广推专区

```python
class RecSystem:
    """搜索、广告、推荐系统"""
    pipeline = ["Recall", "Ranking", "ReRanking"]
    #            召回  →  精排  →  重排
```

| 模块 | 说明 | 链接 |
| :---: | :--- | :---: |
| 🧬 **Embedding** | 用户/物品 Embedding 层 | [→](https://github.com/morepaperac/AI-code/tree/main/RecSys/Embedding) |
| 🏰 **双塔模型** | 召回阶段 Two-Tower 架构 | [→](https://github.com/morepaperac/AI-code/tree/main/RecSys/TwoTower) |
| 📈 **排序模型** | DeepFM / DCN / DIN | [→](https://github.com/morepaperac/AI-code/tree/main/RecSys/Ranking) |
| 🎛️ **多目标优化** | MMOE / PLE / ESMM | [→](https://github.com/morepaperac/AI-code/tree/main/RecSys/MTL) |

---

## 🛠️ 工具类专区

```python
from utils import ResNet, ConvNeXt, Tokenizer, DataLoader
# 常用工具函数与视觉编码器
```

| 模块 | 说明 | 链接 |
| :---: | :--- | :---: |
| 🖼️ **ResNet** | ResNet50 / 101 / 152 | [→](https://github.com/morepaperac/AI-code/tree/main/Utils/ResNet) |
| 🎨 **ConvNeXt** | ConvNeXt v1 系列 | [→](https://github.com/morepaperac/AI-code/tree/main/Utils/ConvNeXt) |
| ✂️ **Tokenizer** | BPE / WordPiece | [→](https://github.com/morepaperac/AI-code/tree/main/Utils/Tokenizer) |
| 📦 **DataLoader** | 高效数据加载 | [→](https://github.com/morepaperac/AI-code/tree/main/Utils/DataLoader) |

---

```bash
$ echo "Happy Coding! 🚀"
Happy Coding! 🚀

$ git commit -m "keep learning, keep growing"
[main ******] keep learning, keep growing
```
