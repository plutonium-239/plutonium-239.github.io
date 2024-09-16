---
title: "`memsave_torch`"
description: "Lowering PyTorch's Memory Consumption for Selective Differentiation"
date: 2024-06-18
tags: ["optimization", "memory efficiency", "fine tuning", "CNNs"]
cover:
  image: memsave_torch_banner.svg
  caption: Logo
  relative: true
accent: "#00e1d2"
---

{{< icon name="github" text="plutonium-239/memsave_torch" url="https://github.com/plutonium-239/memsave_torch" >}}
{{< icon name="openreview" text="Paper (WANT@ICML’24)" url="https://openreview.net/pdf?id=KsUUzxUK7N" >}}
{{< icon name="arxiv" text="arXiv:2404.12406" url="https://arxiv.org/abs/2404.12406" >}}
{{< icon name="poster" text="Poster" align="center" url="https://github.com/plutonium-239/memsave_torch/blob/main/memsave_poster.pdf" >}}

Memory is a limiting resource for many deep learning tasks. Beside the neural network weights, one main memory consumer is the computation graph built up by automatic differentiation (AD) for backpropagation. We observe that PyTorch’s current AD implementation sometimes neglects information about parameter differentiability when storing the computation graph. This information is useful though to reduce memory whenever gradients are requested for a parameter subset, as is the case in many modern fine-tuning tasks. Specifically, inputs to layers that act linearly in their parameters and inputs (fully-connected, convolution, or batch normalization layers in evaluation mode) can be discarded whenever the parameters are marked as non-differentiable. We provide a [drop-in, differentiability-agnostic implementation](https://github.com/plutonium-239/memsave_torch) of such layers and demonstrate its ability to reduce memory without affecting run time on popular convolution- and attention-based architectures.

# Saving Memory in CNNs (with PyTorch)

CNNs are made of mainly Convolution layers along with activations such as ReLU and normalization/pooling layers such as batch normalization and max pooling.

## Motivation

In torch these layers are implemented by `torch.nn.Conv2d`, `torch.nn.ReLU`, `torch.nn.BatchNorm2d`,`torch.nn.MaxPool2d`, and give rise to very fast code that calls native C++ and CUDA kernels at the lowest level. This holds for the forward pass as well as the backward pass. However, sometimes memory efficiency is traded off for better time efficiency by storing a lot of tensors that we *might* need. But this results in consumer-level GPUs to not have enough VRAM for performing these tasks with a decent batch size. Here, we try to make that possible by implementing our own memory saving layers while also not giving up time efficiency. These can be found in the `memsave` module.

==An important use case is when you want to slightly alter a layer==

## Results
Here are summarized results on 4 models (plots from the poster):

### ResNet-101
{{< focusimage name="ResNet-101" src="images/poster_plot_resnet101.svg" >}}
### EfficientNet-v2-L
{{< focusimage name="EfficientNet-v2-L" src="images/poster_plot_efficientnet_v2_l.svg" >}}
### T5
{{< focusimage name="T5" src="images/poster_plot_t5.svg" >}}
### Mistral-7B
{{< focusimage name="Mistral-7B" src="images/poster_plot_mistral-7b.svg" >}}