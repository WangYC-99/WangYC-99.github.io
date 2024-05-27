# [ACL2022] Knowledge Augmented Tutorial

> by WangYC
>
> @NWPU chang'an May.29th 2022
>
> 原文：http://arxiv.org/abs/2105.09111

[toc]

![image-20220530102953071](Knowledge_Augmented.assets/image-20220530102953071.png)

## 1. Main Idea

* tutorial

* 介绍近期在language understanding，language generation 以及 commensense reasoning领域的sota工作

## 2. Contributions

cutting-edge

···

## 3. Related Knowledge

### 3.1 NLP工作

近期的NLP相关工作受益于large-scale model, training strategies 和 great availability of data

e.g. 

* BERT(https://arxiv.org/abs/1810.04805)
* RoBERTa(https://arxiv.org/abs/1907.11692)
* GPT

#### transformer

Attention is all you need https://arxiv.org/abs/1706.03762

* 传统RNN缺点：序列按照顺序计算，$h_t$通过$h_{t - 1}$以及$t$位置的内容来共同决定，会存在算到后面时早先信息丢失或者内存负载过大的问题。

* Attention以前已经被应用到了从encoder到decoder的衔接过程中。

* 相比于RNN，Attention机制的并行性是亮点。

* 卷积网络替换RNN的问题：比较长的信息难以融合到一起。但是transformer没有这个问题。但是卷积的优点是可以输出多通道的模式，因此transformer提出multi-head的attention。

* transformer中比较关键的点是自注意力的attention。

* 当时的较为popular的网络结构是encoder-decoder (其中encoder做的事情是将输入的n个词条转化为同样的n条向量，即做一个向量表示；decoder则利用self-regressive机制，之前所有的输出都可以作为当前时刻的输入)

* <img src="Knowledge_Augmented.assets/image-20220530152454058.png" alt="image-20220530152454058" style="zoom:50%;" />

* residual connection：在每一层结束后都再加上一个输入，$f(x)$ -> $f(x) + x $，这样可以避免某一层的梯度为0的情况，因为此时梯度有一个恒等项1:$f'(x) + 1$。

* transformer的encoder: $LayerNorm(x + Sublayer(x))$ 用这样的自回归残差连接需要输出和输入的大小一样，否则要做投影。其中两个超参数，第一个是$N$，意思是整个过程重复多少层，第二个就是输入输出的向量的大小$d_{model}$。

* LayerNorm和batchNorm：一般所说的归一化指的是batchNorm，意思是一个batch中所有向量同一个位置的内容的列向量归一化。而LayerNorm则是每个样本自己归一化，每个语句序列的不同词的embedding之间进行归一化。

* Attention: 通过QKV来决定参数。
  $$
  Attention(Q, K, V) = softmax(\frac{{QK}^T}{\sqrt{d_k}})V
  $$
  如下图，其中n是需要计算参数的向量的个数，m是需要加权的项数，如邻居的个数。dk为输入向量本身的长度。![IMG_D657AA3C6228-1](Knowledge_Augmented.assets/IMG_D657AA3C6228-1.jpeg)<img src="Knowledge_Augmented.assets/IMG_70507E82D65F-1.jpeg" alt="IMG_70507E82D65F-1" style="zoom:40%;" />

* 两种最常用的attention机制：additive attention（允许Q和K的长度不相同）；dot-product attention（点积注意力，如上图所示）

* Scaled dot-product attention: 如以上attention公式所说，要除以$\sqrt {d_k}$ , 原因是怕向量长度太长以后点积的结果会出现每一个值都很大的情况。不这样的话在softmax以后会出现梯度很小，训练不动的情况。

* 本文中使用的mask机制：

  <img src="Knowledge_Augmented.assets/image-20220530192858440.png" alt="image-20220530192858440" style="zoom:40%;" />

  这个mask是为了保证在研究第k个词的时候不要看到第k个词以后的词的结果，也就是不能把未来的词汇也聚合到当前的表示中。实现方法就是在得到了参数矩阵以后将未来时刻对应的参数都设置成绝对值很大的负数，这样的话在过一个softmax以后就可以得到趋近于0的权重。

* Multi-head Attention:
  $$
  MultiHead(Q, K, V) = Concat(head_1, head_2, ..., head_h)W^O
  \\where\ head_i = Attention(QW_i^Q, KW_i^K, VW_i^V)
  $$
  之所以采用multihead的一个最直接的原因就是如果只用dot-product的话就没有什么可以学习的参数在里面，因此采用multihead来多几个参数矩阵。实现的过程就是先把n维的输入拆成h个小部分（利用线性层进行降维投影），分别进行attention以后concat到一起，成为最终的参数矩阵（这个concat的过程又加了一个参数矩阵）

* 自注意力机制（QKV都是一样的）

* 只有Q不同的注意力机制（KV相同，Q与KV不同）:跟谁像，谁在我最终结果的表示里面占到的权重就多一点。（我更关注谁，谁在我最后的表示里面占的比重就多一点）

* Feed-Forward：
  $$
  FFN(x) = max(0, xW_1 + b_1)W_2 + b_2
  $$
  说白了其实就是：$linear(relu(linear(x)))$,作用就是做语义空间的转换。

* 使用positional encoding来加入时序信息。词嵌入将一个词表示成为一个指定长度的向量，但是没有词的时许信息。为了让transformer能够提取到词的顺序信息，采用positional encoding的方式来对位置信息进行编码。具体的计算方法是通过以下公式来完成的：
  $$
  PE_{pos, 2i} = sin(pos/10000^{2i/d_{model}})
  \\PE_{pos,2i + 1} = cos(pos/10000^{2i/d_{model}})
  $$
  
* 学习率计算：
  $$
  lr = d_{model}^{-0.5}*min(step_num^{-0.5}, step\_num * warmup\_steps^{-1.5})
  $$
  

* 实践：

  https://zh-v2.d2l.ai/chapter_attention-mechanisms/transformer.html

### 3.2 Knowledge

> It has been shown that these pretrained language models can effectively characterize linguistic patterns in text and generate highquality context-aware representations.
>
> However, these models are trained in a way where the only input is the source text. As a result, these models struggle to grasp external world knowledge about *<u>concepts, relations, and common sense</u>*

这些所谓的概念、关系和尝试就是普通的单纯看文本训练的模型所无法获取到的Knowledge。

#### 3.2.1 用于NLU

> In natural language understanding (NLU), the task is to make predictions about the property of words, phrases, sentences or paragraphs based on the input text

**Structured Knowledge**

1. Explicit methods (entity embeddings)
   1. ERNIE:利用TransE做KG的entity embeddings
2. Implicit methods (entity maskng prediction)
   1. KEPLER：利用基于描述文本的预训练的language module进行entity embedding的计算

近期的工作尝试将KG和language module协同训练：

1. JAKET：用knowledge module来对文本中的entity生成embedding，同时用language module来进行。
2. 利用dictionary descriptions 来对NLU进行knowledge的补充。



**Unstructured Knowledge**

非结构化的知识模型通常是一个检索模型来从语料库中发现知识信息。

1. 利用完形填空任务，针对open-domain QA来进行训练。

## 4. Methods



## 5. Datasets



## 6. Questions

* Knowledge module 和 language module 的区别？什么是KG的context-aware initial embeddings

> JAKET ∗(Yu et al., 2022b) proposes to use the knowledge module to produce embeddings for entities in text while using the language module to generate context-aware initial embeddings for entities and relations in the knowledge graph.

* 如何理解retreiver

-End-

