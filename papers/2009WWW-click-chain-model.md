# Click Chain Model in Web Search 阅读笔记
论文出处: WWW 2009\
论文作者: Fan Guo, Chao Liu, Christos Faloutsos等

## 概括
能够增量计算的基于Bayes的click model, 核心是Bayes公式中的"证据"函数的计算, 以及模型中其他行为相关的参数的估计.

模型发展 cascade model - DCM&UCM - CCM
## introduction
Web搜索活动中的点击日志,是反映用户体验的有力调查,并且能够很容易的按照不同时间长度进行聚合,这些统计数据中抽取出的信息和模式能够帮助搜索引擎提供商有效的改善用户体验和帮助网络研究者验证假设和模型.以往的研究表明, 点击事件对于文档相关性的判断已经足够准确但是并不可靠, 即"informative but biased".

click model提供了一种方法来聚合用户搜索信息, 用以推断文档的"用户感知相关性", 而"用户感知相关性可以用于提升一些搜索相关应用的性能.

一个好的click model应当具有**可拓展性**和**支持增量计算**的性质, 在此前的研究中, cascade model, DCM, UCM等模型被提出, 都存在一些问题, 具体会在后文中展开, 因此这篇文章提出了CCM以改进.CCM的优点包括:基础, 可拓展, 高效等, 是一个基于bayes的概率模型.

## background
### 概念与符号表示:
**query session:** 一个检索会话从一次查询提交开始, 重提交或对查询字段的编辑都视为不同的独立检索会话.

**document impression:** 第一页结果页上展示的文档的集合. click model舍弃了之后的页面, 相关查询和定向广告的内容, 可以表示为$D=\{d_1, d_2, \dots ,d_M\}$,通常M=10.

**examination, click:** 一次检视称为examination, 一次点击称为click, 它们都是概率事件, 用二项随机变量$E_i, C_i$表示i个文档是否被检视和点击.

**examination hypothesis:** 文档只有被检视才可能被点击, 文档被点击的概率等于文档的相关性.
$$
P(C_i=1|E_i=0)=0\\
P(C_i=1|E_i=1)=r_{d_i}
$$
其中$r_{d_i}$表示文档相关性, i文档是否被检视和点击, 与之前的检视和点击时间独立.所有click model都符合这样的定义, 但是对于$P(E_i)$存在不同的形式.

### cascade model
最基本的click model是cascade model, 该模型遵循*cascad hypothesis*, 即客户总从检索结果的第一条开始检查, 并严格的逐条向下, 即
$$
P(E_1=1)=1,\\
P(E_{i+1}=1|E_i=0)=0.
$$
除了上述两个hypothesis, 模型的额外约束包括用户会不断检视直到第一次点击,点击后不在看后面的文档直接遗弃当前的query session. 结合以上约束, 模型可以总结为下式
$$
P(E_{i+1}=1|E_i=1,C_i)=1-C_i \tag{1}
$$
模型的缺点:
- 没有考虑当在一个query session中发生多次点击时怎么表示以及怎么估计这种情况下的文档相关性.

### Dependent click model(DCM)
引入了一个点击事件后检视下一个文档的条件概率作为位置相关的参数, 将*cascade model*推广到多次点击的情形, 即
$$
P(E_{i+1}=1|E_i=1, C_i=1)=\lambda_i \tag{2}
$$
$$
P(E_{i+1}=1|E_i=1, C_i=0)=1, \tag{3}
$$
其中$\lambda_i$是行为参数, 全局共享. 模型的整体概率可以表示成
$$
P(C_{1:M})=\prod_{i=1}^l ((r_{d_i}\lambda_i)^{C_i}(1-r_{d_i})^{1-C_i})\cdot (1-\lambda_l+\lambda_l \prod_{j=l+1}^M(1-r_{d_j}))
$$
$l=argmax_{1\leq i\leq M}\{C_i=1\}$表示最后一个点击位置, 如果没有点击, l=0.

模型缺点:
- 模型假设了用户会扫视搜索结果的整个列表, 与现实不贴切.

### User browsering model(UBM)
该模型假设检视的概率$E_i$只与上一次点击的位置$l_i=argmax_{l<i}\{C_l=1\}$有关, 其中距离可以表示为$i-l_i$, $P(E_i)$的定义如下:
$$
P(E_i=1|C_{1:i-1})=\gamma_{l_i,i-l_i} \tag{5}
$$
因为$0 \leq l_i < i \leq M$, 总共有M (M + 1) / 2的用户行为参数$\gamma$.模型概率可以表示为
$$
P(C_{1:M})=\prod_{i=1}^M (r_{d_i}\gamma_{l_i,i-l_i})^{C_i}(1-r_{d_i}\gamma_{l_i,i-l_i})^{1-C_i} \tag{6}
$$
