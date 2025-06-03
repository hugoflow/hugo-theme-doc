---
title: "快速入门：使用 Keras 进行基本分类"
linkTitle: "1. Keras 快速入门"
weight: 10 # 在 "TensorFlow 教程" 这个子菜单中，这是第一项
parent: "TensorFlow 教程"
description: "通过一个简单的图像分类示例，快速了解如何使用 TensorFlow Keras API 构建、训练和评估一个神经网络。"
---

## 1.1 引言

本节将通过一个经典的机器学习问题——对服装图像进行分类（如运动鞋和衬衫），来快速入门 TensorFlow。我们将使用 Keras API。

## 1.2 导入 TensorFlow 和数据集

```python
import tensorflow as tf
from tensorflow import keras
import numpy as np
import matplotlib.pyplot as plt

print(tf.__version__)

# 加载 Fashion MNIST 数据集
fashion_mnist = keras.datasets.fashion_mnist
(train_images, train_labels), (test_images, test_labels) = fashion_mnist.load_data()

# 定义类别名称
class_names = ['T-shirt/top', 'Trouser', 'Pullover', 'Dress', 'Coat',
               'Sandal', 'Shirt', 'Sneaker', 'Bag', 'Ankle boot']
```

## 1.3 数据预处理

在训练网络之前，必须对数据进行预处理。像素值介于 0 到 255 之间，我们需要将其归一化到 0 到 1 的范围。

```python
train_images = train_images / 255.0
test_images = test_images / 255.0
```

## 1.4 构建模型

构建神经网络需要配置模型的层，然后编译模型。

```python
model = keras.Sequential([
    keras.layers.Flatten(input_shape=(28, 28)), # 将图像从 2D (28x28 像素) 数组转换成 1D (28*28=784 像素) 数组
    keras.layers.Dense(128, activation='relu'),   # 128 个节点的全连接层
    keras.layers.Dense(10, activation='softmax') # 输出层，10 个节点对应 10 个类别，softmax 输出概率分布
])
```

## 1.5 编译模型

在准备对模型进行训练之前，还需要一些配置。这些是在模型的编译 (compile) 步骤中添加的：
*   **损失函数 (Loss function)**：衡量模型在训练期间的准确率。
*   **优化器 (Optimizer)**：决定模型如何根据其看到的数据和自身的损失函数进行更新。
*   **指标 (Metrics)**：用于监控训练和测试步骤。以下示例使用了准确率 (accuracy)。

```python
model.compile(optimizer='adam',
              loss='sparse_categorical_crossentropy',
              metrics=['accuracy'])
```

## 1.6 训练模型

训练神经网络模型需要执行以下步骤：
1.  将训练数据馈送给模型。
2.  模型学习将图像和标签关联起来。
3.  要求模型对测试集进行预测。
4.  验证预测结果是否与 `test_labels` 数组中的标签匹配。

```python
model.fit(train_images, train_labels, epochs=10) # 训练 10 个周期
```

## 1.7 评估准确率

比较模型在测试数据集上的表现情况：

```python
test_loss, test_acc = model.evaluate(test_images,  test_labels, verbose=2)
print('\\nTest accuracy:', test_acc)
```

## 总结
本节我们通过一个简单的示例快速了解了如何使用 TensorFlow Keras API 构建和训练一个图像分类模型。在后续的章节中，我们将深入学习更多高级内容。
