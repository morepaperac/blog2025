---
title: Google-TIGER
published: '2025-12-21'
description: 2023年11月，Google DeepMind 提出了TIGER算法
tags:
  - 生成式推荐
  - 召回
category: 推荐算法
draft: false
---

## TIGER 结构

Google DeepMind 提出了一种新颖的生成式检索方法：**TIGER** (Transformer Index for GEnerative Recommenders)。

为此，TIGER 创建了**语义上有意义的码字元组**（semantically meaningful tuple of codewords），作为每个物品（Item）的**语义 ID (Semantic ID)**。

给定用户会话中物品的语义 ID，训练一个基于 Transformer 的 **Seq2Seq** 模型来预测用户将与之交互的下一个物品的语义 ID。

## 语义 ID (SID)

### 优点

将物品表示为语义 Token 序列具有诸多优势：

1. **知识共享**：在语义上有意义的数据上训练 Transformer 记忆，允许在相似物品之间共享知识。
2. **摒弃随机 ID**：这使我们能够摒弃以前在推荐模型中用作物品特征的原子且随机的物品 ID [33, 42, 11, 8]。
3. **泛化能力**：通过物品的语义 Token 表示，模型不太容易受到推荐系统中固有的反馈循环 [1, 26, 39] 的影响，从而使模型能够泛化到语料库中新添加的物品。
4. **扩展性**：使用 Token 序列进行物品表示有助于缓解与物品语料库规模相关的挑战；可以使用 Token 表示的物品数量是序列中每个 Token 基数的乘积。
5. **内存效率**：通常，物品语料库的大小可能在数十亿的数量级，为每个物品学习唯一的嵌入可能会占用大量内存。虽然可以采用基于随机哈希的技术 [16] 来减少物品表示空间，但使用语义上有意义的 Token 进行物品表示是一个有吸引力的替代方案。
