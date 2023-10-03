---
theme: purplin
class: slide-main
layout: default
title: '第二周'
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

## Foundations & Trends in Multimodal Machine Learning: Principles, Challenges, and Open Questions 2023
### 多模态机器学习的基础和趋势：概念、挑战

多模式机器学习旨在通过整合包括语言、声学、视觉、触觉和生理信息在内的多种交流模式，设计具有理解、推理和学习等智能能力的计算机代理（computer agents）

多模态机器学习近期被用于：video understanding, embodied autonomous agents, text-to-image generation, multisensor fusion

这篇论文对多模态机器学习的理论和计算基础进行了总览式的叙述，并提出了三个关键的概念:

- Heterogeneity: 不同模态之间的差异和多样性，不同的模态具有不同的类型的数据与特征
- Connections: 建立不同模态之间的联系，包括相关性、依赖性，通过建立连接，可以利用不同模态之间的信息互补性和相互作用
- Interactions: 不同模态之间的相互影响和作用。
- <del>interconnected</del>
<Footer />

---

`modality` 是指感知或表达自然现象的一种方式，例如声音、图片、视频、通过传感器监测到的振动等等。模态分为原始模态（raw modality）和抽象模态（abstract modality），其中原始模态是通过传感器等仪器直接采集到的信息，而抽象模态是对原始模态进行了处理之后的信息（those farther away from sensors），例如从录音中得到的语言情感、从图片抽取出的对象。

每个模态是具有 `Heterogeneity` `Connections` `Interactions`

<Footer />

---
layout: image-y
image: /wee2/1.png
---
<h2>模态是异质的</h2>
<br/>

- 每一个模态是由 Element 组成的
- 每个 Element 也具有不同的分布、结构、信息熵
- 采集过程中难免会产生噪声
- 不同的模型对不同的任务具有不同的相关性

---
layout: image-y
image: /wee2/2.png
---
<h2>连接（Connections）</h2>
<br />
即使模态之间是互质的，但是由于它们之间存在的互补的信息，所以通常不同模态之间也存在着联系


---
layout: image-y
image: /wee2/3.png
---
<h2>交互（Interactions）</h2>
<br />

---

<h2>六大问题</h2>
<br />

- 表示 representation：表示是指将多模态数据转换为计算机可处理的形式或结构化表示。
- 对齐 alignment：建立模态之间的一致性和相互补充性，使得不同模态之间的信息可以相互利用。
- 推理 reasoning：通过从不同模态中提取的信息，模型可以进行推理，推断出关于多模态数据的隐藏关系、属性或结构。
- 生成 generation：生成是指从一个或多个模态生成另一个或多个模态的过程
- 迁移 transference：迁移是指将从一个模态学到的知识、模型或表示应用到另一个模态的过程。
- 量化 quantification：通过量化方法，可以对表示、对齐、推理等关键概念的质量和效果进行评估

<Footer />

---

## Trends in Integration of Vision and Language Research: A Survey of Tasks, Datasets, and Methods 2021
### 关于视觉和语言融合趋势的调查：任务、数据集、方法

这是一篇关于人工智能（AI）特定子领域——视觉和语言整合的综述文章。这篇文章讨论了十个整合语言和视觉的主要任务，包括问题的构造、方法、现有的数据集、评估测量和与现有最先进方法的结果比较。并且此文还提供了该研究领域潜在的未来方向，对视觉和语言研究的最新趋势进行了概述和详细阐述。

- 首先介绍了计算机视觉和NLP的各种任务背景
- 提出了十个突出的任务用于融合视觉和语言模态
- 为了将传统的研究任务与V&L任务联系起来，本文介绍了每个融合任务是如何从它们最初所基于的独立的任务拓展来的
- 对相关数据集、评估措施以及几种最先进方法获得的相对性能进行了综述。
- 介绍了用大规模多模态数据预训练通用模型的各种方法，以支持下游视觉和语言集成任务


<Footer />

---

## Multimodal Machine Learning: A Survey and Taxonomy 2017
### 多模式机器学习：综述与分类
<br />

- 摘要：

这篇文章没有关注特定的多模式应用，而是调查了多模式机器学习本身的最新进展，并在一个通用的分类中介绍了它们。不同于 早期和晚期融合分类，确定了多模式机器学习面临的更广泛挑战，即：representation, translation, alignment, fusion, and co-learning.

- 结论：
 
本文主要介绍多模态学习的分类 representation, translation, fusion, alignment, and co-learning，其中的一些已经被研究了很长时间（例如 fusion），但是现在（2017）产生了许多 representation 和 translation 相关的新算法，因而引起了广泛的关注。

<Footer />


---

## 学习进度
<br />

- 吴恩达：
  - 参数调整的过程
  - 选择超参数的标准
  - 实践中调整超参数（熊猫和鱼子酱）
  - Batch Norm
  - Softmax 回归
  - 深度学习框架
  - Tensorflow
<Footer />

---

<h2>学习进度</h2>
<br />

- 李沐 [动手学深度学习](https://d2l.ai/index.html):
  - Object-Oriented Design for Implementation
  - Synthetic Regression Data
  - Linear Regression Implementation from Scratch
  - Concise Implementation of Linear Regression

<Footer />