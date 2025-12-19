# 🖥️ Code Repository

```text
 ██████╗ ██████╗ ██████╗ ███████╗
██╔════╝██╔═══██╗██╔══██╗██╔════╝
██║     ██║   ██║██║  ██║█████╗  
██║     ██║   ██║██║  ██║██╔══╝  
╚██████╗╚██████╔╝██████╔╝███████╗
 ╚═════╝ ╚═════╝ ╚═════╝ ╚══════╝
```

> 💡 这里汇集了我在算法学习积累的代码实现。
>
> 🔗 **GitHub**: [morepaperac/AI-code](https://github.com/morepaperac/AI-code)

---

## 📚 Leetcode 专区

> 刷题记录与经典算法实现

| 名称 | 说明 | 链接 |
| :---: | :--- | :---: |
| 数据结构 | 链表、树、图、堆、栈等基础数据结构实现 | [🔗](https://github.com/morepaperac/AI-code/tree/main/Leetcode/DataStructure) |
| 动态规划 | 经典 DP 问题：背包、子序列、区间 DP 等 | [🔗](https://github.com/morepaperac/AI-code/tree/main/Leetcode/DP) |
| 双指针/滑窗 | 双指针、滑动窗口相关题解 | [🔗](https://github.com/morepaperac/AI-code/tree/main/Leetcode/TwoPointers) |
| 图论算法 | DFS、BFS、最短路、拓扑排序等 | [🔗](https://github.com/morepaperac/AI-code/tree/main/Leetcode/Graph) |

---

## 🤖 LLM 专区

> 大语言模型核心组件实现

| 名称 | 说明 | 链接 |
| :---: | :--- | :---: |
| MHA | 多头注意力模块，支持 `flash_attn`，输入：`x:(B,T,C), atten_mask:(B,T)` | [🔗](https://github.com/morepaperac/AI-code/tree/main/LLM/MHA) |
| GQA | 分组查询注意力，支持 `flash_attn`，输入：`x:(B,T,C), atten_mask:(B,T)` | [🔗](https://github.com/morepaperac/AI-code/tree/main/LLM/GQA) |
| MQA | 多查询注意力，支持 `flash_attn`，输入：`x:(B,T,C), atten_mask:(B,T)` | [🔗](https://github.com/morepaperac/AI-code/tree/main/LLM/MQA) |
| SWA | 滑动窗口注意力，支持 `flash_attn`，输入：`x:(B,T,C), atten_mask:(B,T)` | [🔗](https://github.com/morepaperac/AI-code/tree/main/LLM/SWA) |
| MoBA | Kimi MoBA 稀疏注意力，输入：`x:(B,T,C), atten_mask:(B,T)` | [🔗](https://github.com/morepaperac/AI-code/tree/main/LLM/MoBA) |
| PosEncoding | 位置编码：`RoPE`、`AbsPE`、`LearnedPE`，输入：`x:(B,T,C)` | [🔗](https://github.com/morepaperac/AI-code/tree/main/LLM/PosEncoding) |
| Norm | 归一化：`LayerNorm`、`RMSNorm`、`BatchNorm` 等，输入：`(B,T,C)` 或 `(B,C,H,W)` | [🔗](https://github.com/morepaperac/AI-code/tree/main/LLM/Norm) |

---

## 🎯 搜广推专区

> 搜索、广告、推荐系统相关实现

| 名称 | 说明 | 链接 |
| :---: | :--- | :---: |
| Embedding | 用户/物品 Embedding 层实现 | [🔗](https://github.com/morepaperac/AI-code/tree/main/RecSys/Embedding) |
| 双塔模型 | 召回阶段双塔模型架构 | [🔗](https://github.com/morepaperac/AI-code/tree/main/RecSys/TwoTower) |
| 排序模型 | DeepFM、DCN、DIN 等精排模型 | [🔗](https://github.com/morepaperac/AI-code/tree/main/RecSys/Ranking) |
| 多目标优化 | MMOE、PLE 等多任务学习模型 | [🔗](https://github.com/morepaperac/AI-code/tree/main/RecSys/MTL) |

---

## 🛠️ 工具类专区

> 常用工具函数与视觉编码器

| 名称 | 说明 | 链接 |
| :---: | :--- | :---: |
| ResNet | 视觉编码器：`ResNet50`、`ResNet101`、`ResNet152` 系列 | [🔗](https://github.com/morepaperac/AI-code/tree/main/Utils/ResNet) |
| ConvNeXt | 视觉编码器：`ConvNeXt v1` 系列 | [🔗](https://github.com/morepaperac/AI-code/tree/main/Utils/ConvNeXt) |
| Tokenizer | 分词器实现：BPE、WordPiece 等 | [🔗](https://github.com/morepaperac/AI-code/tree/main/Utils/Tokenizer) |
| DataLoader | 高效数据加载与预处理工具 | [🔗](https://github.com/morepaperac/AI-code/tree/main/Utils/DataLoader) |

---

<p align="center">
  <code>// TODO: Keep coding, keep learning 🚀</code>
</p>
