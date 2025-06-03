
---
title: "第二章：自动求导 (Autograd)"
linkTitle: "2. 自动求导"
weight: 20 # 在 "PyTorch 教程" 这个子菜单中，这是第二项
parent: "PyTorch 教程"
description: "探索 PyTorch 强大的自动求导机制，它是神经网络训练的核心。"
---

## 2.1 Autograd 简介

PyTorch 的 `autograd` 包提供了对张量所有操作的自动微分。这是一个逐个运行的框架，意味着你的反向传播是根据你的代码如何运行来定义的，因此每次迭代都可以不同。

要让 PyTorch 跟踪一个张量的计算历史并计算梯度，你需要将该张量的 `requires_grad` 属性设置为 `True`。

## 2.2 梯度计算示例

```python
import torch

# 创建一个张量并设置 requires_grad=True 来跟踪计算
x = torch.ones(2, 2, requires_grad=True)
print(x)

# 对张量进行操作
y = x + 2
print(y)

# y 是作为操作的结果创建的，所以它也有 grad_fn
print(y.grad_fn)

z = y * y * 3
out = z.mean()
print(z, out)

# 计算梯度
# out 是一个标量，所以 out.backward() 等同于 out.backward(torch.tensor(1.))
out.backward()

# 打印梯度 d(out)/dx
print(x.grad)
```
在上面的例子中，`x.grad` 将会是关于 `x` 的梯度。

## 2.3 停止跟踪梯度

有时我们不希望某些操作被跟踪，例如在模型评估阶段，或者在更新模型参数时（因为这是手动操作，不应影响梯度计算）。

可以使用 `torch.no_grad()` 上下文管理器：

```python
print(x.requires_grad) # x 仍然是 requires_grad=True
print((x ** 2).requires_grad) # 这个新张量也是 requires_grad=True

with torch.no_grad():
    print((x ** 2).requires_grad) # 输出 False
```
或者使用张量的 `.detach()` 方法获取一个新的、不参与梯度计算的张量：
```python
y_detached = x.detach()
print(y_detached.requires_grad) # 输出 False
print(x.eq(y_detached).all())   # y_detached 和 x 的值相同
```

## 总结

`autograd` 是 PyTorch 中非常强大的功能，它使得定义和训练复杂的神经网络变得简单。理解其工作原理对于调试和优化模型至关重要。下一章我们将学习如何使用 `nn` 模块构建神经网络。
