---
title: "Cosine Similarity Conflates Clinically Distinct Cancer Variants: A Case for Typed-Graph Retrieval in Precision Oncology Decision Support"
title_zh: 余弦相似度混淆临床不同的癌症变异：精准肿瘤学决策支持中的类型化图谱检索案例
authors: "Khan, U. A."
date: 2026-05-17
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.05.723102v2.full.pdf"
tags: ["query:pwt"]
score: 8.0
evidence: 类型化图检索用于RAG，提升检索准确性
tldr: "RAG系统在肿瘤精准医学中常用余弦相似度检索变异，但发现其将临床不同的癌症变异混淆。评估9对具有差异FDA治疗推荐的变异，使用多种嵌入模型和文本格式，结果表明生物医学预训练编码器（PubMedBERT、MedCPT）在中等格式下100%混淆，通用编码器混淆11%。模板匹配阴性对照证实混淆非模板伪影，余弦阈值无法分离。基于类型图的检索或严格变异ID护栏可消除错误检索。"
source: biorxiv
selection_source: fresh_fetch
motivation: 余弦相似度检索混淆临床不同的癌症变异，影响治疗决策支持准确性。
method: 评估9对癌症变异在多种嵌入模型和文本格式下的余弦相似度，并对比类型图检索。
result: "生物医学编码器100%混淆临床不同变异，通用编码器11%；类型图检索错误率为0%。"
conclusion: 建议变异级临床决策支持默认使用类型图检索或带严格变异ID护栏的向量检索。
---

## 摘要
检索增强生成（RAG）越来越多地应用于肿瘤学临床决策支持，其中治疗选择依赖于从NGS报告中识别患者特定的体细胞变异，并将其与证据分级治疗选项匹配。支撑大多数RAG系统的向量检索使用文本嵌入上的余弦相似度，这是一种针对语言接近性而非实体级身份优化的架构。我们假设基于余弦相似度的检索以临床相关率混淆临床不同的癌症变异，而类型化图谱方法（其中每个变异是一个离散节点）通过构造保留了变异级身份。

我们评估了9对具有差异化FDA批准治疗适应症的癌症变异对，变异身份基于CIViC临床变异证据数据库和主要临床文献。这些对涵盖BRAF、EGFR、KRAS、ERBB2、PIK3CA和NTRK1，包括经典的EGFR L858R vs T790M敏感性与耐药性对，以及KRAS G12C vs G12D（只有G12C有FDA批准的靶向治疗）。我们计算了三个开源嵌入模型（PubMedBERT、MedCPT、BGE-large-en-v1.5）和三种文本格式下的成对余弦相似度，并在本次修订中添加了模板匹配的阴性对照、正式分离度量、变异特异性长文本格式、语料库级排序检索、精确ID防护基线以及端到端类型化图谱流水线。

在中格式（基因+变异+肿瘤类型）下，两个生物医学编码器（PubMedBERT、MedCPT）下100%的临床不同变异对（9/9）余弦相似度≥0.95（精确二项95% CI [66.4%, 100%]）；通用编码器（BGE-large-en-v1.5）混淆了11%。生物医学预训练编码器表现比通用编码器更差，而非更好。模板匹配但生物学无关的阴性对照得分低于临床不同对，证实高相似度是真正的混淆而非模板伪影，并且等价表示的正例无法通过余弦阈值与临床不同对区分（中格式ROC-AUC ≤ 0.54，生物医学编码器低于0.5）。在52篇文档的语料库级排序检索中，生物医学编码器下有75%至100%的查询中错误的配对变异出现在前5名。在余弦检索中添加精确变异ID防护，并通过端到端类型化图谱流水线路由检索，两者均将错误变异检索降至零。我们认为，在能够将变异字符串规范化为规范节点的归一化层条件下，类型化图谱检索，或带有严格变异ID防护的向量检索，应成为变异级临床决策支持的默认基础。我们通过同一个九对基准对类型化图谱基线进行了端到端经验验证，展示了95.8%的归一化准确率和0%的错误变异检索率。

## Abstract
Retrieval-augmented generation (RAG) is increasingly applied to clinical decision support in oncology, where treatment selection depends on identifying a patients specific somatic variant from an NGS report and matching it to evidence-graded therapy options. The vector retrieval that underlies most RAG systems uses cosine similarity over text embeddings, an architecture optimized for linguistic proximity rather than entity-level identity. We hypothesize that cosine-similarity-based retrieval conflates clinically distinct cancer variants at clinically relevant rates, while a typed-graph approach in which each variant is a discrete node preserves variant-level identity by construction.

We evaluated 9 cancer variant pairs with differential FDA-approved therapy indications, variant identity informed by the CIViC clinical variant evidence database and primary clinical literature. The pairs span BRAF, EGFR, KRAS, ERBB2, PIK3CA, and NTRK1, including the canonical EGFR L858R vs T790M sensitivity-versus-resistance pair and KRAS G12C vs G12D (only G12C has an FDA-approved targeted therapy). We computed pairwise cosine similarity across three open-source embedding models (PubMedBERT, MedCPT, BGE-large-en-v1.5) and three text formats, and in this revision added template-matched negative controls, formal separation metrics, variant-specific long-format text, corpus-level ranked retrieval, an exact-ID guardrail baseline, and an end-to-end typed-graph pipeline.

Across the medium format (gene + variant + tumor type), 100% of clinically distinct variant pairs (9/9) had cosine similarity [&ge;] 0.95 under both biomedical encoders (PubMedBERT, MedCPT; exact binomial 95% CI [66.4%, 100%]); the general-purpose encoder (BGE-large-en-v1.5) conflated 11%. The biomedically pre-trained encoders performed worse, not better, than the general-purpose encoder. Template-matched but biologically unrelated negative controls scored lower than the clinically distinct pairs, confirming the high similarities are genuine conflation and not a template artifact, and equivalent-notation positives were not separable from clinically distinct pairs by a cosine threshold (medium-format ROC-AUC [&le;] 0.54, below 0.5 for the biomedical encoders). In corpus-level ranked retrieval over a 52-document corpus, the wrong paired variant appeared in the top 5 for 75% to 100% of queries under the biomedical encoders. Adding an exact variant-ID guardrail to cosine retrieval, and routing retrieval through an end-to-end typed-graph pipeline, both reduced wrong-variant retrieval to zero. We argue that, conditional on a normalization layer that resolves variant strings to canonical nodes, typed-graph retrieval, or vector retrieval coupled with strict variant-ID guardrails, should be the default substrate for variant-level clinical decision support. We empirically validate the typed-graph baseline end-to-end on the same nine-pair benchmark, demonstrating 95.8% normalization accuracy and a 0% wrong-variant retrieval rate.