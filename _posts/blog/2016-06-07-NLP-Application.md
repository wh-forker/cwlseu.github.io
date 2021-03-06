---
layout: post
title: NLP Introduction
categories: [blog ]
tags: [自然语言处理, ]
description: 自然语言处理需要大量语料进行学习，而语料的集合往往被称为语料库。
---


- 声明：本博客欢迎转发，但请保留原作者信息!
- 作者: [曹文龙]
- 博客： <https://cwlseu.github.io/>


# 自然语言应用

@(自然语言处理)[自然语言处理|信息检索]

## 自然语言发展历程

1. 50-60年代，最为人工智能领域的应用主要是机器翻译方面尤其是60年代。普遍采用**基于原则**的方法。
2. 90年代，大规模词典和真是语料库的研制，基于语料库的**统计**自然语言成为重要方法。[因此学习统计分析是是多么重要啊]
3. 过去20年，随着互联网的普及，为自然语言处理领域提供了强有力的应用牵引和海量的语言资源。自然语言处理和信息检索系统结合。统计自然语言受限于训练集的规模，过拟合问题严重，推广能力不足。
4. 近几年，**深度学习**方法，基于分布学习的**词义**和**语义**很好地效果。Web2.0积累了大量的User Generated Content.为自然语言提供了新的资源和技术创新的源泉。基于知识和基于统计的方法融合受到关注。

## 信息抽取

系统并不要求能够对自然语言文本进行深层理解，而是从中抽取有用信息，作为自然语言部分理解的一种形式。在过载的信息中，快速准确获取信息的技术手段。

##定义

1997：从自然语言文本中抽取指定类型的***实体***、***文本***、***关系***和***事件***等事实信息。

## 评测标准

1. MUC （message understanding conferences）
    实体识别，共指消解，模板关系抽取等
2. ACE  automatic content extraction
    2009年变名为TAC ( Text analysis conference )
    关系抽取，事件抽取
3. TAC-KBP ( Knowledge Base Population )
    实体连接 属性抽取

## 命名实体识别

识别1. 人名  2. 机构名 3. 地名 4. 时间 5. 日期 6. 货币 7. 百分比

###注意问题

* 人名地名机构名识别难度大，
* 上下文密切，不同而实体在不同语义下具有不同的实体类型，如：新世界

Wu EMNLP 2005

### 主要方法

1. 通过分析种子实体在查询中的上下文，利用模板找到同类别的实例。
2. 构造向量，计算
Ref： Wang ICDM 2007

### 系统框架
    
    爬取模块 --> 抽取模块 --> 排序模块

### 评价指标
使用$MAP$ 进行评测

## 实体消歧
### 定义
一个实体指称项对应多个真实世界的实体。确定一个实体指称对应真实世界的什么实体。
### 常见方法
基于聚类
基于链接

## 基于聚类消歧方法

1. 同一指称项具有近似的上下文
2. 利用聚类算法尽心小气

###关键问题

选取那些特征対指称项进行表示

### 词袋模型

* 利用待消歧词的实体周边的词进行构造向量
* 利用空间模型来计算两种实体指称项的相似度进行聚类
* 没有考虑词的语义信息

###语义特征

* 利用**SVD**挖掘语义特征

### 社会化网络

不同的人具有不同的社会，通过**社会网络关系**挖掘进行消除歧义

####维基百科的知识[Han ]

利用实体上下文的维基百科条目对尸体进行向量表示
利用维基百科条目之间的相似度进行计算指称之间的相似度（解决数据稀疏的问题）

### 多源异构知识[Han ACL 2010]

仅仅使用wikimadia是有限的，通过结合多种知识库，形成语义图进行知识挖掘。

### 实体消歧：评测-WePS

###挑战

消歧目标难以确定
缺乏实体的显示表示

## 基于链接的消歧

* 候选实体发现
* 候选实体的链接
候选实体发现
1. 利用wikipedia发现实体
2. 利用上下文获取缩略语候选实体

### 候选实体链接

### 类别特征[Bunescu EACL 2006]
1. 实体流行度等特征
2. 传统的方法仅仅是计算实体指称项图实体的相似度，未考虑实体的背景，先验知识等问题。

### 结构化数据中的实体链接 [Shen SIGKDD 2012]
### 社交数据中的实体链接[Shen SIGKDD 2013]
### 评测标准-TAC-KBP
### 总结

实体链接方法主要是如何更有效挖掘实体指称项信息，如何更准确地计算湿体质表象和实体概念之间的相似度

## 实体间关系抽取
### 定义

自动识别由一堆概念和联系这对概念的关系构成的相关三元组

###非结构化关系抽取
##传统关系抽取
###基于特征向量：最大熵 和支持向量机

获取有效此词法句法语义特征

###基于核函数：浅层树核和依存树核 最短依存树核等等

挖掘反应语义关系的结构化信息和计算结构化信息之间的相似度

###基于神经网络

如何设计合理的网络结构，从而捕获更多的信息，进而更准确地完成关系的抽取
基于卷积神经网络的关系抽取
判断句子中实体之间的语义关系

#### 传统方法问题

1. 错误累计
2. 人工设计特征
通过CNN学习文本语义特征
不需要人工设计特征

## 开放域关系抽取
### 按需抽取BoostStrapping
    模板生成--> 实体抽取 --> 
<!--Turing Center Machine Reading-->
1. 开放域关系抽取：从NYT中抽取FreeBase的关系类别（Zeng EMNLP 2015）
2. 基于细粒度实体类型特征发现的弱监督关系抽取Liu Coling 2014

## 开放关系的发现
关系发现就是利用知识图谱中现有的知识推断未知的知识，就是链接预测

### 归纳逻辑编程

符合逻辑宝石精确，表达能力强
但是很难在大规模语料库上进行推广。

### 概率图模型

-- 马尔科夫随机场
-- 概率软逻辑

## 机器翻译的产生

1949年，W. Weaver提出“机器翻译”：

    翻译类似于解读密码的过程：当我阅读一篇用俄语写的文章时， 我可以说这篇文章实际上是用英文写的， 只不过它用另外一种奇怪的符号编了码， 当我阅读时， 我是在进行解码。 --1949

## 机器翻译的现状

1990年左右，统计机器翻译由于仅依赖双语平行语料，大大降低了进入机器翻译研究的门槛；
2014年，深度学习应用于机器翻译中，获得performance的提升。

## MT的主要困难

* 句法结构歧义，词汇歧义，新的词汇等未知现象
* 不仅仅是翻译，还有不同语言之间的文化差异
* 翻译结果不唯一

## 基本翻译方法
### 直接转换法

从源语言句子的表层出发，将单词、短语或句子直接置换成目标语言译文，必要时进行简单的词序调整。对原文句子的分析仅满足于特定译文生成的需要。这类翻译系统一般针对某一个特定的语言对，将分析与生成、语言数据、文法和规则与程序等都融合在一起。
例如：
I like Mary. => Me(I) gusta(like) Maria(Mary).
X like Y => Y X gusta

### 基于规则的翻译方法

对源语言和目标语言均进行适当描述、 把翻译机制与语法分开、 用规则描述语法的实现思想， 这就是基于规则的翻译方法。“独立分析－独立生成－相关转换”：
* 对源语言句子进行词法分析
* 对源语言句子进行句法/语义分析
* 源语言句子结构到译文结构的转换
* 译文句法结构生成
* 源语言词汇到译文词汇的转换
* 译文词法选择与生成