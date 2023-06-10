> 本项目包含两个内容，面向知识图谱的频繁模式挖掘与对指令数据的无监督聚类任务。

> Part1：
> > 知识图谱（Knowledge Graphs）由三元组 (h, r, t) 表示的知识组成
> > 而这些元知识可以很大程度上帮助不管是人类还是人工智能模型理解和生成知识体系，从而构建更加庞大的知识图谱或大模型。我们从最基础的频繁模式
> > 挖掘出发，首先尝试挖掘出知识图谱中存在的关联规则和元路径
> > 并尝试构建出合理的推理规则等，以实现从知识图谱到推理规则的生成过程。
>
> > 本次实验提供的知识图谱数据集共有 4590547 条 json 记录，每条记录组成为 qid 字段，
types 字段，head_triples 字段，tail_triples 字段，types 字段中含有零或多
个 type 类型，head_triples 和 tail_triples 字段包含零或多个三元组。三元组数量最大值为62331.

> > 项目实现过程为：
> > 1.数据处理 2.构建FP-tree 3.挖掘频繁项集 4.抽取条件模式基 5.结果生成 

> Part2:
> > 高质量数据是大语言模型训练的关键，尤其是高质量的指令/对话数据
对大语言模型的指令微调（instruction fine-tuning, ift）至关重要。高质量
指令数据集需要具有两个特点： 
1.数据集内的不同对话应多样性； 
2.对话
内容合理，能体现一定的深度、知识。
而如何构建高质量指令/对话数据，以及如何对低质量的数据进行清洗，
则需要对指令数据进行一定的处理和识别。而我们想到的方向则是可以通
过聚类方法对指令/对话数据首先进行分类，能够大致区分数据的类别，以
便更好的进行数据清理操作。
>
> > 聚类算法使用的数据集为 ift_cluster_given_fudandm2023.jsonl：每个
json 样本包含两个字段，‘input’表示样本的文本，’label’ 均为’?’，表示该
样本的类别未知。数据包含英语数据和中文数据，也包含对话数据和 NLP
任务数据。真实类别包括 cn_chat, en_chat, cn_mrc, en_mrc, cn_nli（mrc
表示机器阅读理解，nli 表示自然语言推断）等预估共有70-100簇。

> > 项目实现过程为：1.数据处理，通过词频模型或语言模型生成句向量 2.对句向量进行聚类分析