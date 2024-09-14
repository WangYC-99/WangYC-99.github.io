---
permalink: /
title: "About Me"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---
I am a Ph.D. student at the School of Information, Renmin University of China, under supervision of [Jing Zhang](https://xiaojingzi.github.io/). 
At the same time, I'm an intern at THUKEG and ZHIPU.AI, under supervision of [Jifan Yu](https://yujifan0326.github.io/). 
Previous to that, I graduated from [Honors College](https://honors.nwpu.edu.cn/) of Northwestern Polytechnical University, where I majored in Computer Science and Technology. 

Currently, my research focuses on **Tool Intelligence of LLMs** and **AI for Education**.
Besides, I love soccer⚽️, photography📷, and snowboarding🏂. 
I also keep training for triathlon races 🏊 🚴 🏃.
Feel free to contact me for our shared interests whether in research or life.

# What's New!
* [R-Eval](https://arxiv.org/abs/2406.11681) has been accepted by KDD'24!
* We create a [Tool Intelligence Paper-reading List](https://github.com/RUCKBReasoning/ToolIntelligence_Reading_List), welcome to follow!

# Publications

## 2024
### From MOOC to MAIC: Reshaping Online Teaching and Learning through LLM-driven Agents
*Arxiv preprint*
<br> Jifan Yu, Zheyuan Zhang, Daniel Zhang-li, Shangqing Tu, Zhanxin Hao, Rui Miao Li, Haoxuan Li, **Yuanchun Wang**, Hanming Li, Linlu Gong, Jie Cao, Jiayin Lin, Jinchang Zhou, Fei Qin, Haohua Wang, Jianxiao Jiang, Lijun Deng, Yisi Zhan, Chaojun Xiao, Xusheng Dai, Xuan Yan, Nianyi Lin, Nan Zhang, Ruixin Ni, Yang Dang, Lei Hou, Yu Zhang, Xu Han, Manli Li, Juanzi Li, Zhiyuan Liu, Huiqin Liu, Maosong Sun
<div style="display: flex; align-items: center;">
    <div style="flex: 1;">
        <img src="https://wangyc-99.github.io/images/pubs/maic.png" alt="maic.jpg">
    </div>
    <div style="flex: 2;">
        MAIC (Massive AI-empowered Course) is a new form of online education that leverages LLM-driven multi-agent systems. This project will continue to evolve, ultimately aiming to establish a comprehensive open platform that supports and unifies research, technology, and applications in exploring the possibilities of online education in the era of large model AI. to construct an AI-augmented classroom, balancing scalability with adaptivity.
    </div>
</div>

### R-Eval: A Unified Toolkit for Evaluating Domain Knowledge of Retrieval Augmented Large Language Models
*Proceedings of KDD'24 (Industry Track)*
<br> Shangqing Tu and **Yuanchun Wang** (equal contribution), Jifan Yu, Yuyang Xie, Yaran Shi, Xiaozhi Wang, Jing Zhang, Lei Hou, Juanzi Li
<div style="display: flex; align-items: center;">
    <div style="flex: 1;">
        <img src="https://wangyc-99.github.io/images/pubs/reval.jpg" alt="reval.jpg">
    </div>
    <div style="flex: 2;">
        A Python toolkit designed to streamline the evaluation of different RAG workflows in conjunction with LLMs. Our toolkit, which supports popular built-in RAG workflows and allows for the incorporation of customized testing data on the specific domain.
        * User-friendly: R-Eval provides easy-to-use scripts for running and analysing experiments with the given models and datasets automatically.
        * Modular: R-Eval is designed to be modular, which allows users to easily extend the framework with new models, datasets, and analysis tools.
        * Extensibility: The domain-agnostic design of R-Eval makes it easy to evaluate Retrieval Augmented Large Language Models on new domain based on our framework.
    </div>
</div>
[[code](https://github.com/THU-KEG/R-Eval)], [[PDF](https://arxiv.org/pdf/2406.11681)]

### A Solution-based LLM API-using Methodology for Academic Information Seeking
*Arxiv preprint*
<br> **Yuanchun Wang**, Jifan Yu, Zijun Yao, Jing Zhang, Yuyang Xie, Shangqing Tu, Yiyang Fu, Youhe Feng, Jinkai Zhang, Jingyao Zhang, Bowen Huang, Yuanyao Li, Huihui Yuan, Lei Hou, Juanzi Li, Jie Tang
<div style="display: flex; align-items: center;">
    <div style="flex: 1;">
        <img src="https://wangyc-99.github.io/images/pubs/soay.jpg" alt="soay.jpg">
    </div>
    <div style="flex: 2;">
        A solution-based LLM API-using methodology for academic information seeking, which is named SoAy.  
        It uses code with a solution as the reasoning method, where a solution is a pre-constructed API calling sequence. 
        The addition of the solution reduces the difficulty for the model to understand the complex relationships between APIs. 
        Code improves the efficiency of reasoning.
        To evaluate SOAY, we introduce SOAYBench, an evaluation benchmark accompanied by SOAYEval, built upon a cloned environment of APIs from AMiner.
    </div>
</div>
[[code](https://github.com/RUCKBReasoning/SoAy)], [[PDF](https://arxiv.org/pdf/2405.15165)], [[System](https://soay.aminer.cn)], [[Application](https://chatglm.cn/main/gdetail/65bf5a99396389a73ace9352)], [[Model](https://huggingface.co/frederickwang99/soayllama_v2_7b)], [[Benchmark & Dataset](https://huggingface.co/datasets/frederickwang99/SoAyBench)]

## 2023

### GKD: A General Knowledge Distillation Framework for Large-scale Pre-trained Language Model
*Proceedings of ACL'23 (Industry Track)*
<br> Shicheng Tan, Weng Lam Tam, **Yuanchun Wang**, Wenwen Gong, Shu Zhao, Peng Zhang, Jie Tang
<div style="display: flex; align-items: center;">
    <div style="flex: 1;">
        <img src="https://wangyc-99.github.io/images/pubs/gkd.jpg" alt="gkd.jpg">
    </div>
    <div style="flex: 2;">
        A general knowledge distillation framework that supports distillation on larger-scale PLMs using various distillation methods.
        With GKD, developers can build larger distillation models on memorylimited GPUs and easily switch and combine different distillation methods within a single framework.
        Experimental results show that GKD can support the distillation of at least 100B-scale PLMs and 25 mainstream methods on 8 NVIDIA A100 (40GB) GPUs.
    </div>
</div>
[[code](https://github.com/aitsc/GLMKD)], [[PDF](https://aclanthology.org/2023.acl-industry.15.pdf)]

***

### Are Intermediate Layers and Labels Really Necessary? A General Language Model Distillation Method
*Findings of ACL 2023*
<br> Shicheng Tan, Weng Lam Tam, **Yuanchun Wang**, Wenwen Gong, Shu Zhao, Peng Zhang, Jie Tang
<div style="display: flex; align-items: center;">
    <div style="flex: 1;">
        <img src="https://wangyc-99.github.io/images/pubs/glmd.jpg" alt="glmd.jpg">
    </div>
    <div style="flex: 2;">
        A general language model distillation (GLMD) method that performs two-stage word prediction distillation and vocabulary compression, which is simple and surprisingly shows extremely strong performance.
        Specifically, GLMD supports more general application scenarios by eliminating the constraints of dimension and structure between models and the need for labeled datasets through the absence of intermediate layers and golden labels. 
        Meanwhile, based on the long-tailed distribution of word frequencies in the data, GLMD designs a strategy of vocabulary compression through decreasing vocabulary size instead of dimensionality.
    </div>
</div>
[[code](https://github.com/aitsc/GLMKD)], [[PDF](https://aclanthology.org/2023.findings-acl.614.pdf)]

## 2022

### NHGMI: Heterogeneous graph multi-view infomax with node-wise contrasting samples selection
*Knowledge-Based Systems*
<br> Qing Li, Hang Ni and **Yuanchun Wang**
<div style="display: flex; align-items: center;">
    <div style="flex: 1;">
        <img src="https://wangyc-99.github.io/images/pubs/nhgmi.jpg" alt="nhgmi.jpg">
    </div>
    <div style="flex: 2;">
        A novel unsupervised method for heterogeneous graph representation learning, rooted in the principles of mutual information maximization.
        NHGMI comprehensively harnesses the inherent characteristics of HINs and adeptly amalgamates diverse semantic information emanating from multiple contrasting perspectives. 
        In addition to inter-view contrasts, NHGMI also incorporates intra-view contrasts. 
        Diverging from conventional contrastive learning approaches, NHGMI meticulously selects contrasting samples based on similarity metrics, thereby achieving a noise-free contrastive learning paradigm.
    </div>
</div>
[[code](https://github.com/KennyNH/NHGMI)], [[PDF](https://www.sciencedirect.com/science/article/abs/pii/S0950705124001552)]