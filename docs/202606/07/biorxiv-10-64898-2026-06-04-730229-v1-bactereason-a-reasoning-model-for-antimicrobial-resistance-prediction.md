---
title: "BacteReason: A Reasoning Model for Antimicrobial Resistance Prediction"
title_zh: BacteReason：一种用于抗菌素耐药性预测的推理模型
authors: "Oikawa, Y., Kawashima, S., Kinjo, A. R., Demizu, Y., Tamura, R., Tsuda, K."
date: 2026-06-07
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.04.730229v1.full.pdf"
tags: ["query:pwt"]
score: 6.0
evidence: 使用知识图推理抗生素耐药性
tldr: "抗菌素耐药性快速全球蔓延，现有机器学习预测模型缺乏机制解释，难以获得临床信任。本文提出BacteReason，一个推理大语言模型，通过微调开源LLM并引入教师模型从生物医学知识图谱生成分子机制理由，预测细菌对抗生素的敏感性。在泛化基准上，相比未调优基线准确率提升43%，相比无理由微调提升38%。该工作证明推理监督能显著提高预测的可解释性和准确性。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有机器学习AMR预测缺乏机制依据，导致临床可信度低。
method: 微调开源LLM，使用教师模型基于知识图谱生成分子机理理由，作为训练数据。
result: "在泛化基准上相对提升43%，较无理由微调提升38%。"
conclusion: 推理监督可有效提升AMR预测的准确性与可解释性。
---

## 摘要
抗菌素耐药性（AMR）在全球范围内的快速传播给临床决策带来了前所未有的压力。现有机器学习预测抗生素敏感性的方法，但由于缺乏机制基础，其可信度有限。我们提出了BacteReason，一个推理型大语言模型（LLM），能够预测细菌对目标抗生素的敏感性，并提供机制性解释。BacteReason通过在临床敏感性数据上微调一个开源权重LLM获得，这些数据附带了解释分子机制的原理说明。这些原理说明由专有教师LLM生成，该教师被提示解释已知的敏感性结果。教师通过TogoMCP与一系列生物医学知识图谱数据库连接，使每个推理步骤都基于检索到的证据。在外推基准测试中，BacteReason相对于未调优基线实现了43%的相对改进，相对于未使用原理说明微调的相同基础LLM实现了38%的相对改进，表明推理监督提高了预测准确性。

## Abstract
The rapid global spread of antimicrobial resistance (AMR) has placed unprecedented pressure on clinical decision-making. Machine learning predictors of antibiotic susceptibility exist, but their lack of mechanistic grounding limits credibility. We present BacteReason, a reasoning large language model (LLM) that predicts bacterial susceptibility to a target antibiotic, together with a mechanistic rationale. BacteReason is obtained by fine-tuning an open-weight LLM on clinical susceptibility data augmented with rationales that explain the molecular mechanisms. These rationales are produced by a proprietary teacher LLM prompted to explain known susceptibility outcomes. The teacher is interfaced via TogoMCP with a collection of biomedical knowledge-graph databases, grounding each reasoning step in retrieved evidence. On an extrapolation benchmark, BacteReason achieves a relative improvement of 43% over the untuned baseline and 38% over the same base LLM fine-tuned without rationales, demonstrating that reasoning supervision improves prediction accuracy.