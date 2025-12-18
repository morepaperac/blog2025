---
title: How Attention Got So Efficient
published: 2025-12-19
description: Attention各种变种
tags: [Attention, KV Cache]
category: 大模型
draft: false
---

## Token Embeddings: The Starting Point

在 Transformer 架构中，一切始于 Token Embeddings。

**Token Embedding** 的核心作用是将离散的单词（Token）映射到一个连续的向量空间中。在这个空间里，语义相似的词在距离上会更加接近。例如，"Cat" 和 "Dog" 的向量距离会比 "Cat" 和 "Car" 更近。

然而，传统的 Token Embedding 有一个致命的局限性：**静态性（Static）**。
它**不包含任何上下文信息**。这意味着无论单词出现在什么语境下，它的初始 Embedding 都是一样的。

> *例子*：
> 单词 "Bank" 在 "River bank"（河岸）和 "Bank account"（银行账户）中意思完全不同，但在输入 Attention 层之前，它们的 Embedding 是完全相同的。

这就是为什么我们需要引入 **Attention 机制** —— 它的作用就是让 Token 之间进行"交流"，从而根据上下文调整每个 Token 的表示。

## Attention Mechanism

Attention 机制的核心在于将输入的 Token 向量映射为 **Query (Q)**, **Key (K)**, 和 **Value (V)** 三个向量。

### 为什么是 Q, K, V?

这可以类比为一个**搜索引擎**或**文件检索系统**：

* **Query (Q)**: 你手里的问题（"我想要找什么"）。
* **Key (K)**: 数据库中资料的标签或索引（"这个资料含有什么特征"）。
* **Value (V)**: 数据库中的实际内容（"这个资料的具体信息"）。

Attention 的过程就是：拿你的 **Q** 去和所有的 **K** 计算相似度，根据相似度（权重）来加权聚合对应的 **V**。

### 1. 投影 (Projection)

对于一个输入向量 $x$（维度 $1 \times d$），我们需要将其投影到 Head 维度。以 **DeepSeek-V3** 为例 ($d=7168, d_k=128$)：

$$
\begin{aligned}
q &= x \cdot W_q \\
k &= x \cdot W_k \\
v &= x \cdot W_v
\end{aligned}
$$

其中 $W_q, W_k, W_v \in \mathbb{R}^{d \times d_k}$ 是可学习的参数矩阵。

### 2. 注意力计算 (Attention Calculation)

得到 Q, K, V 后，我们通过以下步骤计算输出：

1. **相似度 (Similarity)**: 计算 $q \cdot k^T$。点积越大，相关性越强。
2. **归一化 (Normalization)**: 除以 $\sqrt{d_k}$ (防止数值过大梯度消失) 并应用 **Softmax**，得到概率分布（Attention Score）。
3. **加权求和 (Weighted Sum)**: 用 Score 对 $v$ 进行加权求和。

单次计算（单头）的输出维度为 $d_v$ (通常等于 $d_k=128$)，远小于原始维度 $d$。

![Attention Process](https://blog-1316756713.cos.ap-shanghai.myqcloud.com/bolg/20251219005617.webp)

### 3. 矩阵形式与多头 (Matrix Form & Multi-Head)

为了并行计算，我们将所有 Token 堆叠成矩阵 $Q, K, V$，并引入 **Mask ($M$)** 来处理因果关系（如 Decoder 中防止看到未来 Token）：

$$
\text{Head}_i = \text{Softmax}\left(\frac{Q K^T + M}{\sqrt{d_k}}\right)V
$$

在 **Multi-Head Attention** 中，我们并行计算多个 Head（例如 deepseek r1 中的128个），捕捉不同的特征子空间。
最后，将所有 Head 的输出**拼接 (Concat)**，并通过输出矩阵 $W^O$ 融合，恢复到原始维度 $d$：

$$
\text{Output} = \text{Concat}(\text{Head}_1, \dots, \text{Head}_h) \cdot W^O
$$

其中 $W^O$ 用于将多头拼接后的向量映射回模型维度 $d$。

### 4. Code

## KV Caching

1. 为啥可以存储
2. 为啥query不需要存储？
因为之前的query被遮蔽了

## GQA (Grouped-Query Attention)

（待补充：解释 Llama 2/3 中使用的分组查询注意力，如何平衡 MHA 和 MQA 的效果与速度）

## MLA (Multi-Head Latent Attention)

（待补充：DeepSeek 提出的多头潜在注意力，通过低秩压缩大幅减少 KV Cache 显存占用）

## DSA (DeepSeek Attention)

（待补充：具体的 DeepSeek Attention 变种或特定优化）

计算成本大幅降低，使得长上下文推理成为可能。

## 面试问题

### 1. 为啥除以 $\sqrt{d_k}$

### 2. LN 和 BN 的位置？

## 参考

1. Video Source

<iframe width="100%" height="468" src="https://www.youtube.com/embed/Y-o545eYjXM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

2. Attention is all your need

3. KV cache

<iframe width="100%" height="468" src="https://www.youtube.com/embed/sNv5jpAwkcU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
