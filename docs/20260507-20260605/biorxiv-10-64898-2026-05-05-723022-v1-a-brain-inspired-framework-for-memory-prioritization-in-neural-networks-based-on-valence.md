---
title: A brain-inspired framework for memory prioritization in neural networks based on valence
title_zh: 基于效价的神经网络记忆优先级脑启发框架
authors: "Zbaranska, S., Rajeev, A., Josselyn, S., Laschowski, B."
date: 2026-05-08
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.05.723022v1.full.pdf"
tags: ["query:pwt"]
score: 8.0
evidence: 脑启发记忆优先化框架利用效价，将记忆集成到注意力机制，与记忆增强神经网络推理相关
tldr: 人工神经网络长期记忆能力不足。受生物情感效价启发，本文提出一种记忆优先级框架，包含效价加权交叉熵损失、杏仁核模块学习高维效价嵌入、海马体模块整合效价到注意力机制。在空间、情景、语言记忆任务上，该方法一致提升高显著性信息的长期保留，并缓解语言模型中的“中间丢失”问题。工作证明脑启发算法有潜力推动机器学习。
source: biorxiv
selection_source: fresh_fetch
motivation: 为提升人工神经网络长期记忆，受情感效价对生物记忆优先级调控的启发。
method: 提出杏仁核-海马体启发框架：效价加权损失调控学习，效价嵌入通过注意力机制调制信息检索。
result: 在空间、情景和语言记忆任务上，高显著性信息保留率显著提升，语言模型“中间丢失”问题缓解。
conclusion: 脑启发算法通过效价优先级可有效改善神经网络长期记忆，拓展了机器学习方法。
---

## 摘要
改进人工神经网络中的长期记忆仍然是一个开放的挑战。为此，我们开发了一个新颖的基于效价情感原则的记忆优先级脑启发框架。我们的框架包括：(i) 效价加权交叉熵损失，通过效价幅度缩放学习信号，类似于神经调节；(ii) 一个杏仁核启发模块，学习高维效价嵌入；(iii) 一个海马体启发模块，将效价嵌入整合到注意力机制中以调节信息检索。我们展示了该框架在空间、情景和基于语言记忆任务中的泛化能力，持续改善了高显著性信息的记忆优先级和长期保留。除了改进长期记忆，我们还表明该框架有助于缓解语言建模中的“中间迷失”问题。更广泛地说，这项研究进一步证明了脑启发算法推动机器学习领域的潜力。

## Abstract
Improving long-term memory in artificial neural networks remains an open challenge. To address this, we developed a novel brain-inspired framework for memory prioritization based on the principle of emotional valence. Our framework includes: (i) a valence-weighted cross-entropy loss that scales the learning signal by the valence magnitude, analogous to neuromodulation; (ii) an amygdala-inspired module that learns high-dimensional valence embeddings; and (iii) a hippocampus-inspired module that integrates valence embeddings into the attention mechanism to modulate information retrieval. We demonstrated the generalization of our framework across spatial, episodic, and language-based memory tasks, consistently improving memory prioritization and long-term retention of high-salience information. In addition to improving long-term memory, we also showed that our framework can help mitigate the "lost-in-the-middle" problem in language modeling. More generally, this research provides further evidence of the potential of brain-inspired algorithms to advance the field of machine learning.