---
title: "第一章：PyTorch 基础与张量"
linkTitle: "1. 基础与张量"
weight: 10 # 在 "PyTorch 教程" 这个子菜单中，这是第一项
parent: "PyTorch 教程" # 明确指定父级菜单项
description: "了解 PyTorch 的基本安装和核心数据结构——张量（Tensor）的操作。"
---

## 1.1 什么是 PyTorch?

PyTorch 是一个开源的机器学习框架，由 Facebook 的人工智能研究团队开发。它以其灵活性和动态计算图特性而受到研究人员和开发者的喜爱。

主要特点：
*   **易于使用**: Pythonic 的 API 设计。
*   **动态计算图**: 允许在运行时改变网络结构，非常适合 NLP 等复杂模型。
*   **强大的 GPU 加速**: 无缝支持 NVIDIA CUDA。
*   **丰富的工具和库**: TorchVision, TorchText, TorchAudio 等。

## 1.2 安装 PyTorch

你可以访问 PyTorch 官方网站 ([https://pytorch.org/get-started/locally/](https://pytorch.org/get-started/locally/)) 根据你的操作系统、包管理器（conda 或 pip）、计算平台（CPU 或 CUDA 版本）选择合适的安装命令。

例如，使用 pip 安装 CPU 版本：
```bash
pip install torch torchvision torchaudio
```

## 1.3 张量 (Tensors)

张量是 PyTorch 中的核心数据结构，类似于 NumPy 的 ndarrays，但它可以在 GPU 上运行以加速计算。

### 1.3.1 创建张量

```python
import torch

# 创建一个未初始化的 5x3 矩阵
x = torch.empty(5, 3)
print(x)

# 创建一个随机初始化的 5x3 矩阵
x = torch.rand(5, 3)
print(x)

# 创建一个全零矩阵，类型为 long
x = torch.zeros(5, 3, dtype=torch.long)
print(x)

# 直接从数据创建张量
x = torch.tensor([5.5, 3])
print(x)
```

### 1.3.2 张量操作

PyTorch 支持多种张量操作，包括算术运算、索引、切片等。

```python
# 加法
y = torch.rand(5, 3)
print(x + y)

# 索引
# print(x[0]) # 获取第一行 (注意: 上面的 x 被重新赋值为 torch.tensor([5.5, 3]), 这是一个1D张量)
# 如果 x 是一个多维张量，例如:
x_multi_dim = torch.rand(5,3)
print(x_multi_dim[0]) # 获取第一行

# 改变形状 (Reshape)
x_reshape_source = torch.randn(4, 4)
y_reshaped = x_reshape_source.view(16)
z_reshaped = x_reshape_source.view(-1, 8)  # -1 表示维度由其他维度推断
print(x_reshape_source.size(), y_reshaped.size(), z_reshaped.size())
```

更多关于张量的操作，请查阅官方文档。

## 总结

本章我们介绍了 PyTorch 的基本情况和核心数据结构——张量。熟练掌握张量的创建和操作是学习 PyTorch 的第一步。在下一章，我们将学习 PyTorch 的自动求导机制。
