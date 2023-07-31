# XunFeiCompetition-KeyPhraseExtraction
    讯飞开放平台-基于论文摘要的文本分类与关键词抽取挑战赛
    https://challenge.xfyun.cn/topic/info?type=abstract-of-the-paper&ch=vWxQGFU
    https://github.com/Treelaw/XunFeiCompetition-KeyPhraseExtraction/tree/main


## 任务一：二分类
### baseline 1: 词频法+logistic regression
#### 主要思路
    使用词袋法抽取句子特征向量
    使用逻辑回归进行二分类
  
#### 主要的API
##### CountVectorizer详解
    CountVectorizer是属于常见的特征数值计算类，是一个文本特征提取方法。对于每一个训练文本，它只考虑每种词汇在该训练文本中出现的频率。
    https://blog.csdn.net/weixin_38278334/article/details/82320307

##### 逻辑回归（Logistic regression）
    https://zhuanlan.zhihu.com/p/46941769

### baseline 2: Bert+ffn
#### 主要思路
    Bert模型对文本的每个token生成向量，将cls这个token位置接入ffn，对token进行二分类，判断其是否是医学文本
#### 优化方法
    将模型最后生成的每个token向量进行mean pooling, max pooling, min pooling等方式求得句向量，再将句向量接入ffn进行分类。


## 任务二：关键词抽取任务
### baseline 1: 使用词频法抽取关键词:
    step1: 分词
    step2: 2-grams
    step3: 将2-grams的两个单词中包含停用词的2-grams剔除
    step4: 将2-grams的两个单词的字符串长度小于或者等于3的剔除
    step5: 保留2-grams词频大于1的部分
    step5: 保留词频最高的5个2-grams

#### 主要的API
##### ngrams    
    短语生成, e.g. 2-grams: 2个单词构成的短语  
    
##### word_tokenize
    分词

### baseline 2: 使用词频/Tf-idf + Bert无监督方法:
#### KeyBert
#### 主要思路
    使用词频/Tf-idf生成文本的候选关键词
    使用Bert类的预训练模型生成文本和候选关键词的向量
    求文本和候选关键词之间的相似度，并根据相似度进行排序，最终求得关键词

### baseline 3: 使用序列标注的有监督微调方法：
#### Bert+ffn
#### 主要思路
    Bert模型对文本的每个token生成向量，每个token位置接入ffn，对token进行二分类，判断其是否是关键词

## 任务三：大模型应用
### baseline1: 使用Chatglm2进行文本二分类

### baseline2：使用Chatglm2进行关键词抽取
