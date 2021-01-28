<!--
 * @Author: your name
 * @Date: 2020-11-22 16:30:06
 * @LastEditTime: 2020-11-22 16:45:35
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: /undefined/Users/wsc/Documents/实验室工作/VSR-LKH.md
-->

# Title

Combining Reinforcement Learning with Lin-Kernighan-Helsgaun Algorithm for the Traveling Salesman Problem

## 0. Summary

写完笔记之后最后填，概述文章的内容，以后查阅笔记的时候先看这一段。注：写文章summary切记需要通过自己的思考，用自己的语言描述。忌讳直接Ctrl + c原文。



## 1. Research Objective

DRL方式的组合优化方法难以扩展，LKH的候选集遍历方式可能导致其错过最优解，用Q-value，sarsa，monto-carlo方式替代LKH中不灵活的遍历方式都可以大幅提升LKH的表现，三种方式在不同的算例集有不同的表现，文章受到VNS的启发，将三种方式进行组合，进一步提升算法的表现

- 用q-value替代$\alpha-nearness$，结合了城市距离，$\alpha$值，候选城市排序，经验结果证明更优
- 提出VSR-LKH进一步提高LKH的表现
- 提出将这种选择机制进行进一步泛化到组合优化中

## 2. Problem Statement

问题陈述，需要解决的问题是什么？



## 3. Method(s)

作者解决问题的方法/算法是什么？是否基于前人的方法？



## 4. Evaluation

作者如何评估自己的方法，实验的setup是什么样的，有没有问题或者可以借鉴的地方。



## 5. Conclusion

作者给了哪些结论，哪些是strong conclusions, 哪些又是weak的conclusions?



## 6. Notes

(optional) 不符合此框架，但需要额外记录的笔记。



## Reference

(optional) 列出相关性高的文献，以便之后可以继续track下去。