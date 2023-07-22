### XunFeiCompetition-KeyPhraseExtraction
  讯飞开放平台-基于论文摘要的文本分类与关键词抽取挑战赛
  https://challenge.xfyun.cn/topic/info?type=abstract-of-the-paper&ch=vWxQGFU
  https://github.com/Treelaw/XunFeiCompetition-KeyPhraseExtraction/tree/main


## 任务一：二分类
# 主要思路
  使用词袋法抽取句子特征向量
  使用逻辑回归进行二分类
  
# 主要的几个库
----CountVectorizer详解
  CountVectorizer是属于常见的特征数值计算类，是一个文本特征提取方法。对于每一个训练文本，它只考虑每种词汇在该训练文本中出现的频率。
  https://blog.csdn.net/weixin_38278334/article/details/82320307

----逻辑回归（Logistic regression）
  https://zhuanlan.zhihu.com/p/46941769


## 任务二：关键词抽取任务
# baseline使用词频法抽取关键词:
  step1: 分词
  step2: 2-grams
  step3: 将2-grams的两个单词中包含停用词的2-grams剔除
  step4: 将2-grams的两个单词的字符串长度小于或者等于3的剔除
  step5: 保留2-grams词频大于1的部分
  step5: 保留词频最高的5个2-grams

# 主要的几个库
----ngrams    
  短语生成, e.g. 2-grams: 2个单词构成的短语  
----word_tokenize
  分词
