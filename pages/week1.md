---
theme: purplin
class: slide-main
layout: default
title: '第一周'
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
class: slide-main
---

## 一、论文来源

<br/>

- https://github.com/mli/paper-reading (李沐带你读)

- https://github.com/search?q=Multimodal&type=repositories

---

<h2>一、论文来源</h2>
<h3>李沐提到的一些阅读方法</h3>
<br/>

一篇论文读三遍，在每一遍分别：

1. 读标题，摘要，结论
2. 通读全文，不用追求细节，可以看一下重要的图表
3. 知道论文中的每句话在做什么，包括公式方法

可以在每一步做判断要不要继续往下读。

--- 

<h2>一、论文来源</h2>
<h3>找到的一些有用的仓库</h3>
<br/>

- https://github.com/pliang279/awesome-multimodal-ml ⭐️4.6k
- https://github.com/Eurus-Holmes/Awesome-Multimodal-Research ⭐️1.2k

两个仓库内容类似，对论文进行了收集与分类，包括：

1. Survey Papers
2. Core Areas
3. Architectures
4. Applications and Datasets
5. Tutorials
6. Courses

---

<h2>一、论文来源</h2>
<h3>找到的一些有用的仓库</h3>
<br/>

- https://github.com/maelfabien/Multimodal-Emotion-Recognition (text audio video)
- https://github.com/Demfier/multimodal-speech-emotion-recognition (audio text)
- https://github.com/soujanyaporia/multimodal-sentiment-analysis (videoText videoAudio videoVisual)
- https://github.com/david-yoon/multimodal-speech-emotion (audio text)
- https://github.com/dsaidgovsg/multimodal-learning-hands-on-tutorial (text image location)

<br />

- https://www.cs.cmu.edu/~morency/MMML-Tutorial-ACL2017.pdf
- https://cmu-multicomp-lab.github.io/mmml-tutorial/schedule/

---

## 二、论文阅读

<h3>ImageNet Classification with Deep Convolutional Neural Networks</h3>
<h3>摘要</h3>
<br />

有60百万个参数和650,000个神经元，由五个卷积层构成，其中包括一个**最大池化层**、三个全连接层、一个**1000-way softmax**

**为了使训练更快** 使用了 `non-saturating` 神经元以及非常高效地GPU卷积操作的实现

**为了减少在全连接层中的过度拟合** 引入了最近（2012）刚被开发的 `dropout` 它被证明非常的高效

---

<h2>二、论文阅读</h2>
<h3>主要贡献</h3>
<br />

1. 训练了迄今为止最大的卷积神经网络，并在 `ImageNet` 的竞赛中获得了最好的结果
2. 实现了高度优化的 `GPU` 实现的2D卷积，以及所有的其他操作
3. 使用了一些不寻常的 `features` 使得性能得到了提升
4. 使用了一些高效的技术来预防因数据集过大而造成的过拟合

---
layout: image-x
image: ./images/relu.png
---

<h2>二、论文阅读</h2>
<h3>关键方法</h3>
<br />

1. 使用 `ReLU` 函数，用了之后训练的特别快
2. 同时使用两个GPU（在BERT等大模型出来之后很有用）
3. 对输入进行标准化以防止饱和
4. Stochastic gradient descent
5. “Overlapping Pooling” (Krizhevsky et al., 2012, p. 4)
6. 数据增强（随机从256x256中提取224x224，使用PCA增强RGB通道）
7. Dropout （等价于L2正则项）

---
layout: image-x
image: ./images/demo.png
---

## 三、项目学习
<h3>https://github.com/dsaidgovsg/multimodal-learning-hands-on-tutorial</h3>
<br />

1. 输入是文本、图片、位置
2. 输出是反馈的重要程度
3. 文本分析使用了 BERT
4. 图片分析使用了 ResNet
5. 将两者的分析结果结合使用了 ALBEF 模型
<br />

---

## 四、学习进度

这周学习了怎么调节神经网络的超参数，分别是：

- 初始化 weights 的方法 (随机初始化，注意不能过大)
- 梯度检查的方法 （使用定义法去检验公式法的结果）
- 正则化的方法 （L2正则，dropout）

<Footer />