---
theme: purplin
class: slide-main
layout: default
title: '第三周'
selectable: true
fonts:
  sans: 'Noto Sans CJK SC'
  serif: 'Noto Serif CJK SC'
  mono: 'Fira Code'
---

# 目录

<Toc minDepth="2" maxDepth="2"></Toc>
<Footer />

---

## ResNet

ResNet是一种卷积神经网络，它的全称是深度残差网络（Deep residual network）。ResNet的提出是CNN图像史上的一件里程碑事件。ResNet的作者何恺明因此摘得CVPR2016最佳论文奖。ResNet的主要特点是解决了深度CNN模型难训练的问题。**ResNet通过残差学习（Residual learning）来解决深层网络中梯度消失和精度下降的问题。**

ResNet在2015年的ILSVRC（ImageNet Large Scale Visual Recognition Challenge）中取得了冠军。自此之后，ResNet被广泛应用于各种计算机视觉任务中，并且也成为了其他神经网络架构的基础。例如：

- ResNeXt
- Wide ResNet
- Residual Attention Network (RANet)
- Residual Dense Network (RDN)
- Residual Network of Residual Networks (RoR)
- Dual Path Network (DPN)
- Multi-Scale Dense Network (MSDNet)

---

## Deep Residual Learning for Image Recognition (2016 IEEE CVPR)
### 基于深度残差学习的图像识别

**摘要**

- 越**深**的神经网络越难以训练, 而网络的深度又很重要（主要问题）
- 本文提出了一种基于残差学习的框架使得很深的网络训练更加容易（解决方案）
- 一些实验结果证明该方法的可行性
  - 比VGA网络深了八倍的152层网络并且仍然具有更低的复杂度
  - 在 ImageNet 的测试集中达到了3.57%的错误率
  - 并且做出了用于分析测试集 CIFAR-10 的100层和**1000**层的网络
  - 在 COCO 对象检测数据集上获得了28%的提升

<Footer />

---

## 为什么我们要追求更深的网络？
<br />

**因为每一层都会对输入数据进行一系列的变换和特征提取，所以通过堆叠更多的层能够获得更丰富的特征。**

除此之外，也有很多证据表明网络的深度具有关键的重要性

- Very deep convolutional networks for large-scale image recognition. In ICLR, 2015.
- Going deeper with convolutions. In CVPR, 2015.
- Delving deep into rectifiers: Surpassing human-level performance on imagenet classification. In ICCV, 2015.

既然网络越深越好，那为什么我们不把许多层简单堆叠在呢？
<Footer />

---
layout: "image-y"
image: "./week3/1.png"
---

## 是否简单的堆叠越多层，网络的效果就越好？

简单堆叠层存在的问题：

- 梯度消失和爆炸的问题，这将会阻碍结果的收敛（解决办法：正则化，Batch Norm）
- 当深度网络开始收敛时会出现衰退问题（degradation problem），即随着深度的增加精度会达到饱和并在之后快速降低，并且这种衰退不是由于过拟合（图中的训练误差和测试误差在添加了层数之后都有升高）

---
layout: "image-y"
image: "./week3/1.png"
---

## 衰退问题的理论解
<br />

假设有两个模型架构，其中一个为浅层模型，而另一个是在该浅层模型的基础上加上更多的模型。这些添加的层对浅层模型已经学习的结果进行恒等映射（identity mapping），因为这种架构的出现，理论上更深的模型应该也能不产生更高的错误率（相对于它所基于的浅层模型），但是实验显示网络并没有达到这一状态，而是产生了衰退。

---
layout: "image-x"
image: "./week3/2.png"
---

## 解决衰退问题（论文的核心）

在这篇文章中，作者通过引入深度残差学习框架来解决衰退问题，假设我们最终要拟合的函数为 $H(x)$ (underlying mapping)，在一个残差块中，我们去拟合 $F(x)$ 其中 $F(x):=H(x)-x$ 最后将这个残差块最后一层的输出 $F(x)$ 加上输入 $x$ （捷径连接/短路机制）即得到我们想要的 $H(x)$，因此在一个残差块内，我们不再去拟合 $H(x)$ 而是去拟合一个残差函数 $F(x)$ (residual mapping)
<br />
如果输入和输出之间的变换很小（接近恒等映射），那么网络可以选择性地将残差推向零，从而逼近恒等映射。这种优化过程相对来说更容易，因为只需要微调残差部分，而不是通过一系列非线性层逐层拟合恒等映射。
<br />
由于这种捷径连接不会带来额外的复杂度，因此网络整体的复杂度也得到了保证

---
layout: image-y
image: "./week3/3.png"
---

## 实验结果
<br />

实验结果显示使用了 ResNet 之后更深的神经网络能够发挥更大的作用，使得错误率进一步降低，并且训练速度也有所提升。

---

## 补充

后来普遍认为，RexNet 所展现出来的优势是它在梯度上保持的比较好。假设 $g(x)$ 为原始的较浅的网络，再加了一些层之后相当于 $h(g(x))$ ，当对其求导时有：

$$
\frac{\partial h(g(x))}{\partial g(x)} \cdot \frac{\partial g(x)}{\partial x}
$$

因此当层数增多时，对应的乘法也就会变多，又由于梯度一般较小（小于1），将导致**梯度消失**

当使用 ResNet 之后，最终的结果将会变为 $f(g(x)) + x$ ，因此求梯度为：

$$
\frac{\partial (f(g(x)) + g(x))}{\partial x} = 
\frac{\partial f(g(x))}{\partial g(x)} \cdot \frac{\partial g(x)}{\partial x} + \frac{\partial g(x)}{\partial x}
$$

因此梯度仍然能保持一个较大的值，使得训练更快（梯度下降）。

<Footer />

---

## 本周学习进度

<br />

- 正交化（调节参数时尽可能使其对结果只产生单一影响）
- 单数评价指标（将多个指标宗合为一个指标考虑）
- 满足和优化指标（某些指标需要优先满足与优化）
- 训练开发测试集的分配
- 人类水平表现（用于衡量模型的性能与结果）
- 超越人类水平表现
- 提高模型性能的方法

