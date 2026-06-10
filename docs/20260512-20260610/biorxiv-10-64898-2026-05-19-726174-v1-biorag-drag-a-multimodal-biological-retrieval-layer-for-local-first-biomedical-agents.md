---
title: "BioRAG-DRAG: A Multimodal Biological Retrieval Layer for Local-First Biomedical Agents"
title_zh: BioRAG-DRAG：面向本地优先生物医学代理的多模态生物检索层
authors: "Wang, L."
date: 2026-05-21
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.19.726174v1.full.pdf"
tags: ["query:power-ticket"]
score: 8.0
evidence: 检索增强生成中的图证据打包
tldr: 针对生物医学智能体需要从文献、序列、通路等多源异构证据中检索的难题，提出BioRAG-DRAG，一种本地优先的多模态生物检索层。它集成了可插拔的神经向量检索（如ESM-2、OmniGene CPT）、BLAST序列比对验证以及DRAG图状证据路径，构建了含25.8万条记录的分区语料库BioRAG-Standard v0。实验表明：BLAST在序列匹配上接近饱和，向量检索在蛋白质上表现中等，DNA/cDNA检索较弱。结论支持有界架构——向量检索提供统一候选上下文，BLAST和DRAG保证生物验证与证据归因。
source: biorxiv
selection_source: fresh_fetch
motivation: 生物医学智能体需要统一的接口获取文献、序列、通路等异构证据，现有工具缺乏整合。
method: 提出多模态检索层，结合神经向量检索、BLAST验证和DRAG图路径，支持可插拔编码器。
result: BLAST在序列匹配上接近饱和；蛋白质编码器优于OmniGene嵌入；DNA/cDNA向量检索较弱。
conclusion: 有界架构中，向量检索提供统一候选，BLAST和DRAG确保验证与归因，支持模型无关设计。
---

## 摘要
生物医学代理需要可靠地访问异质性证据：文献文本、基因和通路记录、蛋白质序列、DNA/cDNA序列以及结构化的生物学关系。经典的序列工具（如BLAST）仍然是基于比对验证的正确选择，但它们并非大语言模型代理的统一上下文接口。我们提出BioRAG-DRAG，这是一种本地优先的多模态检索层，结合了可插拔的神经序列-文本检索、BLAST验证和基于图的证据打包。专门的编码器（如ESM-2）可用于蛋白质分区，而OmniGene CPT为混合序列/文本和面向代理的使用提供了统一的生物语言骨干；BLAST对序列候选进行重排序或验证；DRAG图为下游代理展示了带类型、可追溯的路径。

我们引入BioRAG-Standard v0，这是一个分区语料库/库，包含257,886条可检索记录，以及基于Open-Rosalin标准生物医学记录和序列窗口扩展构建的初始注释层，用于工程评估。在索引内序列窗口压力测试中，BLAST几乎饱和了生物学匹配，而向量检索恢复了显著但较低的生物学匹配率。在留出父片段控制上，公共蛋白质编码器优于当前OmniGene蛋白质窗口嵌入，而DNA/cDNA密集检索即使使用现成的Nucleotide Transformer池化仍然较弱；这支持了一种模型无关的BioRAG设计，而非主张一个统一生成器骨干是最佳序列搜索编码器。在标准文本和10万序列窗口集合上的索引Chroma查找在查询嵌入后仅增加了少量查找开销；这并未衡量端到端的即时延迟。最后，探索性序列DRAG轨迹显示了可检查的生物学邻域，包括免疫球蛋白家族和基因符号模块，初始图控制表明结构非随机且部分由序列相似性驱动。这些结果支持了一种有界的架构：向量检索提供统一候选上下文，而BLAST和DRAG提供生物学验证和证据归因。

## Abstract
Biomedical agents need reliable access to heterogeneous evidence: literature text, gene and pathway records, protein sequences, DNA/cDNA sequences, and structured biological relations. Classical sequence tools such as BLAST remain the right choice for alignment-grounded verification, but they are not a unified context interface for large language model agents. We present BioRAG-DRAG, a local-first multimodal retrieval layer that combines pluggable neural sequence-text retrieval, BLAST verification, and graph-based evidence packaging. Specialized encoders such as ESM-2 can serve protein partitions, while OmniGene CPT provides a unified biological-language backbone for mixed sequence/text and agent-facing use; BLAST reranks or verifies sequence candidates; and DRAG graphs expose typed, traceable paths for downstream agents.

We introduce BioRAG-Standard v0, a partitioned corpus/library with 257,886 retrievable records and an initial annotation layer for engineering evaluation built from Open-Rosalind Standard biomedical records and sequence-window extensions. On an in-index sequence-window stress test, BLAST nearly saturates biological matching, while vector retrieval recovers substantial but lower biological match rates. On held-out parent-fragment controls, public protein encoders outperform the current OmniGene protein-window embedding, while DNA/cDNA dense retrieval remains weak even with off-the-shelf Nucleotide Transformer pooling; this supports a model-agnostic BioRAG design rather than a claim that one unified generator backbone is the best sequence-search encoder. Indexed Chroma lookup over Standard text and 100k sequence-window collections adds only small lookup overhead after query embedding; this does not measure end-to-end instant latency. Finally, exploratory sequence DRAG traces show inspectable biological neighborhoods, including immunoglobulin-family and gene-symbol modules, with initial graph controls indicating non-random but partly sequence-similarity-driven structure. These results support a bounded architecture: vector retrieval supplies unified candidate context, while BLAST and DRAG provide biological verification and evidence attribution.