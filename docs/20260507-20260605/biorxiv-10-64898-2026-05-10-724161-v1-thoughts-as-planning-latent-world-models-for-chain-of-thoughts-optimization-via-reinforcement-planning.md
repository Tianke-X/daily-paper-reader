---
title: "Thoughts-as-Planning: Latent World Models for Chain-of-Thoughts Optimization via Reinforcement Planning"
title_zh: 思想即规划：通过强化规划进行思维链优化的潜在世界模型
authors: "Liu, D., Yu, Y., Wu, Y. N."
date: 2026-05-15
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.10.724161v1.full.pdf"
tags: ["query:pwt"]
score: 8.0
evidence: 思维链推理的替代方法用于冷启动
tldr: 大型语言模型在多种任务中的成功凸显了推理链优化的重要性，但现有方法依赖黑箱启发式或梯度-free搜索，缺乏可解释性和泛化性。本文提出Thoughts-as-Planning框架，将推理链优化形式化为潜在语义空间上的序贯决策过程，通过学习潜在世界模型模拟推理链编辑对下游输出的影响。该方法支持多尺度抽象（token、segment、指令级别），利用梯度下降或强化学习规划，在语言理解和生成任务上优于现有基线，同时提供结构化规划轨迹增强可解释性。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有推理链优化方法依赖黑箱启发式或梯度-free搜索，缺乏可解释性、泛化性和样本效率，亟需更高效的序贯决策框架。
method: 将LLM建模为部分可观测环境，学习潜在世界模型模拟推理链编辑效果，通过邻近性嵌入空间编码动态，利用强化学习或梯度下降进行规划。
result: 在语言理解和生成任务上，该方法在效率、鲁棒性和泛化性上超越现有基线，并保持可解释性。
conclusion: Thoughts-as-Planning为推理链优化提供了可解释、高效的序贯决策范式，支持多尺度编辑，具有广泛适用性。
---

## 摘要
大语言模型（LLMs）在多种自然语言处理任务中的成功，使得推理链优化成为将模型行为与任务目标对齐的关键步骤。现有的推理链调优方法通常依赖于黑盒启发式或无需梯度的搜索，缺乏可解释性、泛化能力和样本效率。在这项工作中，我们提出了思想即规划（Thoughts-as-Planning），这是一个新颖的框架，将推理链优化形式化为在潜在语义空间中的序贯决策过程。我们将LLM建模为部分可观测环境，并学习一个模拟推理链编辑对下游输出影响的潜在世界模型。我们构建了一个保持邻近性的嵌入空间，用于编码推理链-响应动态，从而通过梯度下降或强化学习实现规划。我们的方法支持多尺度抽象，允许在词元、片段和指令级别进行推理链编辑，并将其整合到统一规划器中。通过在语言理解和生成任务上的大量实验，我们证明了思想即规划在效率、鲁棒性和泛化性方面优于最先进的推理链调优基线，同时通过其结构化的规划轨迹提供了可解释性。我们的代码可在 https://github.com/FastLM/Thoughts-as-Planning 获取。

## Abstract
The success of large language models (LLMs) across diverse NLP tasks has elevated the importance of reasoning chain optimization as a critical step in aligning model behavior with task objectives. Existing reasoning chain tuning methods often rely on black-box heuristics or gradient-free search, which lack interpretability, generalization, and sample efficiency. In this work, we introduce Thoughts-as-Planning, a novel framework that formalizes reasoning chain optimization as a sequential decision-making process over a latent semantic space. We model the LLM as a partially observable environment and learn a latent world model that simulates the effect of reasoning chain edits on downstream outputs. A proximity-preserving embedding space is constructed to encode reasoning chain-response dynamics, enabling planning via gradient descent or reinforcement learning. Our method supports multi-scale abstraction, allowing reasoning chain edits at token, segment, and instruction levels to be integrated into a unified planner. Through extensive experiments on language understanding and generation tasks, we demonstrate that Thoughts-as-Planning outperforms state-of-the-art reasoning chain tuning baselines in efficiency, robustness, and generalization, while offering interpretability through its structured planning trajectory. Our code is available at https://github.com/FastLM/Thoughts-as-Planning.