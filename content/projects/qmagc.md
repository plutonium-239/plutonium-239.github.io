---
title: Q-MAGC
description: Modularity aided consistent attributed graph clustering via coarsening
date: 2024-04-05
tags: ["graphs", "clustering", "optimization", "unsupervised learning", "representation learning"]
cover:
  image: Q-arch_new.jpg
  caption: Overview
  relative: true
---

<!-- {{< icon name="github" text="plutonium-239/memsave_torch" url="https://github.com/plutonium-239/memsave_torch" >}} -->
<!-- {{< icon name="openreview" text="Paper (WANT@ICML’24)" url="https://openreview.net/pdf?id=KsUUzxUK7N" >}} -->
{{< icon name="arxiv" text="arXiv:2407.07128 (TMLR)" url="https://arxiv.org/abs/2407.07128" >}}
{{< icon name="link" text="Paper (OPT-ML@NeurIPS'24)" align="center" url="https://drive.google.com/file/d/1v9hD_VF63LcK6tx7jQKgQxiVbRiewZjD/view?usp=drive_link" >}}


Graph clustering is an important unsupervised learning technique for partitioning graphs with attributes and detecting communities. However, current methods struggle to accurately capture true community structures and intra-cluster relations, be computationally efficient, and identify smaller communities. 

We address these challenges by integrating coarsening and modularity maximization, effectively leveraging both adjacency and node features to enhance clustering accuracy. We propose a loss function incorporating log-determinant, smoothness, and modularity components using a block majorization-minimization technique, resulting in superior clustering outcomes.

The method is theoretically consistent under the Degree-Corrected Stochastic Block Model (DC-SBM), ensuring asymptotic error-free performance and complete label recovery. Our provably convergent and time-efficient algorithm seamlessly integrates with graph neural networks (GNNs) and variational graph autoencoders (VGAEs) to learn enhanced node features and deliver exceptional clustering performance. Extensive experiments on benchmark datasets demonstrate its superiority over existing state-of-the-art methods for both attributed and non-attributed graphs.