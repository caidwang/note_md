<!--
 * @Author: sunchao wang
 * @Date: 2021-01-16 20:33:02
 * @LastEditTime: 2021-01-22 21:06:46
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



不同环境对应不同版本的合适的mapreduce实现，文章介绍适用于google的环境的实现：

- 大量的普通PC机器
- 商业网络设备
- 运行在具有数百台client的集群之上，机器故障是大概率事件
- 使用便宜的IDE硬盘作为存储，机器可以直接访问这些硬盘，文件系统通过备份实现在不可靠硬件上的可靠性和可用性
- 用户向调度系统提交工作，每个工作由若干个人物足证，调度系统负责将这些任务分发到一个集群中的一些可用的机器上

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
对于每个map和reduce任务，master需要保存一些数据结构进行记录，包括状态（空闲，处理中，处理完成），对于非空闲的任务，需要记录处理它的worker机器编号。同时，master是中间结果路径的从map任务的机器传递到reduce任务的机器的通道，对于每个完成的map任务，master需要记录中间结果的存储位置以及R个中间文件的大小。当map任务完成式，路径信息和大小信息都会被更新。这些信息被增量推送到正在进行reduce任务的worker上。

### 容错

**worker 失效**

master会定期ping worker，当一定时间worker没有响应时，master判断该worker已经失效。

所有已经被该worker完成的map任务会被重新置为空闲状态，并且能够重新调度给其他worker。所有正在被该worker处理的map/reduce任务也会被置为空闲状态。

> 由于map任务处理后的中间结果被存储在worker的本地存储当中，因此如果该worker失效，其上完成的map任务的中间结果也无法访问。当前worker上完成的reduce任务不需要被重新执行因为这类结果会被存储在全局文件系统中。

当一个map任务首先被A机器执行，之后被B机器执行，所有正在执行reduce任务的机器都被通知重新执行。

当集群中发生大规模worker失效时，对mapreduce时不可见的，mapreduce继续按照可达的机器重新执行任务直到任务完成。

**master失效**

master的单点失效并不常见，因此如果出现master失效的情况，mapreduce的执行直接放弃。如果需要的话，用户可以检查这种情况，并重试mapreduce操作。



**“出现失效”的语义**

系统目标：对于确定性的map和reduce函数，分布式的实现的输出与单进程的执行完全一致。对于非确定性的map和reduce函数，对于某个特定的reduce任务$R_1$的输出 ，其结果与某一次线性执行整个非确定性程序相同，而对于另一个特定的reduce任务$R_2$ 的输出，其结果可能与另一次线性执行整个非确定性程序的结果相同。

实现方法：依赖map和reduce任务输出的原子性提交。

对于map任务，当任务完成时，worker将包含R个临时文件名称的消息发送给master，如果master已经接受过了完成该map任务的信息则会忽略这条信息，否则接受这条信息并更新master数据结构中的R个文件的名称。

对于reduce任务，worker首先产生一个私有的临时输出文件，并在完成时将这个文件重命名为最终的输出文件。系统以来原子化的重命名操作，保证最终的文件系统状态中包含一个reduce任务的执行结果。

### 本地化数据存储

为了节约网络带宽资源，mapreduce的输入数据存储在GFS上，分配到集群中的主机当中，mapreduce任务执行时，master会将主机上存放的输入数据信息纳入考虑，尽可能将map任务分配到存放了对应输入数据副本的主机上，减少输入数据在集群中的网络上传递的次数。如果上述尝试失败，系统会继续尝试将任务分配到离数据副本临近的机器上执行（例如在同一个交换机域中）。

### 任务粒度

理想情况下，M和R最好能够比worker数量大得多，因此可以提高负载均衡的能力和在一台worker失效时，提高恢复的速度（失效机器上的任务会被分配到所有的其他机器上去）。

通常情况R会被用于约束，而M的选择通常会使得每个任务的大小大致在16MB到64MB之间。






## 4. Evaluation

作者如何评估自己的方法，实验的setup是什么样的，有没有问题或者可以借鉴的地方。



## 5. Conclusion

作者给了哪些结论，哪些是strong conclusions, 哪些又是weak的conclusions?



## 6. Notes

(optional) 不符合此框架，但需要额外记录的笔记。



## Reference

(optional) 列出相关性高的文献，以便之后可以继续track下去。

