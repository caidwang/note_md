<!--
 * @Author: sunchao wang
 * @Date: 2021-01-16 20:33:02
 * @LastEditTime: 2021-01-20 14:48:07
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: /note_md/papers/2004-jeffrey-mapreduce.md
-->


# Title

MapReduce: Simpliﬁed Data Processing on Large Clusters


## 0. Summary

写完笔记之后最后填，概述文章的内容，以后查阅笔记的时候先看这一段。注：写文章summary切记需要通过自己的思考，用自己的语言描述。忌讳直接Ctrl + c原文。



## 1. Research Objective

实现一个基于普通主机集群的高可扩展性的分布式编程框架，使用者不需要去考虑计算的并行，系统的容错，数据的分发，负载平衡等问题，专注于业务本身。


## 2. Programming model
计算任务的输入是一个键值对的集，输出是另一个键值对的集，用户将将计算任务抽象成map和reduce两个阶段。

map阶段，map函数接受一个键值对的输入，输出键值对的集合作为中间结果，mapreduce库负责将所有具有相同键的值进行聚合，reduce阶段的输入

reduce阶段，reduce函数接受一个中间结果的键和这个键对应的聚合的值的列表，reduce函数将这些值聚合构建一个可能更小的集合。其中，中间结果的值会以一个迭代器的形式传入到reduce当中以适应值过多超过内存限制的情况。

map(K1, V1) -> list(K2, V2)
reduce(K2, list(V2)) -> list(V2)

具体应用例子：

- **分布式的 Grep** map方法输入一行，如果该行能够匹配，输出该行； reduce方法是一个01函数，只将输入的值进行输出
- **计算URL的访问次数** map方法处理给定的日志，输出\<URL, 1\>的列表，reduce方法将所有相同URL的键值对进行累加，返回\<URL, TOTAL COUNT\>
- **倒排索引** map方法解析一个网页文档，输出一个(word, document ID)的序列；reduce方法接受所有具有给定word的键值对，对documentID进行排序后输出(word, list(doucument ID))，所有的输出集合构成一个简单的倒排索引

## 3. Method(s)

### 执行的基本步骤

![](../pictures/papers/mapreduce/2020-09-20%2019-48-46%20的屏幕截图.png)

1. 输入数据被分割为M份，每个大小通常在16MB到64MB之间，之后在集群中分发多份程序拷贝开始执行
2. 在所有程序的拷贝中选择一份作为master，由其向其他worker分配任务，所有任务包括M个map任务和R个reduce任务，由master选择空闲的worker进行分配
3. 接受到map任务的worker首先获取相应的数据切片，将输入数据解析成键值对并传入用户指定的map函数，map函数产生的中间结果被缓存在内存当中
4. 之后，缓存的中间结果按照分片函数分成R份并储存到本地存储中，worker将这些中间结果的存储位置返回给master，用于传递给之后的reduce方法作为数据输入
5. 当一个reduce worker从master获得地址后，该worker通过rpc从map worker的本地磁盘中获取这些中间数据。当一个reduce worker拿到了所有中间数据后，它首先对这些中间数据进行排序，使得所有的相同key的键值对能够聚合到一起。这种排序的必要性在于一个reduce worker通常会被分配到多个key。如果键值对过多，可以通过外部排序的方式进行排序
6. reduce worker遍历所有的中间结果键值对，对每个遇到的新的key以及弃对应的所有值，将其作为键值对输入用户定义的reduce方法，reduce的输出被追加到该reduce分片的最终输出文件中。
7. 当所有的map和reduce任务完成时，master唤醒用户程序，这个部分结束

### master 数据结构


## 4. Evaluation

作者如何评估自己的方法，实验的setup是什么样的，有没有问题或者可以借鉴的地方。



## 5. Conclusion

作者给了哪些结论，哪些是strong conclusions, 哪些又是weak的conclusions?



## 6. Notes

(optional) 不符合此框架，但需要额外记录的笔记。



## Reference

(optional) 列出相关性高的文献，以便之后可以继续track下去。

