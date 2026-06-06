---
title: "HyperNiche: Learning Heterophilic Cellular Niches with Hypergraph Neural Networks"
title_zh: "HyperNiche: 使用超图神经网络学习异嗜性细胞生态位"
authors: "Mahmud, M. I., Banerjee, T."
date: 2026-06-03
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.30.728986v1.full.pdf"
tags: ["query:power-ticket"]
score: 7.0
evidence: 超图结构学习
tldr: 空间转录组数据中的细胞微环境建模常依赖成对相似性，导致同质簇而忽略异质性。为此提出HyperNiche，利用超图神经网络通过兼容性驱动机制学习anchor中心超边，同时捕获同质与异质细胞关系。在乳腺癌和肺癌Xenium数据集上，其聚类性能（ARI、NMI）和生物学可解释性显著优于基线模型，且生成的超边内部特征多样性更高，证明高阶关系建模能有效发现异质细胞微环境，为理解复杂组织结构和肿瘤微环境提供了新视角。
source: biorxiv
selection_source: fresh_fetch
motivation: 传统图方法基于成对相似性产生同质簇，难以捕获空间转录组中细胞类型的异质性微环境。
method: 提出HyperNiche，通过兼容性驱动机制构建anchor中心超边，解耦节点角色为锚点和成员，并整合空间几何信息。
result: 在乳腺癌和肺癌Xenium数据上，ARI和NMI指标超越基线，超边内特征多样性显著提升，表明更好捕获异质关系。
conclusion: 高阶超图建模有效识别异质细胞微环境，增强对肿瘤组织和空间生物学的理解。
---

## 摘要
我们提出HyperNiche，一个基于超图的框架，用于从空间转录组数据中建模高阶、异质的细胞生态位。与依赖成对相似性并倾向于产生同质聚类的传统图方法不同，HyperNiche通过兼容性驱动机制学习以锚点为中心的超边，同时捕捉细胞间的同嗜性和异嗜性关系。通过将节点角色解耦为锚点和成员表示，并将空间几何整合到超边构建中，该模型能够发现跨越不同细胞类型的多细胞生态位。我们在乳腺癌和肺癌组织微阵列的高多重Xenium空间转录组数据集上评估了HyperNiche，证明其在聚类性能（ARI、NMI）和生物学可解释性方面优于最先进的基于图的基线方法。进一步分析表明，与基于相似性的模型相比，HyperNiche产生的超边具有显著更高的边内特征多样性，表明其捕捉异质细胞生态位的能力增强。这些结果凸显了高阶关系建模对于理解复杂空间组织结构和肿瘤微环境的重要性。

## Abstract
We propose HyperNiche, a hypergraph-based framework for modeling higher-order, heterogeneous cellular niches from spatial transcriptomics data. Unlike conventional graph-based methods that rely on pairwise similarity and tend to produce homogeneous clusters, HyperNiche learns anchor-centered hyperedges through a compatibility-driven mechanism that captures both homophilic and heterophilic relationships among cells. By decoupling node roles into anchor and member representations and integrating spatial geometry into hyperedge construction, the model enables the discovery of multicellular niches that span diverse cell types. We evaluate HyperNiche on high-plex Xenium spatial transcriptomics datasets from breast and lung cancer tissue microarrays, demonstrating improvements over state-of-the-art graph-based baselines in clustering performance (ARI, NMI) and biological interpretability. Further analysis shows that HyperNiche produces hyperedges with significantly higher intra-edge feature diversity, indicating an enhanced ability to capture heterogeneous cellular niches compared to similarity-based models. These results highlight the importance of higher-order relational modeling for understanding complex spatial tissue organization and tumor microenvironments.