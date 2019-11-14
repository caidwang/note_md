# Introduction ot Information_Retrieval

## IIR 1 Boolean Retrieval

**关键词**: 倒排索引 布尔模型

IR定义: 在非结构化材料中(文本)搜索满足信息需求的材料(文档)

**布尔模型**
- 查询是bool表达式
- 搜索引擎返回全部满足bool表达式的文档

**token&term关系**
- Word – A delimited string of characters as it appears in the text.
- Term – A “normalized” word (case, morphology, spelling etc); an equivalence class of words.
- Token – An instance of a word or term occurring in a document.
- Type – The same as a term in most cases: an equivalence class of tokens.


### 倒排索引

grep存在问题
- 慢
- grep是按行的, IR是面向文档的
- 否条件不好操作
- near这种条件无法实现

因此通过建立矩阵的方式:
1. 建立文档-词索引矩阵, 元素为1表示term在文档中出现, 因此对每个term有一个0/1向量.
2. 对查询中涉及到的词的向量做交集,对于not等条件取反, 就得到了结果.

**存在的问题**: 矩阵过于稀疏; **解决方法**: 邻接表表示, 每个termt, 保存一个链表, 链表中的元素是包含t的文档的编号.

倒排索引的构造:
- 收集需要索引的文档
- 对文本tokenize, 将文档转换为标识的列表
- 对token进行标准化得到用于索引的term
- 对term出现的文档进行索引, 产生一个倒排索引, 包含一个dictionary和对应的posting(文档编号的链表)

倒排索引中需要解决的问题:
- 如果对大集合构建索引:
- 需要多少空间存储dictionary和posting:
- 索引压缩:
- ranked retrieval, 如何获得最好的结果:

倒排索引用于查询的步骤: 1.定位到dictionary中的term, 2. 拿到各个term的posting, 3. 取交集获得最终的结果.

*tips*: 实际操作中, 从长度最短的posting开始合并.即获取terms后按照频率升序排序

## IIR 2: The term vocabulary and postings lists

**关键词** 多语言 vocabulary of terms, 跳跃点, 短语解析

简单布尔检索的假设和问题
- 假设: 文档已知; 词组已知;
- 问题: 如何判断文档, 如何定义和处理文档集合中的term vocabulary

## IRR 5: Index Compression

预处理中的一些步骤可以看做有损压缩: 小写化,停用词, porter, number elimination

Heaps' Law: 词典大小与token数量的关系

Zipf's law: 高频词在文档集合中出现的频率关系.

### 词典压缩
- 定长元素(20bytes-term, 4bytes-freq, 4bytes-pointer_to_posting)不好, term字长浪费同时不能表示所有单词.
- 将词典的terms连成一个string, 词典的每一项引出一个指针指向string中位置表示term, 同时增加length.
- front coding, 将不同词的相同前缀只进行一次表示,在之后用特殊符号代替

### posting压缩
- 基本的想法是一个posting是一个docID, 可以用整型或更小范围的正整数表示.
- 使用ID之间的gap表示, 可以使得数值更小
- 变长编码: 对于gap小于128, 低7位编码, 第一位设为1; gap大于128, 例如511(1 1111 1111), 从从高位开始排, 即 0,0000011 1,1111111
- Gamma code 对gap编码

## 