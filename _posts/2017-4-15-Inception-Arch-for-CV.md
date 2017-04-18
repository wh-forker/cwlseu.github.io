---
layout: post
title: "Rethinking the Inception Architecture for Computer Vision"
categories: [blog ]
tags: [CV论文笔记]
description: Inception是在NIN中提出的一个神经网络模块，后来随着googLeNet中的成功被人们视为深度网络的法宝。
后来人们在原来Inception的基础上进行组件替换和添加实现了Inception的进化。
---

声明：本博客欢迎转发，但请保留原作者信息!

作者: 曹文龙

博客： <https://cwlseu.github.io/>

## 论文
[Inception v4]<https://arxiv.org/abs/1602.07261>
[Inception v3]<https://www.arxiv.org/abs/1512.00567>

## 从Inception中的演变看问题

## 遵循规则

### 避免特征表示瓶颈

Avoid representational bottlenecks, especially early in the network. Feed-forward networks can be represented by an acyclic graph from the input layer(s) to the classifier or regressor. This defines a clear direction
for the information flow. For any cut separating the inputs from the outputs, one can access the amount of information passing though the cut. One should avoid bottlenecks with extreme compression. In general the representation size should gently decrease from the inputs to the outputs before reaching the final representation used for the task at hand. Theoretically, information content can not be assessed merely by the dimensionality of the representation as it discards important factors like correlation structure; the dimensionality merely provides a rough estimate of information content.
![@](../images/inception/9.PNG)

### 高纬度更容易处理局部

Higher dimensional representations are easier to process locally within a network. Increasing the activations per tile in a convolutional network allows for more disentangled features. The resulting networks will train faster.
![@](../images/inception/7.PNG)

### 通过低维嵌入的方式实现空间信息的聚合，能够减少特征表示的损失

Spatial aggregation can be done over lower dimensional embeddings without much or any loss in representational power. For example, before performing a more spread out (e.g. 3 × 3) convolution, one can reduce the dimension of the input representation before the spatial aggregation without expecting serious adverse effects. We hypothesize that the reason for that is the strong correlation between adjacent unit results in much less loss of information during dimension reduction, if the outputs are used in a spatial aggregation context. Given that these signals should be easily compressible, the dimension reduction even promotes faster learning.
![@](../images/inception/5.PNG)
![@](../images/inception/6.PNG)

### 网络的宽度和深度的平衡
Balance the width and depth of the network. Optimal performance of the network can be reached by balancing the number of filters per stage and the depth of the network. Increasing both the width and the depth of the network can contribute to higher quality networks.
However, the optimal improvement for a constant amount of computation can be reached if both are increased in parallel. The computational budget should therefore be distributed in a balanced way between the depth and width of the network.