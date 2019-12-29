# 2020ICRL-Neural execution of graph algorithms
- [概括](#%e6%a6%82%e6%8b%ac)
- [问题设定](#%e9%97%ae%e9%a2%98%e8%ae%be%e5%ae%9a)
- [实验设定](#%e5%ae%9e%e9%aa%8c%e8%ae%be%e5%ae%9a)
- [结果分析讨论](#%e7%bb%93%e6%9e%9c%e5%88%86%e6%9e%90%e8%ae%a8%e8%ae%ba)

## 概括
使用GNN训练除能够用于多个图算法的算法执行器, 证明了GNN在图结构的输入上的强大表示能力.
将传统图算法(BFS, Bell-Ford, Prim)中算法执行的每一步的决策作为标签,上一步决策后的图信息作为输入, 预测算法在当前时间步的决策, 网络最终能够学习到传统算法的选择策略.

文章的动机: 目标是增强GNN的更新规则中的算法可解释性, 增强这种归纳性的认知。这种认知对于例如发现新颖的算法或改进现有算法是个很重要的前提。文章还通过实验证明了在学习两种不同算法（BFS和Bellman-Ford）之间的转换，这直接指出了一个学到的算法执行器增强另一种算法的预测的准确性的潜力。

## 问题设定
输入: 
- 一个T长的graph-structured的图的序列: 序列中的图G是固定的,点和边的信息是变化的
  - 点 $\vec{x_i}^{(t)} \in R^{N_x}, \quad i \in V$
  - 边 $\vec{e_{ij}}^{(t)} \in R^{N_e}$
- 待学习的算法A

输出:
- $\vec{y_i}^{(t)} \in R^{N_y}, \quad i \in V$

**网络的组成:**

Encoder: $f_A$ 与A相关, 输出与节点相关, $\vec{z_i}^{(t)}=f_A(x_i^{(t)}, \vec{h_i}^{(t-1)})$, 其中${h_i}^{(0)} = \vec{0}$

Processor: $P$ 与A无关, $H^{(t)}=P(Z^{(t)}, E^{(t)})$

Decoder: $g_A$ 与A相关, 输出与节点相关, $\vec{y_i}^{(t)}=g_A(z_i^{(t)}, \vec{h_i}^{(t)})$

Temination: $T_A$ 与A相关, $\tau^{(t)}=\sigma(T_A(H^{(t)}, \overline{H^{(t)}})$, 得到的是决定算法是否要进行下一个时间步的概率, 当$\tau > 0.5$时, 算法从Encoder重复.

其中$\overline{H^{(t)}} = \frac{1}{|V|} \sum_{i\in V}\vec{h_i}^{(t)}$

> Tips:
> 
> - $\vec{x_i}^{t+1}$会部分或完全引入$\vec{y_i}^{t}$的信息,即从上一个时间步的决策作为下一步的输入信息.
> - 输出中可以很容易的输出和边相关的结果以及和图相关的结果, 文章中并没有用到,所以输出只输出和节点相关的内容.
> - $h_i$的计算可以通过GNN层获得, 使用到用于比较的GNN有GAT, MPNNS及变种

## 实验设定
图类型:
- 7种
- 每个点, 新加self-edge: 利于信息传递
- 对每个边分配随机分配权重, 符合[0.2, 1]的平均分布, 对于所有时间步t, 这个参数作为边上的唯一信息.
- 这种边权采样保证了结果恢复的唯一性, 简化了对比分析

> 为什么认为学习算法的执行具有扩展性: 人类专家从小图观察规律, 设计算法用于大图, 因此认为算法也能够学到类似的规律

**Parallel algo:**
- BFS 每个点维护bool, 表示是否可达
- BF 每个点维护Real, 表示与s的最短距离
- 文章断言称这类算法的需要在邻域上做离散决策的特点,很适合max-aggregator MPNN来学习执行.

BFS:
$$
x_{i}^{(1)}=
\begin{cases}
\begin{aligned}
1 & , & i=s \\
0 & , & i \neq s
\end{aligned}
\end{cases}
\qquad
x_{i}^{(t+1)}=
\begin{cases}
\begin{aligned}
1 & , & x_i^{t} = 1 \\
1 & , & \exist j.(j,i) \land x_j^{(t)}=1 \\
0 & , & otherwise
\end{aligned}
\end{cases}
\\ \quad
\\
x_i^{(t+1)} = y_i^{(t)}
$$

BF:
$$
x_{i}^{(1)}=
\begin{cases}
\begin{aligned}
1 & , & i=s \\
+\infty & , & i \neq s
\end{aligned}
\end{cases}
\qquad
x_{i}^{(t+1)}=min(\vec{x_i^{(t)}, min_{j,i)} x_j^{(t)} + e_{ji}^{(t)}})
\\ \quad
\\
y_i^{(t)}=P_i^{(t)} || x_i^{(t+1)} \text{(|| means concat)}
$$

**Sequential algo:**
- seq的一类算法, 在每个时间步只处理一个节点, 在构造算法中常见
- 文章希望能够证明, 图神经网络也能很好的学到序列模型的算法

Prim:

$$
x_{i}^{(1)}=
\begin{cases}
\begin{aligned}
1 & , & i=s \\
0 & , & i \neq s
\end{aligned}
\end{cases}
\qquad
x_{i}^{(t+1)}=
\begin{cases}
\begin{aligned}
1 & , & x_i^{t} = 1 \\
1 & , & i=argmin_{j s.t. x_j^{(t)}=0} min_{k.s.t. x_k^{(t)}=1} e_{jk}^{(t)},*\\
0 & , & otherwise
\end{aligned}
\end{cases}
\\ \quad
\\
p_i^{(t)}=
\begin{cases}
\begin{aligned}
i & , & i=s\\
P_i^{(t-1)} &, & i\neq s \land x_i^{(t)}=1\\
argmin_{x_j^{(t)}=1} e_{ij}^{(t)} &, & x_i^{(t)}=0 \land x_i^{(t+1)}=1, *
\end{aligned}
\end{cases}
\qquad
y_i^{(t)}=P_i^{(t)} || x_i^{(t+1)} \text{(|| means concat)}
$$

* \*标注的部分只针对当前时间步选择的节点更新

* 其中$p_i$是前驱节点预测, 由于恢复solution

**网络结构**

在processor的模型选择上, 除了max-aggregator的MPNN, 文章还设置了GAT, mean-aggregator MPNN, sum-aggregator MPNN. 为了说明图神经网络是必须的, 文章还设置了非图神经网络的结构, 由于前面已经有文章说明, MLP不适合变节点树的情况, 最终引入了一个LSTM的结构作为对照.

模型使用的是**监督学习**
- bin cross-entropy: reachibility
- mean squared error: distance
- categorical cross-entropy: predecessor node
- bin cross-entropy: termination

**Tips**
- 如果在|V|步后模型的termination没有终止, 默认算法终止
- 对于seq类的问题,categorical cross-entropy预测的是下一个节点, 为此需要将未加入MST的节点添加mask

## 结果分析讨论

训练:使用模型在20个节点的图上学习

测试方法: 应用到20, 50, 100节点规模测试过程准确性和最终准确性.

结论:

**额外指标**: 迁移学习的对比

动机: 图网络学习到的是什么信息?

通过在一类图上训练, 在另一类图上测试, 得出MPNN-max能够在学习到输入图中的结构相似性在不同类的图中获得较好的bias.
