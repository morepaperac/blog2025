---
title: 美团-MTGR
published: 2025-12-18
description: MTGR论文阅读笔记
tags: [生成式推荐, 召回]
category: 推荐算法
draft: false
---

# 引言

## Scaling law

随着模型大小、数据集大小和用于训练的计算浮点数的增加，模型的性能会提高。并且为了获得最佳性能，所有三个因素必须同时放大。当不受其他两个因素的制约时，模型性能与每个单独的因素都有幂律关系。

## 目的

在推荐系统中，最近的工作采用了生成式推荐来实现可扩展性，但它们的生成方法需要放弃传统推荐模型精心构建的交叉特征。
我们提出MTGR（美团生成建议）来解决这个问题。 MTGR是基于HSTU[23]架构进行建模，可以保留原始深度学习推荐模型（DLRM）特征，包括交叉特征

# 参考文献

1. MTGR论文：<https://arxiv.org/pdf/2505.18654>
2. MTGR技术报告：<https://tech.meituan.com/2025/05/19/meituan-generative-recommendation.html>
3. Zhai J, Liao L, Liu X, et al. Actions speak louder than words: Trillion-parameter sequential transducers for generative recommendations[J]. arXiv preprint arXiv:2402.17152, 2024
