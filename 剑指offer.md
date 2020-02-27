# 剑指Offer
- [剑指Offer](#%e5%89%91%e6%8c%87offer)
  - [语法Tips](#%e8%af%ad%e6%b3%95tips)
  - [第二章](#%e7%ac%ac%e4%ba%8c%e7%ab%a0)
    - [面试题3 数组查找重复数字](#%e9%9d%a2%e8%af%95%e9%a2%983-%e6%95%b0%e7%bb%84%e6%9f%a5%e6%89%be%e9%87%8d%e5%a4%8d%e6%95%b0%e5%ad%97)
      - [问题扩展: 不修改数组找出重复数字](#%e9%97%ae%e9%a2%98%e6%89%a9%e5%b1%95-%e4%b8%8d%e4%bf%ae%e6%94%b9%e6%95%b0%e7%bb%84%e6%89%be%e5%87%ba%e9%87%8d%e5%a4%8d%e6%95%b0%e5%ad%97)
    - [面试题4 二维数组的查找](#%e9%9d%a2%e8%af%95%e9%a2%984-%e4%ba%8c%e7%bb%b4%e6%95%b0%e7%bb%84%e7%9a%84%e6%9f%a5%e6%89%be)
    - [面试题5 替换空格](#%e9%9d%a2%e8%af%95%e9%a2%985-%e6%9b%bf%e6%8d%a2%e7%a9%ba%e6%a0%bc)
    - [面试题6 从尾到头打印链表](#%e9%9d%a2%e8%af%95%e9%a2%986-%e4%bb%8e%e5%b0%be%e5%88%b0%e5%a4%b4%e6%89%93%e5%8d%b0%e9%93%be%e8%a1%a8)
    - [面试题7 重建二叉树](#%e9%9d%a2%e8%af%95%e9%a2%987-%e9%87%8d%e5%bb%ba%e4%ba%8c%e5%8f%89%e6%a0%91)
    - [面试题8 二叉树的下一个节点](#%e9%9d%a2%e8%af%95%e9%a2%988-%e4%ba%8c%e5%8f%89%e6%a0%91%e7%9a%84%e4%b8%8b%e4%b8%80%e4%b8%aa%e8%8a%82%e7%82%b9)
    - [面试题9 用两个栈实现队列](#%e9%9d%a2%e8%af%95%e9%a2%989-%e7%94%a8%e4%b8%a4%e4%b8%aa%e6%a0%88%e5%ae%9e%e7%8e%b0%e9%98%9f%e5%88%97)
    - [面试题10 斐波那契数列](#%e9%9d%a2%e8%af%95%e9%a2%9810-%e6%96%90%e6%b3%a2%e9%82%a3%e5%a5%91%e6%95%b0%e5%88%97)
    - [面试题11 旋转数组的最小数字](#%e9%9d%a2%e8%af%95%e9%a2%9811-%e6%97%8b%e8%bd%ac%e6%95%b0%e7%bb%84%e7%9a%84%e6%9c%80%e5%b0%8f%e6%95%b0%e5%ad%97)
    - [面试题12 矩阵中的路径](#%e9%9d%a2%e8%af%95%e9%a2%9812-%e7%9f%a9%e9%98%b5%e4%b8%ad%e7%9a%84%e8%b7%af%e5%be%84)
    - [面试题13 机器人的运动范围](#%e9%9d%a2%e8%af%95%e9%a2%9813-%e6%9c%ba%e5%99%a8%e4%ba%ba%e7%9a%84%e8%bf%90%e5%8a%a8%e8%8c%83%e5%9b%b4)
    - [面试题14 剪绳子](#%e9%9d%a2%e8%af%95%e9%a2%9814-%e5%89%aa%e7%bb%b3%e5%ad%90)
    - [面试题15 二进制中1的个数](#%e9%9d%a2%e8%af%95%e9%a2%9815-%e4%ba%8c%e8%bf%9b%e5%88%b6%e4%b8%ad1%e7%9a%84%e4%b8%aa%e6%95%b0)
  - [第三章](#%e7%ac%ac%e4%b8%89%e7%ab%a0)
    - [面试题16 数值的整数次方](#%e9%9d%a2%e8%af%95%e9%a2%9816-%e6%95%b0%e5%80%bc%e7%9a%84%e6%95%b4%e6%95%b0%e6%ac%a1%e6%96%b9)
    - [面试题 17 打印1到最大的n位数](#%e9%9d%a2%e8%af%95%e9%a2%98-17-%e6%89%93%e5%8d%b01%e5%88%b0%e6%9c%80%e5%a4%a7%e7%9a%84n%e4%bd%8d%e6%95%b0)
    - [面试题18 删除链表中的结点](#%e9%9d%a2%e8%af%95%e9%a2%9818-%e5%88%a0%e9%99%a4%e9%93%be%e8%a1%a8%e4%b8%ad%e7%9a%84%e7%bb%93%e7%82%b9)
      - [题目1 O(1)时间删除链表中的节点](#%e9%a2%98%e7%9b%ae1-o1%e6%97%b6%e9%97%b4%e5%88%a0%e9%99%a4%e9%93%be%e8%a1%a8%e4%b8%ad%e7%9a%84%e8%8a%82%e7%82%b9)
      - [题目2 删除链表中的重复节点](#%e9%a2%98%e7%9b%ae2-%e5%88%a0%e9%99%a4%e9%93%be%e8%a1%a8%e4%b8%ad%e7%9a%84%e9%87%8d%e5%a4%8d%e8%8a%82%e7%82%b9)
    - [面试题19 正则表达式匹配](#%e9%9d%a2%e8%af%95%e9%a2%9819-%e6%ad%a3%e5%88%99%e8%a1%a8%e8%be%be%e5%bc%8f%e5%8c%b9%e9%85%8d)
    - [面试题20 表示数值的字符串](#%e9%9d%a2%e8%af%95%e9%a2%9820-%e8%a1%a8%e7%a4%ba%e6%95%b0%e5%80%bc%e7%9a%84%e5%ad%97%e7%ac%a6%e4%b8%b2)
    - [面试题21 调整数组顺序使奇数位于偶数前面](#%e9%9d%a2%e8%af%95%e9%a2%9821-%e8%b0%83%e6%95%b4%e6%95%b0%e7%bb%84%e9%a1%ba%e5%ba%8f%e4%bd%bf%e5%a5%87%e6%95%b0%e4%bd%8d%e4%ba%8e%e5%81%b6%e6%95%b0%e5%89%8d%e9%9d%a2)
    - [面试题22 链表中倒数第k个节点](#%e9%9d%a2%e8%af%95%e9%a2%9822-%e9%93%be%e8%a1%a8%e4%b8%ad%e5%80%92%e6%95%b0%e7%ac%ack%e4%b8%aa%e8%8a%82%e7%82%b9)
    - [面试题23 链表中环的入口节点](#%e9%9d%a2%e8%af%95%e9%a2%9823-%e9%93%be%e8%a1%a8%e4%b8%ad%e7%8e%af%e7%9a%84%e5%85%a5%e5%8f%a3%e8%8a%82%e7%82%b9)
    - [面试题24 反转链表](#%e9%9d%a2%e8%af%95%e9%a2%9824-%e5%8f%8d%e8%bd%ac%e9%93%be%e8%a1%a8)
    - [面试题25 合并两个排序的链表](#%e9%9d%a2%e8%af%95%e9%a2%9825-%e5%90%88%e5%b9%b6%e4%b8%a4%e4%b8%aa%e6%8e%92%e5%ba%8f%e7%9a%84%e9%93%be%e8%a1%a8)
    - [面试题26 树的子结构](#%e9%9d%a2%e8%af%95%e9%a2%9826-%e6%a0%91%e7%9a%84%e5%ad%90%e7%bb%93%e6%9e%84)
  - [第四章](#%e7%ac%ac%e5%9b%9b%e7%ab%a0)
    - [面试题27 二叉树的镜像](#%e9%9d%a2%e8%af%95%e9%a2%9827-%e4%ba%8c%e5%8f%89%e6%a0%91%e7%9a%84%e9%95%9c%e5%83%8f)
    - [面试题28 对称的二叉树](#%e9%9d%a2%e8%af%95%e9%a2%9828-%e5%af%b9%e7%a7%b0%e7%9a%84%e4%ba%8c%e5%8f%89%e6%a0%91)
    - [面试题29 顺时针打印矩阵](#%e9%9d%a2%e8%af%95%e9%a2%9829-%e9%a1%ba%e6%97%b6%e9%92%88%e6%89%93%e5%8d%b0%e7%9f%a9%e9%98%b5)
    - [面试题30 包含min函数的栈](#%e9%9d%a2%e8%af%95%e9%a2%9830-%e5%8c%85%e5%90%abmin%e5%87%bd%e6%95%b0%e7%9a%84%e6%a0%88)
    - [面试题31 栈的压入、弹出序列](#%e9%9d%a2%e8%af%95%e9%a2%9831-%e6%a0%88%e7%9a%84%e5%8e%8b%e5%85%a5%e5%bc%b9%e5%87%ba%e5%ba%8f%e5%88%97)
    - [面试题32 从上往下打印二叉树](#%e9%9d%a2%e8%af%95%e9%a2%9832-%e4%bb%8e%e4%b8%8a%e5%be%80%e4%b8%8b%e6%89%93%e5%8d%b0%e4%ba%8c%e5%8f%89%e6%a0%91)
    - [面试题33 二叉搜索树的后序遍历序列](#%e9%9d%a2%e8%af%95%e9%a2%9833-%e4%ba%8c%e5%8f%89%e6%90%9c%e7%b4%a2%e6%a0%91%e7%9a%84%e5%90%8e%e5%ba%8f%e9%81%8d%e5%8e%86%e5%ba%8f%e5%88%97)
    - [面试题34 二叉树中和为某一值的路径](#%e9%9d%a2%e8%af%95%e9%a2%9834-%e4%ba%8c%e5%8f%89%e6%a0%91%e4%b8%ad%e5%92%8c%e4%b8%ba%e6%9f%90%e4%b8%80%e5%80%bc%e7%9a%84%e8%b7%af%e5%be%84)
    - [面试题35 复杂链表的复刻](#%e9%9d%a2%e8%af%95%e9%a2%9835-%e5%a4%8d%e6%9d%82%e9%93%be%e8%a1%a8%e7%9a%84%e5%a4%8d%e5%88%bb)
    - [面试题36 二叉搜索树与双向链表](#%e9%9d%a2%e8%af%95%e9%a2%9836-%e4%ba%8c%e5%8f%89%e6%90%9c%e7%b4%a2%e6%a0%91%e4%b8%8e%e5%8f%8c%e5%90%91%e9%93%be%e8%a1%a8)
    - [面试题37 序列化二叉树](#%e9%9d%a2%e8%af%95%e9%a2%9837-%e5%ba%8f%e5%88%97%e5%8c%96%e4%ba%8c%e5%8f%89%e6%a0%91)
    - [面试题38 字符串的排列](#%e9%9d%a2%e8%af%95%e9%a2%9838-%e5%ad%97%e7%ac%a6%e4%b8%b2%e7%9a%84%e6%8e%92%e5%88%97)
  - [第五章](#%e7%ac%ac%e4%ba%94%e7%ab%a0)
    - [面试题39 数组中出现次数超过一半的数字](#%e9%9d%a2%e8%af%95%e9%a2%9839-%e6%95%b0%e7%bb%84%e4%b8%ad%e5%87%ba%e7%8e%b0%e6%ac%a1%e6%95%b0%e8%b6%85%e8%bf%87%e4%b8%80%e5%8d%8a%e7%9a%84%e6%95%b0%e5%ad%97)
    - [面试题40 最小的k个数](#%e9%9d%a2%e8%af%95%e9%a2%9840-%e6%9c%80%e5%b0%8f%e7%9a%84k%e4%b8%aa%e6%95%b0)
    - [面试题41 数据流中的中位数](#%e9%9d%a2%e8%af%95%e9%a2%9841-%e6%95%b0%e6%8d%ae%e6%b5%81%e4%b8%ad%e7%9a%84%e4%b8%ad%e4%bd%8d%e6%95%b0)
    - [面试题42 连续子数组的最大和](#%e9%9d%a2%e8%af%95%e9%a2%9842-%e8%bf%9e%e7%bb%ad%e5%ad%90%e6%95%b0%e7%bb%84%e7%9a%84%e6%9c%80%e5%a4%a7%e5%92%8c)
    - [面试题43 从1到n整数中1出现的次数](#%e9%9d%a2%e8%af%95%e9%a2%9843-%e4%bb%8e1%e5%88%b0n%e6%95%b4%e6%95%b0%e4%b8%ad1%e5%87%ba%e7%8e%b0%e7%9a%84%e6%ac%a1%e6%95%b0)
    - [面试题44 数字序列中某一位的数字](#%e9%9d%a2%e8%af%95%e9%a2%9844-%e6%95%b0%e5%ad%97%e5%ba%8f%e5%88%97%e4%b8%ad%e6%9f%90%e4%b8%80%e4%bd%8d%e7%9a%84%e6%95%b0%e5%ad%97)
    - [面试题45 把数组排成最小的数](#%e9%9d%a2%e8%af%95%e9%a2%9845-%e6%8a%8a%e6%95%b0%e7%bb%84%e6%8e%92%e6%88%90%e6%9c%80%e5%b0%8f%e7%9a%84%e6%95%b0)
    - [面试题46 把数字翻译成字符串](#%e9%9d%a2%e8%af%95%e9%a2%9846-%e6%8a%8a%e6%95%b0%e5%ad%97%e7%bf%bb%e8%af%91%e6%88%90%e5%ad%97%e7%ac%a6%e4%b8%b2)
    - [面试题48 礼物的最大价值](#%e9%9d%a2%e8%af%95%e9%a2%9848-%e7%a4%bc%e7%89%a9%e7%9a%84%e6%9c%80%e5%a4%a7%e4%bb%b7%e5%80%bc)
    - [面试题48 最长不含重复字符的子字符串](#%e9%9d%a2%e8%af%95%e9%a2%9848-%e6%9c%80%e9%95%bf%e4%b8%8d%e5%90%ab%e9%87%8d%e5%a4%8d%e5%ad%97%e7%ac%a6%e7%9a%84%e5%ad%90%e5%ad%97%e7%ac%a6%e4%b8%b2)
    - [面试题49 丑数](#%e9%9d%a2%e8%af%95%e9%a2%9849-%e4%b8%91%e6%95%b0)
    - [面试题50 第一个只出现一次的字符](#%e9%9d%a2%e8%af%95%e9%a2%9850-%e7%ac%ac%e4%b8%80%e4%b8%aa%e5%8f%aa%e5%87%ba%e7%8e%b0%e4%b8%80%e6%ac%a1%e7%9a%84%e5%ad%97%e7%ac%a6)
      - [题目1 字符串中第一个只出现一次的字符](#%e9%a2%98%e7%9b%ae1-%e5%ad%97%e7%ac%a6%e4%b8%b2%e4%b8%ad%e7%ac%ac%e4%b8%80%e4%b8%aa%e5%8f%aa%e5%87%ba%e7%8e%b0%e4%b8%80%e6%ac%a1%e7%9a%84%e5%ad%97%e7%ac%a6)
      - [题目2 字符流中第一个只出现一次的字符](#%e9%a2%98%e7%9b%ae2-%e5%ad%97%e7%ac%a6%e6%b5%81%e4%b8%ad%e7%ac%ac%e4%b8%80%e4%b8%aa%e5%8f%aa%e5%87%ba%e7%8e%b0%e4%b8%80%e6%ac%a1%e7%9a%84%e5%ad%97%e7%ac%a6)
    - [面试题51 数组中的逆序对](#%e9%9d%a2%e8%af%95%e9%a2%9851-%e6%95%b0%e7%bb%84%e4%b8%ad%e7%9a%84%e9%80%86%e5%ba%8f%e5%af%b9)
    - [面试题51 两个链表的第一个公共结点](#%e9%9d%a2%e8%af%95%e9%a2%9851-%e4%b8%a4%e4%b8%aa%e9%93%be%e8%a1%a8%e7%9a%84%e7%ac%ac%e4%b8%80%e4%b8%aa%e5%85%ac%e5%85%b1%e7%bb%93%e7%82%b9)
    - [面试题53 数字在排序数组中出现的次数](#%e9%9d%a2%e8%af%95%e9%a2%9853-%e6%95%b0%e5%ad%97%e5%9c%a8%e6%8e%92%e5%ba%8f%e6%95%b0%e7%bb%84%e4%b8%ad%e5%87%ba%e7%8e%b0%e7%9a%84%e6%ac%a1%e6%95%b0)
    - [面试题54 二叉搜索树的第k个结点](#%e9%9d%a2%e8%af%95%e9%a2%9854-%e4%ba%8c%e5%8f%89%e6%90%9c%e7%b4%a2%e6%a0%91%e7%9a%84%e7%ac%ack%e4%b8%aa%e7%bb%93%e7%82%b9)
    - [面试题55 二叉树的深度](#%e9%9d%a2%e8%af%95%e9%a2%9855-%e4%ba%8c%e5%8f%89%e6%a0%91%e7%9a%84%e6%b7%b1%e5%ba%a6)
    - [面试题56 数组中数字的出现次数****](#%e9%9d%a2%e8%af%95%e9%a2%9856-%e6%95%b0%e7%bb%84%e4%b8%ad%e6%95%b0%e5%ad%97%e7%9a%84%e5%87%ba%e7%8e%b0%e6%ac%a1%e6%95%b0)
      - [数组中只出现一次的两个数字](#%e6%95%b0%e7%bb%84%e4%b8%ad%e5%8f%aa%e5%87%ba%e7%8e%b0%e4%b8%80%e6%ac%a1%e7%9a%84%e4%b8%a4%e4%b8%aa%e6%95%b0%e5%ad%97)
      - [数组中唯一只出现一次的数字](#%e6%95%b0%e7%bb%84%e4%b8%ad%e5%94%af%e4%b8%80%e5%8f%aa%e5%87%ba%e7%8e%b0%e4%b8%80%e6%ac%a1%e7%9a%84%e6%95%b0%e5%ad%97)
    - [面试题57 和为S的数字](#%e9%9d%a2%e8%af%95%e9%a2%9857-%e5%92%8c%e4%b8%bas%e7%9a%84%e6%95%b0%e5%ad%97)
      - [和为S的两个数字(2-SUM问题)](#%e5%92%8c%e4%b8%bas%e7%9a%84%e4%b8%a4%e4%b8%aa%e6%95%b0%e5%ad%972-sum%e9%97%ae%e9%a2%98)
      - [和为S的连续正数序列](#%e5%92%8c%e4%b8%bas%e7%9a%84%e8%bf%9e%e7%bb%ad%e6%ad%a3%e6%95%b0%e5%ba%8f%e5%88%97)
    - [面试题58 翻转字符串](#%e9%9d%a2%e8%af%95%e9%a2%9858-%e7%bf%bb%e8%bd%ac%e5%ad%97%e7%ac%a6%e4%b8%b2)
    - [面试题59 队列的最大值](#%e9%9d%a2%e8%af%95%e9%a2%9859-%e9%98%9f%e5%88%97%e7%9a%84%e6%9c%80%e5%a4%a7%e5%80%bc)
      - [滑动窗口的最大值](#%e6%bb%91%e5%8a%a8%e7%aa%97%e5%8f%a3%e7%9a%84%e6%9c%80%e5%a4%a7%e5%80%bc)
    - [面试题60 n个骰子的点数](#%e9%9d%a2%e8%af%95%e9%a2%9860-n%e4%b8%aa%e9%aa%b0%e5%ad%90%e7%9a%84%e7%82%b9%e6%95%b0)
    - [面试题61 扑克中的顺子](#%e9%9d%a2%e8%af%95%e9%a2%9861-%e6%89%91%e5%85%8b%e4%b8%ad%e7%9a%84%e9%a1%ba%e5%ad%90)
    - [面试题62 圆圈中最后剩下的数字***](#%e9%9d%a2%e8%af%95%e9%a2%9862-%e5%9c%86%e5%9c%88%e4%b8%ad%e6%9c%80%e5%90%8e%e5%89%a9%e4%b8%8b%e7%9a%84%e6%95%b0%e5%ad%97)
    - [面试题63 股票的最大利润](#%e9%9d%a2%e8%af%95%e9%a2%9863-%e8%82%a1%e7%a5%a8%e7%9a%84%e6%9c%80%e5%a4%a7%e5%88%a9%e6%b6%a6)
    - [面试题65 不用加减乘除做加法](#%e9%9d%a2%e8%af%95%e9%a2%9865-%e4%b8%8d%e7%94%a8%e5%8a%a0%e5%87%8f%e4%b9%98%e9%99%a4%e5%81%9a%e5%8a%a0%e6%b3%95)
    - [面试题66 构建乘积数组](#%e9%9d%a2%e8%af%95%e9%a2%9866-%e6%9e%84%e5%bb%ba%e4%b9%98%e7%a7%af%e6%95%b0%e7%bb%84)
    - [面试题67 把字符串转化为整数](#%e9%9d%a2%e8%af%95%e9%a2%9867-%e6%8a%8a%e5%ad%97%e7%ac%a6%e4%b8%b2%e8%bd%ac%e5%8c%96%e4%b8%ba%e6%95%b4%e6%95%b0)
    - [面试题68 树中两个节点的最低公共祖先](#%e9%9d%a2%e8%af%95%e9%a2%9868-%e6%a0%91%e4%b8%ad%e4%b8%a4%e4%b8%aa%e8%8a%82%e7%82%b9%e7%9a%84%e6%9c%80%e4%bd%8e%e5%85%ac%e5%85%b1%e7%a5%96%e5%85%88)
    - [57 0到n-1中缺失的数字](#57-0%e5%88%b0n-1%e4%b8%ad%e7%bc%ba%e5%a4%b1%e7%9a%84%e6%95%b0%e5%ad%97)
    - [58 数组中数值和下标相等的元素](#58-%e6%95%b0%e7%bb%84%e4%b8%ad%e6%95%b0%e5%80%bc%e5%92%8c%e4%b8%8b%e6%a0%87%e7%9b%b8%e7%ad%89%e7%9a%84%e5%85%83%e7%b4%a0)

## 语法Tips
- 取中位的操作可以用位运算代替除2, `mid = (start+end) >> 1;`, 注意右移是1位
- `String.replace()`方法和`String.replaceAll()`方法的区别, 前者是将旧字符串替换成新的字符串, 后者是将符合**正则表达式**的字符串替换成新的字符串, 后者的字符串会先进行转义. 前者的底层用的也是`replaceAll`
- 运行效率上`StringBuilder`> `StringBuffer`, 但是`StringBuffer`是线程安全的, 而`StringBuilder`不是.
- `Arrays.toList`方法返回一个`List`, 其底层的Array就是传入的参数, 因此对List的操作都会映射到底层的Array上.
- `String.split`方法返回的是数组, 会把`regex`的部分给消费掉.
- 复制Array的方法不需要用for语句, 可以用`System.ArrayCopy`
- `List.toArray`方法当`T[]`的大小小于size时, 会创建一个新的array返还回去
- `Queue`只用`add()`和`remove()`方法, 加在尾上和从头上去掉
- `List`没有`remove()`方法, 只有带`index`的方法, `add`方法也在尾上添加
- link版本的和array版本的queue分别是`ArrayDeque`和`LinkedList`
- 注意`int[]`转到`List<Integer>` 除了流的`boxed`方法, 就只有用循环处理, 通常也是用后者
## 第二章
### 面试题3 数组查找重复数字
题目: [Acwing](https://www.acwing.com/problem/content/14/)

思路: (适合数组找重复)

- hash: 时间O(N), 空间O(N)
- 交换: 总是将当前元素交换到下标对应位置, 时间O(N), 空间O(1), 问题: 需要修改数组
- 排序: 时间O(nlogn), 空间O(1), 需要修改数组
- 二分搜索数组中1-n区间上的元素个数, 总有大于区间大小的区间, 时间O(nlogN), 空间O(1), 不修改数组 **不能找到所有的重复元素**

```java
// 边界条件: [], [2], [-1], [0, 1], [1, 1]
// 思路: 将元素与下标对应, 不对应的进行交换, 时间复杂度O(N) 空间复杂度O(1)
class Solution {
    /**
     * 每次将当前位置的元素安排到和元素对应的下标位置
     * @param nums
     * @return 
     */
    public int duplicateInArray(int[] nums) {
        if (nums == null || nums.length == 0) return -1;
        for (int a: nums) {
            if (a < 0 || a >= nums.length) return -1;
        }
        for (int i = 0; i < nums.length; i++) {
            while (nums[i] != i) {
                if (nums[nums[i]] == nums[i]) return nums[i];
                int temp = nums[i];
                nums[i] = nums[temp];
                nums[temp] = temp;
            }
        }
        return -1;
    }
}
```

#### 问题扩展: 不修改数组找出重复数字

题目: [Acwing](https://www.acwing.com/problem/content/15/)
- [ ] 独立&&完美
```java
// 题目变化: n+1长的数组, 元素位于1-n, 必定有重复, 不能修改元素
// 边界条件: [], [1, 1, 2], [1, 1, 3, 3]
// 思路: 暴力法: 对于每个元素, 遍历之后的元素看是否有和它相同的元素, 复杂度是O(N). 利用到元素都是位于1-n的条件, 1-n/2范围或n/2-n范围的数的个数一定会超过一半. 因此, 可以对范围二分, 复杂度变为O(NlogN)

class Solution {
    public int duplicateInArray(int[] nums) {
        if (nums == null || nums.length == 0) return -1;
        int start = 1;
        int end = nums.length-1;
        while (start <= end) {
            int mid = (start + end) >> 1;
            if (getCount(nums, start, mid) <= (mid - start + 1)) start = mid + 1;
            else end = mid;
        }
        return start;
    }
    int getCount(int[] nums, int start, int end) {
        int cnt = 0;
        for (int a: nums) {
            if (a >= start && a <= end) cnt++;
        }
        return cnt;
    }
}
```

### 面试题4 二维数组的查找
题目:[Acwing](https://www.acwing.com/problem/content/16/)

- 思路: 暴力法遍历O(m*n), 那么是否能够一次比较排除多个? 因为是有序的, 考虑二分查找, 但是二分查找会将矩阵分成3块, 并且还有两块是有重叠的, 很不好处理. 但是, 对于右上角的这个元素, 其左边的都比它小, 其下方的都比它大, 因此, 可以利用它, 每次用target和右上角的元素比较, 如果比它大, 递归的对其下方的二维矩阵查找, 否则递归的对其左边的二维矩阵查找.

```java
class Solution {
    public boolean searchArray(int[][] array, int target) {
        if (array == null || array.length < 1) 
            return false;
        
        int rlen = array.length;
        int clen = array[0].length;
        int row = 0, col = clen - 1;
        while(row < rlen && col >= 0) { // 从右上角往左下角搜索
            int current = array[row][col];
            if (current > target) col--;
            else if (current < target) row++;
            else return true;
        }
        return false;
    }
}
```

### 面试题5 替换空格
题目: [Acwing](https://www.acwing.com/problem/content/description/17/)

```java
// 使用库函数
class Solution {
    public String replaceSpaces(StringBuffer str) {
        return str.toString().replaceAll(" ", "%20");
    }
}
// 不使用库函数
// 思路: 第一遍遍历找到有多少个空格, 第二遍从尾部往前遍历, 遇到空格进行替换. 这样的做法能够避免频繁的移动元素.
class Solution {
    public String replaceSpaces(StringBuffer str) {
        if (str == null || str.length() == 0) return new String();
        int cnt = 0;
        for (int i = 0; i < str.length(); i++) {
            if (str.charAt(i) == ' ') cnt++;
        }
        char[] charArray = new char[str.length()+cnt*2];
        int indexC = charArray.length-1, indexS = str.length()-1;
        while (indexC >= 0) {
            if (str.charAt(indexS) == ' ') {
                charArray[indexC--] = '0';
                charArray[indexC--] = '2';
                charArray[indexC] = '%';
            }
            else charArray[indexC] = str.charAt(indexS);
            indexC--;
            indexS--;
        }
        return new String(charArray);
    }
}
```

**思路扩展：**

在将一个数组合并到另一个数组（包括字符串）时，如果从前往后复制每个数字（或字符）需要重复移动数字（或字符）多次，那么我们可以考虑**从后往前**复制，这样就能减少移动的次数，从而提高效率。

### 面试题6 从尾到头打印链表
题目: [Acwing](https://www.acwing.com/problem/content/18/)

思路: 链表不支持随机访问, 常规的顺序是从头到尾的, 要求从尾到头有两种基本的思路, 用栈, 或用递归. 还有一种可以通过修改链表结构将整个链表翻转得到从头到尾的访问顺序.(修改了结构)

```java
class Solution {
    public int[] printListReversingly(ListNode head) {
        if (head == null) return new int[0];
        Stack<Integer> s = new Stack<>();
        while (head != null) {
            s.push(head.val);
            head = head.next;
        }
        int[] result = new int[s.size()];
        for (int i = 0; i < result.length; i++) {
            result[i] = s.pop();
        }
        return result;
    }
}
```

### 面试题7 重建二叉树
题目: [Acwing](https://www.acwing.com/problem/content/23/)

```java
// 思路: 必须要有中序, 此外需要有一个前序或后序, 才可以唯一还原一个二叉树
// 边界条件: 完全二叉树, 不完全二叉树, 空树, 只有一个根节点树, 一边为空的树,

class Solution {
    public TreeNode buildTree(int[] preorder, int[] inorder) {
        TreeNode root = build(preorder, inorder, 0, preorder.length - 1, 0, inorder.length - 1);
        return root;
    }
    private TreeNode build(int[] pre, int[] in, int preBegin, int preEnd, int inBegin, int inEnd) {
        if (preBegin > preEnd || preBegin < 0) return null;
        TreeNode root = new TreeNode(pre[preBegin]);
        int rootId = inBegin;
        for (; rootId <= inEnd; rootId++) {
            if (in[rootId] == pre[preBegin]) break;
        }
        root.left = build(pre, in, preBegin + 1, preBegin + rootId - inBegin, inBegin, rootId - 1);
        root.right = build(pre, in, preBegin + rootId - inBegin + 1, preEnd, rootId + 1, inEnd);
        return root;
    }
}
```

### 面试题8 二叉树的下一个节点 
题目: [Acwing](https://www.acwing.com/problem/content/31/)

```java
// 边界条件: 空树;有右儿子,右儿子是叶节点; 有右儿子, 右儿子不是叶节点; 无右儿子, 自己是左节点; 无右儿子, 自己是右节点; 自己是最后一个节点
public class Solution {
    public TreeLinkNode GetNext(TreeLinkNode pNode)
    {
        if (pNode == null) return null;
        TreeLinkNode result = null;
        if (pNode.right == null) {
            while (pNode.next != null && pNode.next.right == pNode) {pNode = pNode.next;}
            if (pNode.next != null) result = pNode.next;
        }
        else {
            pNode = pNode.right;
            while (pNode.left != null) pNode = pNode.left;
            result = pNode;
        }
        return result;
    }
}
```

### 面试题9 用两个栈实现队列

扩展: 用两个队列模拟一个栈, 压入n个元素后, pop出最后一个元素的方法是将前n-1个pop到另外一个栈中

```java
class MyQueue {
    Stack<Integer> s1, s2;

    /** Initialize your data structure here. */
    public MyQueue() {
        s1 = new Stack<Integer>();
        s2 = new Stack<Integer>();
    }
    
    /** Push element x to the back of queue. */
    public void push(int x) {
        s1.push(x);
    }
    
    /** Removes the element from in front of queue and returns that element. */
    public int pop() {
        if (s2.empty()) flush();
        return s2.pop();
    }
    
    /** Get the front element. */
    public int peek() {
        if (s2.empty()) flush();
        return s2.peek();
    }
    
    /** Returns whether the queue is empty. */
    public boolean empty() {
        return s1.empty() && s2.empty();
    }

    private void flush() {
        assert s2.empty() == true;
        while (!s1.empty()) {
            s2.push(s1.pop());
        }
    }
}
```

### 面试题10 斐波那契数列
题目: [Acwing](https://www.acwing.com/problem/content/19/)

思路1 N用两个变量通过循环得到(实用)

```java
class Solution {
    public int Fibonacci(int n) {
         if (n == 0 || n == 1) return n;
         int n0 = 0, n1 = 1;
         while(n >= 2) {
             int temp = n0 + n1;
             n0 = n1;
             n1 = temp;
             n--;
         }
         return n1;
    }
}
```
思路2 (logN 利用公式
$$
 \left[
 \begin{matrix}
   f(n) & f(n-1) \\
   f(n-1) & f(n-2) 
  \end{matrix}
  \right] = 
   \left[
 \begin{matrix}
   1 & 1 \\
   1 & 0 
  \end{matrix}
  \right]^{n-1} 
$$
而乘方的计算不用按照一遍一遍的乘, 而是利用$a^n=a^{n/2}\cdot a^{n/2}$计算

> 本题扩展: 青蛙跳台问题可以建模成$f(n) = f(n-1) + f(n-2)$, 因此就是斐波那契数列问题; 当问题变为青蛙一次可以跳1级,也可以跳2级,...,也可以跳n级时, $f(n)=2^{n-1}$(数学归纳法可证)

### 面试题11 旋转数组的最小数字

思路: 基本的想法是n, 然后添加一些条件使得小于O(n), O(n)的算法没有抓住旋转数组有序的根本特点, 就是分为两个有序子列, 第一个元素通常大于等于最后一个元素, 从这一点出发可以根据二分法构造更快的算法, 但是要考虑边界条件, 如果第一个和最后一个以及中点相等时, 按照算法会将id1一道中点, 但是事实上没法判断例如{1, 1, 0, 1, 1, 1}和{1, 1, 1, 1 ,0, 1}的两种情况的差别. 因此这种时候要退化为O(n)

```java
class Solution {
    public int findMin(int[] nums) {
        if (nums == null || nums.length == 0) return -1;
        int id1 = 0, id2 = nums.length - 1;
        int mid = (id1 + id2) / 2;
        if (nums[id1] < nums[id2]) return nums[id1];
        if (nums[mid] == nums[id1] && nums[mid] == nums[id2]) {
            int min = Integer.MAX_VALUE;
            for (int a : nums) {
                if (a < min) min = a;
            }
            return min;
        }
        while (id1 < id2-1) {
            mid = (id1 + id2) / 2;
            if (nums[id1] <= nums[mid]) id1 = mid;
            else id2 = mid;
        }
        return nums[id2];
    }
}
```

### 面试题12 矩阵中的路径
- [ ] 独立&&完美

- 思路: 经典的dfs变种问题
- 边界条件: 空 只有一行一列, 所有字符相同
```java
public class Solution {
    private boolean[] visit;
    public boolean hasPath(char[] matrix, int rows, int cols, char[] str)
    {
        if (matrix == null || matrix.length == 0) return false;
        if (str == null ) return false;
        if (str.length == 0) return true;
        visit = new boolean[matrix.length];
        for (int i = 0; i < matrix.length; i++)
            if (dfs(matrix, rows, cols, i, str, 0)) return true;
        return false;
    }
    boolean dfs(char[] matrix, int rows, int cols, int pos, char[] str, int index) {
        if (visit[pos] || matrix[pos] != str[index]) return false;
        if (index == str.length-1) return true;
        // 边界条件1,1的矩阵, 必须判断len-1而不能往下一步到length的时候直接返回true
        visit[pos] = true;
        boolean result = false;
        int row = pos / cols, col = pos % cols;
        if (row < rows-1 && dfs(matrix, rows, cols, pos + cols, str, index + 1)) result = true;
        else if (row > 0 && dfs(matrix, rows, cols, pos - cols, str, index + 1)) result = true;
        else if (col > 0 && dfs(matrix, rows, cols, pos-1, str, index + 1)) result = true;
        else if (col < cols - 1 && dfs(matrix, rows, cols, pos + 1, str, index + 1)) result = true;
        visit[pos] = false;
        return result;
    }
}
```

### 面试题13 机器人的运动范围
题目: [Acwing](https://www.acwing.com/problem/content/22/)

思路: 经典的dfs变种问题

```java
public class Solution {
    public int movingCount(int threshold, int rows, int cols)
    {
        boolean[] visit = new boolean[rows * cols];
        int cnt = movingCore(visit, threshold, rows, cols, 0, 0);
        return cnt;
    }
    private int movingCore(boolean[] visit, int threshold, 
                           int rows, int cols, int row, int col) {
        if (row >= 0 && row < rows && col >= 0 && col < cols
           && !visit[row * cols + col] && ableToVisit(threshold, row, col)) {
            int cnt = 1;
            visit[row * cols + col] = true;
            cnt += movingCore(visit, threshold, rows, cols, row+1, col)
                + movingCore(visit, threshold, rows, cols, row-1, col)
                + movingCore(visit, threshold, rows, cols, row, col+1)
                + movingCore(visit, threshold, rows, cols, row, col-1);
            return cnt;
        }
        else return 0;
    }
    private boolean ableToVisit(int threshold, int row, int col) {
        int sum = 0;
        while (row > 0) {
            sum += row % 10;
            row /= 10;
        }
        while (col > 0) {
            sum += col % 10;
            col /= 10;
        }
        return sum <= threshold;
    }
}
```

### 面试题14 剪绳子
题目: [Acwing](https://www.acwing.com/problem/content/24/)

思路: 动态规划问题, 紧扣动态规划的两个特性: 重叠子问题和最佳子结构. 最佳子结构是剪出来的子绳子的最大值, 是自己或自己的剪绳子问题, 重叠子问题是指,求绳子的最大值是求绳子拆成两部分后两部分的最大值问题, 然后相乘

```java
public class Solution {
    public int cutRope(int target) {
        int[] table = new int[61];
        table[1] = 1; table[2] = 1;
        if (target < 2) return 0;
        return calMax(target, table);
    }
    private int calMax(int target, int[] table) {
        if (table[target] == 0) {
            int max = Integer.MIN_VALUE;
            for (int i = 1; i <= target / 2; i++) {
                int a = Math.max(i, calMax(i, table));
                int b = Math.max(target - i, calMax(i, table));
                max = Math.max(max, a * b);
            }
            table[target] = max;
        }
        return table[target];
    }
}
```

### 面试题15 二进制中1的个数

- [ ] 独立&&完美

这道题体现出基础不扎实和语法不扎实, 补充知识点:
- 原码: 正数的正常表示, 首位为0
- 反码: 将所有位取反
- 补码: 负数的表示是对应的正数取反后加1
- 因此, 补码中的[-1] = 11111111111111..11
- Java语法中, 位运算: & | ~ ^ 分别对应了与或非异或, >> 算术右移, >>> 逻辑右移

算法: 最朴实的算法是对n不断和1做与运算, 然后逻辑右移(也可以将1左移), 更加惊艳的算法利用到了一个性质, n-1的二进制表示是n的二进制表示的右侧第一个1变为0, 其右边的所有0变为1, 左边不变;则n与n-1做与运算得到的效果就是, 将n的最右边的一个1变成0;这样的好处是, 循环只进行cnt次, cnt是含有的1的数量.

```java
// 更快的方法 每次得到最右的第一个1
public class Solution {
    public int NumberOf1(int n) {
        int cnt = 0;
        while (n != 0) {
            n = (n-1) & n;
            cnt++;
        }
        return cnt;
    }
}
```

## 第三章
### 面试题16 数值的整数次方
题目:[Acwing](https://www.acwing.com/problem/content/26/)
- 思路: exponent的二进制表示可以表示成例如`exponent=6=1*2^2+1*2^1+0*2^0`, 因此`pow(base, exp) = base^(2^2)*base^(2^1)*1`, 而`base^(2^2) = (base^(2^1))*(base^(2^1))`, 因此可以写成遍历`exponent`的二进制表示, 每左移一位, $base_{new}=base*base$.
- 边界条件: base为0, base为正/负, exp为0, exponent为正/负

```java
public class Solution {
    public double Power(double base, int exponent) {
        if (base == 0) return 0;
        if (exponent == 0) return 1;
        else if (exponent < 0) return 1 / Power(base, -exponent);
        double result = 1;
        int bitmask = 1;
        while (bitmask != 0) {
            if ((exponent & bitmask) != 0) {
                result *= base;
            }
            base *= base;
            bitmask <<= 1;
        }
        return result;
  }
}
```

### 面试题 17 打印1到最大的n位数
题目: 打印从1到最大的n位数

- 边界条件: n位数超过10,即超过了Integer甚至long的最大值; 小于n位时, 前面没有0
- 思路: 递归全排列
```java
class Solution {
    public void print1ToN(int n) {
        char[] str = new char[n];
        Arrays.fill(str, '0');
        printCore(str, 0);
    }
    private void printCore(char[] str, int index) {
        if (index >= str.length) return ;
        for (int i = 0; i < 10; i++) {
            str[index] = (char)('0' + i);
            if (index == str.length-1) {
                printCharToInt(str);
            }
            else printCore(str, index + 1);
        }
    }
    private void printCharToInt(char[] str) {
        int index = 0;
        while (index < str.length && str[index] == '0') index++;
        if (index == str.length) System.out.println('0');
        else System.out.println(new String(str, index, str.length-index));
    }
}
```

### 面试题18 删除链表中的结点
#### 题目1 O(1)时间删除链表中的节点
题目:[Acwing](https://www.acwing.com/problem/content/85/)

思路: 原题还需要考虑是否是尾节点的情况, 如果是尾节点则依然要顺序遍历

```java
class Solution {
    public void deleteNode(ListNode node) {
        node.val = node.next.val;
        node.next = node.next.next;
    }
}
```

#### 题目2 删除链表中的重复节点
题目:[Acwing](https://www.acwing.com/problem/content/27/)
边界条件: 全部重复, 全部不重复, 头结点对应的数重复
思路: 重复子问题, 找到一个子链表的第一个不重复的节点
```java
public class Solution {
    public ListNode deleteDuplication(ListNode pHead)
    {
        pHead = findFirstSingle(pHead);
        if (pHead != null) {
            ListNode cur = pHead, next;
            while ((next = findFirstSingle(cur.next)) != null) {
                cur.next = next;
                cur = next;
            }
            cur.next = null;
        }
        return pHead;
    }
    private ListNode findFirstSingle(ListNode head) {
        if (head == null) return null;
        while (head != null) {
            ListNode ptr = head;
            while ((ptr = ptr.next) != null && ptr.val == head.val);
            if (ptr == head.next) break;
            head = ptr;
        }
        return head;
    }
}
```

### 面试题19 正则表达式匹配
- [ ] 独立&&完美

思路: 用逻辑或和递归构造LSA, 遍历所有可能的情况
边界条件: ("a", "", false), ("","",true), ("", "a*", true), ("a", "a*a", true), ("adsbd", ".*", true) 

```java
public class Solution {
    public boolean match(char[] str, char[] pattern)
    {
        if (str == null || pattern == null) return false;
        return matchCore(str, pattern, 0, 0);
    }
    private boolean matchCore(char[] str, char[] pattern, int sIndex, int pIndex) {
        if (pIndex >= pattern.length) return sIndex == str.length;
        if (pIndex + 1 < pattern.length && pattern[pIndex+1] == '*') {
            if (sIndex >= str.length) return matchCore(str, pattern, sIndex, pIndex+2);
            if (pattern[pIndex] == '.' || str[sIndex] == pattern[pIndex]) 
                return matchCore(str, pattern, sIndex+1, pIndex) // 匹配当前 继续匹配 
                || matchCore(str, pattern, sIndex+1, pIndex + 2) // 匹配当前 完成*
                || matchCore(str, pattern, sIndex, pIndex + 2); // *匹配0次
            else return matchCore(str, pattern, sIndex, pIndex + 2); // 匹配0次
        }
        else {
            if (sIndex >= str.length) return false;
            if (pattern[pIndex] == '.' ||str[sIndex] == pattern[pIndex])
                return matchCore(str, pattern, sIndex + 1, pIndex+1);
            else return false;
        }
    }
}
```

### 面试题20 表示数值的字符串

思路: 将问题拆分到判断一个自字符串是否为整数
```java
// 正则方法
public class Solution {
    public boolean isNumeric(char[] str) {
        String s = new String(str);
        return s.matches("[+-]?((\\d+(\\.\\d*)?)|(\\.\\d+))([eE][+-]?[0-9]+)?");
    }
}
// 普通方法
class Solution {
    public boolean isNumber(String s) {
        int eIndex = s.indexOf('e');
        if (eIndex == -1) eIndex = s.indexOf('E');
        if (eIndex != -1) return isFloat(s, 0, eIndex-1) && isInteger(s, eIndex + 1, s.length()-1, true);
        return isFloat(s, 0, s.length()-1);
    }
    private boolean isInteger(String s, int begin, int end, boolean useSign) {
        System.out.println(s.substring(begin, end+1));
        if (begin > end) return false;
        if (useSign && (s.charAt(begin) == '+' || s.charAt(begin) == '-')) begin ++;
        for (int i = begin; i<= end; i++) {
            if (s.charAt(i) < '0' || s.charAt(i) > '9') return false;
        } 
        return true;
    }
    private boolean isFloat(String s, int begin, int end) {
        if (begin > end) return false;
        int pointIndex = s.indexOf('.', begin);
        if (pointIndex == -1 || pointIndex > end) return isInteger(s, begin, end, true);
        else {
            if (s.charAt(begin) == '+' || s.charAt(begin) == '-') begin++;
            if (pointIndex == begin) return isInteger(s, pointIndex+1, end, false);
            if (pointIndex == end) return isInteger(s, begin, end-1, false);
            return isInteger(s, begin, pointIndex-1, false) && isInteger(s, pointIndex+1, end, false);
        }
    }
}
```

### 面试题21 调整数组顺序使奇数位于偶数前面
题目: [Acwing](https://www.acwing.com/problem/content/30/)

边界条件: 全偶数 全奇数 空
```java
class Solution {
    public void reOrderArray(int [] array) {
        if (array == null || array.length == 0) return ;
        int oddPtr = 0, evenPtr = array.length-1;
        while (oddPtr < evenPtr) {
            while (oddPtr < array.length && (array[oddPtr] & 1) == 1) oddPtr++;
            while (evenPtr >= 0 && (array[evenPtr] & 1) == 0) evenPtr--;
            if (oddPtr < evenPtr) {
                int temp = array[oddPtr];
                array[oddPtr++] = array[evenPtr];
                array[evenPtr--] = temp;
            }
        }
    }
}
```

### 面试题22 链表中倒数第k个节点
题目: [Acwing](https://www.acwing.com/problem/content/32/)

- 边界条件: 链表长度小于k, k为1 k为0 k为1同时链表长度为1
- 思路: 链表经典思路, 快慢指针
```java
public class Solution {
    public ListNode FindKthToTail(ListNode head,int k) {
        if (k < 0) return null;
        ListNode ptr1 = head, ptr2 = head;
        while (k > 0 && ptr1 != null) {
            ptr1 = ptr1.next;
            k--;
        }
        if (k > 0) return null;
        while (ptr1 != null) {
            ptr1 = ptr1.next;
            ptr2 = ptr2.next;
        }
        return ptr2;
    }
}
```

### 面试题23 链表中环的入口节点
题目: [Acwing](https://www.acwing.com/problem/content/86/)

- 思路: 快慢指针 先用一个两倍的指针和一个一倍的指针, 去发现环的长度或无环, 之后让快指针从头结点先走cnt长度, 然后然后慢指针开始和快指针一起往前走, 当然两个指针重合的时候, 就说明找到了入口.
- 边界条件: 无环 环长为奇数 环长为偶数 环连接头结点, 环连接尾节点
```java
public class Solution {

    public ListNode EntryNodeOfLoop(ListNode pHead)
    {
        ListNode ptrFast = pHead, ptrSlow = pHead;
        int cnt = 0;
        while (ptrFast != null && (cnt == 0 || ptrFast != ptrSlow)) {
            ptrFast = ptrFast.next;
            cnt++;
            if (ptrFast == null) return null;
            else if (ptrFast == ptrSlow) break;
            else {
                ptrFast = ptrFast.next;
                ptrSlow = ptrSlow.next;
            }
        }
        if (ptrFast == null) return null;
        ptrFast = pHead;ptrSlow = pHead;
        while (cnt > 0) {
            ptrFast = ptrFast.next;
            cnt--;
        }
        while (ptrFast != ptrSlow) {
            ptrFast = ptrFast.next;
            ptrSlow = ptrSlow.next;
        }
        return ptrSlow;
    }
}
```

### 面试题24 反转链表
题目: [Acwing](https://www.acwing.com/problem/content/33/)

- 经典基础题, 链表翻转, 两个指针和一个临时指针, 向右移动.
```java
public class Solution {
    public ListNode ReverseList(ListNode head) {
        if (head == null || head.next == null ) return head;
        ListNode left = null, right = head;
        while (right != null) {
            ListNode temp = right.next;
            right.next = left;
            left = right;
            right = temp;
        }
        return left;
    }
}
```

### 面试题25 合并两个排序的链表
题目: [Acwing](https://www.acwing.com/problem/content/34/)
```java
public class Solution {
    public ListNode Merge(ListNode list1,ListNode list2) {
        if (list1 == null) return list2;
        if (list2 == null) return list1;
        ListNode head = null, ptr = null;
        if (list1.val <= list2.val) {
            head = list1;
            list1 = list1.next;
        }
        else {
            head = list2;
            list2 = list2.next;
        }
        ptr = head;
        while (list1 != null && list2 != null) {
            if (list1.val <= list2.val) {
                ptr.next = list1;
                list1 = list1.next;
            }
            else {
                ptr.next = list2;
                list2 = list2.next;
            }
            ptr = ptr.next;
        }
        if (list1 != null) ptr.next = list1;
        if (list2 != null) ptr.next = list2;
        return head;
    }
}
```

### 面试题26 树的子结构
题目: [Acwing](https://www.acwing.com/problem/content/35/)

- 边界条件: 两个都是空树 两个都是只有一个节点的树 B是A的叶子节点 B是A的中间一部分
```java
class Solution {
    public boolean hasSubtree(TreeNode pRoot1, TreeNode pRoot2) {
        if (pRoot2 == null || pRoot1 == null) return false;
        return isSameTree(pRoot1, pRoot2) || hasSubtree(pRoot1.left, pRoot2) || hasSubtree(pRoot1.right, pRoot2);
    }
    private boolean isSameTree(TreeNode pRoot1, TreeNode pRoot2) {
        if (pRoot1 == null && pRoot2 == null) return true;
        if (pRoot2 == null) return true;
        if (pRoot1 == null) return false;
        if (pRoot1.val == pRoot2.val) return isSameTree(pRoot1.left, pRoot2.left) && isSameTree(pRoot1.right, pRoot2.right);
        return false;
    }
}
```

## 第四章
### 面试题27 二叉树的镜像
题目: [Acwing](https://www.acwing.com/problem/content/37/)
- 思路: 递归旋转
- 边界条件: 空 只有一个节点 单边 完全二叉树
```java
public class Solution {
    public void Mirror(TreeNode root) {
        turn(root);
    }
    private TreeNode turn(TreeNode node) {
        if (node == null) return null;
        TreeNode temp = node.left;
        node.left = turn(node.right);
        node.right = turn(temp);
        return node;
    }
}
```

### 面试题28 对称的二叉树
题目:[Acwing](https://www.acwing.com/problem/content/38/)
- 思路: 递归比较两棵树的左边vs右边, 右边vs左边 对于同一棵树(root) 只需要比较一次.
- 边界条件: 空 只有一个节点 完全二叉树 只有两个外侧有 斜不对称的值相同树 如下
```
   1
  / \
 1   1
/   /
1   1
```
```java

public class Solution {
    boolean isSymmetrical(TreeNode pRoot)
    {
        return isSymetrical(pRoot, pRoot);
    }
    private boolean isSymetrical(TreeNode root1, TreeNode root2) {
        if (root1 == null && root2 == null) return true;
        if (root1 == null || root2 == null) return false;
        if (root1 == root2) return isSymetrical(root1.left, root2.right);
        if (root1.val == root2.val) {
            return isSymetrical(root1.left, root2.right) 
                && isSymetrical(root1.right, root2.left);
        }
        return false;
    }
}
```

### 面试题29 顺时针打印矩阵
题目: [Acwing](https://www.acwing.com/problem/content/39/)

- 边界条件: 只有一行, 只有一列, 只有一个, 2*2, 3*3, 空
```java
class Solution {
    public ArrayList<Integer> printMatrix(int [][] matrix) {
        if (matrix == null || matrix.length == 0 || matrix[0].length == 0) 
            return new ArrayList<>();
        ArrayList<Integer> list = new ArrayList<>();
        printCircle(matrix, list, 0, 0, matrix.length-1, matrix[0].length-1);
        return list;
    }
    private void printCircle(int[][] matrix, List<Integer> list, 
                                int up, int left, int down, int right) {
        if (up > down || left > right) return ;
        for (int i = left; i <= right; i++) list.add(matrix[up][i]); // 从左到右
        if (up < down) {
            for (int i = up+1; i <= down; i++) list.add(matrix[i][right]); // 从上倒下
        }
        if (up != down && left < right) {
            for (int i = right-1; i >= left; i--) list.add(matrix[down][i]);
        }
        if (left != right && up + 1 < down) {// 从下到上 down-1 到 up+1
            for (int i = down-1; i > up; i--) list.add(matrix[i][left]); 
        }
        printCircle(matrix, list, up+1, left+1, down-1, right-1);
    }
}
```

### 面试题30 包含min函数的栈
题目: [Acwing](https://www.acwing.com/problem/content/90/)
- 思路: 用一个min辅助栈记录当前的最小值, 这样当但前的最小被pop出去时, 以前的最小值依然保留. min栈的更新规则, 如果push进来的比之前的min小, 则将该值push进min, 否则把min顶的当前最小值再push进一遍作为当前元素进入时的全局最小值.

```java
public class Solution {
    Stack<Integer> elems = new Stack<>();
    Stack<Integer> min = new Stack<>();
    
    public void push(int node) {
        elems.push(node);
        if (min.isEmpty() || node < min.peek()) min.push(node);
        else min.push(min.peek());
    }
    
    public void pop() {
        elems.pop();
        min.pop();
    }
    
    public int top() {
        return elems.peek();
    }
    
    public int min() {
        return min.peek();
    }
}
```

### 面试题31 栈的压入、弹出序列
题目: [Acwing](https://www.acwing.com/problem/content/40/)

```java
public class Solution {
    public boolean IsPopOrder(int [] pushA,int [] popA) {
        if (pushA == null && popA == null) return true;
        if (pushA == null || popA == null) return false;
        int ptrPush = 0, ptrPop = 0;
        Stack<Integer> stack = new Stack<>();
        while (ptrPop < popA.length) {
            while (stack.isEmpty() || stack.peek() != popA[ptrPop]) {
                if (ptrPush >= pushA.length) return false;
                stack.push(pushA[ptrPush++]);
            }
            if (stack.peek() == popA[ptrPop]) {
                stack.pop();
                ptrPop++;
            }
        }
        return true;
    }
}
```

### 面试题32 从上往下打印二叉树
题目: [Acwing](https://www.acwing.com/problem/content/41/)
- 思路: 用队列
```java
public class Solution {
    public ArrayList<Integer> PrintFromTopToBottom(TreeNode root) {
        ArrayList<Integer> result = new ArrayList<>();
        if (root == null) return result;
        Queue<TreeNode> q = new ArrayDeque<>();
        q.add(root);
        while (!q.isEmpty()) {
            TreeNode node = q.remove();
            result.add(node.val);
            if (node.left != null) q.add(node.left);
            if (node.right != null) q.add(node.right);
        }
        return result;
    }
}
```

### 面试题33 二叉搜索树的后序遍历序列
题目: [Acwing](https://www.acwing.com/problem/content/44/)

- 思路: 序列尾是根节点, 左子树小于根节点, 右子树大于根节点

```java
public class Solution {
    public boolean VerifySquenceOfBST(int [] sequence) {
        if (sequence == null || sequence.length == 0) return false;
        return verify(sequence, 0, sequence.length-1);
    }
    private boolean verify(int[] seq, int start, int end) {
        if (start >= end) return true;
        int root = seq[end], rightStart = start;
        while (seq[rightStart] < root) rightStart++;
        for (int i = rightStart; i < end; i++) {
            if (seq[i] < root) return false;
        }
        return verify(seq, start, rightStart-1) && verify(seq, rightStart, end-1);
    }
}
```

### 面试题34 二叉树中和为某一值的路径
题目: [Acwing](https://www.acwing.com/problem/content/45/)
- 思路: dfs到底进行判断, 加入
```java
public class Solution {
    private ArrayList<ArrayList<Integer>> results;
    public ArrayList<ArrayList<Integer>> FindPath(TreeNode root,int target) {
        results = new ArrayList<ArrayList<Integer>>();
        if (root == null) return results;
        ArrayList<Integer> path = new ArrayList<Integer>();
        dfs(root, target, path, 0);
        results.sort(
            (ArrayList<Integer> a, ArrayList<Integer> b) -> b.size() - a.size()
        );
        return results;
    }
    private void dfs(TreeNode root, int target, 
                     ArrayList<Integer> path, int current) {
        // guarantee that root not be null
        current += root.val;
        path.add(root.val);
        if (root.left == null && root.right == null && current == target) {
            results.add(new ArrayList(path));
        }
        if (root.left != null) dfs(root.left, target, path, current);
        if (root.right != null) dfs(root.right, target, path, current);
        path.remove(path.size()-1);
    }
}
```

### 面试题35 复杂链表的复刻
题目: [Acwing](https://www.acwing.com/problem/content/89/)

- 思路: 主要困难是random指针不好处理, 一种方法是建立clone的链表的节点和原链表的节点的hash, 但是需要额外空间, 另一种方法是让每个clone的节点跟在原节点后面, 做好random的连接后, 把两个链表分离开来.
```java
public class Solution {
    public RandomListNode Clone(RandomListNode pHead)
    {
        if (pHead == null) return null;
        RandomListNode ptr = pHead;
        while (ptr != null) { // 复制新节点跟在原节点后面
            RandomListNode clone = new RandomListNode(ptr.label);
            clone.next = ptr.next;
            ptr.next = clone;
            ptr = clone.next;
        }
        ptr = pHead;
        RandomListNode clonePtr;
        while (ptr != null) { // 将克隆节点的random指针指向原节点的random指针指向的节点的后一个
            clonePtr = ptr.next;
            if (ptr.random != null) {
                clonePtr.random = ptr.random.next;
            }
            ptr = clonePtr.next;
        }
        ptr = pHead;
        RandomListNode cHead = ptr.next;
        while (ptr != null) {
            clonePtr = ptr.next;
            ptr.next = clonePtr.next;
            if (clonePtr.next != null) clonePtr.next = clonePtr.next.next;
            ptr = ptr.next;
        }
        return cHead;
    }
}
```

### 面试题36 二叉搜索树与双向链表
题目: [Acwing](https://www.acwing.com/problem/content/87/)

- 思路: 中序遍历首先就是有序的, 另外处理到某一个节点时, 其左儿子的指针是访问过的, 可以用来做链表, 而右儿子的指针还没有用过. 因此基本思想是用当前节点的左儿子指针指向链表上的前一个节点, 使用递归实现.

```java
public class Solution {
    public TreeNode Convert(TreeNode pRootOfTree) {
        if (pRootOfTree == null) return null;
        TreeNode tail = inOrder(pRootOfTree, null);
        TreeNode success = null;
        while (tail != null) {
            tail.right = success;
            success = tail;
            tail = tail.left;
        }
        return success;
    }
    private TreeNode inOrder(TreeNode node, TreeNode prev) {
        if (node.left != null) node.left = inOrder(node.left, prev);
        else node.left = prev;
        if (node.right != null) return inOrder(node.right, node);
        else return node;
    }
}
```

### 面试题37 序列化二叉树
题目: [Acwing](https://www.acwing.com/problem/content/46/)

思路: 不管中序也好, 前序也好, 要把null保存进去就能得到唯一的树
```java
import java.util.*;
public class Solution {
    String Serialize(TreeNode root) {
        StringBuilder sb = new StringBuilder();
        treeToString(root, sb);
        return sb.toString();
  }
    TreeNode Deserialize(String str) {
        if (str == null || str.length() == 0) return null;
        List<String> list = new LinkedList<>();
        String[] sarray = str.split("!");
        for (String s : sarray) list.add(s);
        return stringToTree(list);
        
  }
    private void treeToString(TreeNode node, StringBuilder sb) {
        if (node == null) sb.append("#!");
        else {
            sb.append("" + node.val + "!");
            treeToString(node.left, sb);
            treeToString(node.right, sb);
        }
    }
    private TreeNode stringToTree(List<String> list) {
        if (list.isEmpty()) return null;
        String s = list.remove(0);
        if (s.equals("#")) return null;
        TreeNode node = new TreeNode(Integer.parseInt(s));
        node.left = stringToTree(list);
        node.right = stringToTree(list);
        return node;
    }
}
```

### 面试题38 字符串的排列
思路: 全排列有两种思路, 一种是基于swap, 将第一个元素与后面的元素交换, 然后递归处理后面的元素. 另一种是基于boolean[]数组.
```java
import java.util.ArrayList;
import java.util.Arrays;
// 按位排列 递归 每一位都有不重复的所有字符的可能性
public class Solution {
    private boolean[] used;
    public ArrayList<String> Permutation(String str) {
        ArrayList<String> results = new ArrayList<>();
        if (str == null || str.length() == 0) return results;
        char[] array = str.toCharArray();
        char[] current = new char[array.length];
        used = new boolean[array.length];
        Arrays.sort(array);
        arrange(array, 0, results, current);
        return results;
    }
    private void arrange(char[] array, int index, 
                         ArrayList<String> results, char[] current) {
        for (int i = 0; i < array.length; i++) { // 选择当前没有被使用过的, 并且不重复
            if (!used[i] && (i == 0 || !(array[i] == array[i-1] && !used[i-1]))) {
                used[i] = true;
                current[index] = array[i];
                if (index == array.length-1) results.add(new String(current));
                else arrange(array, index + 1, results, current);
                used[i] = false;
            }
        }
    }
}
```

## 第五章
### 面试题39 数组中出现次数超过一半的数字
数组中有一个数字出现的次数超过数组长度的一半，请找出这个数字。

假设数组非空，并且一定存在满足条件的数字

- [x] 独立&&完美

解法1:

- 思路: 出现次数超过一半的数字的个数与其他数字个数之和的差一定是正数, 因此用一个cnt计数, 每出现一个和当前数相同的数就+1, 每出现一个不相同的数就-1, 若当前的cnt为0, 则将当前数设为所在的数, 重新开始计数
- 边界条件: 全相同, 3个相同的接4个相同的,4个相同的接3个相同的

```java
class Solution {
    public int moreThanHalfNum_Solution(int[] nums) {
        if (nums == null) return -1;
        int cnt = 0, cur = nums[0];
        for (int i = 0; i < nums.length; i++) {
            if (cnt == 0) {
                cur = nums[i];
                cnt = 1;
            }
            else if (cur == nums[i]) cnt++;
            else cnt--;
        }
        return cur;
    }
}
```

解法二: 考虑有可能会没有超过一半的情况, 可以使用hash的方式

### 面试题40 最小的k个数

输入n个整数，找出其中最小的k个数。

注意：
- 数据保证k一定小于等于输入数组的长度;
- 输出数组内元素请按从小到大顺序排序;

- [x] 独立&&完美
- 思路: 最大堆的应用, 维护一个k个数的最大堆, 如果有更小的数进来, 就把最大的pop出去
- 边界条件: k=length, 有重复且重复的部分刚好一部分在最小k个数, 一部分不在, k大于length
- Java知识点: 自定义Comparator, Comparator.reverseOrder

```java
import java.util.Comparator;
import java.util.PriorityQueue;

class Solution {
    public List<Integer> getLeastNumbers_Solution(int [] input, int k) {
        if (k > input.length) return null;
        LinkedList<Integer> result = new LinkedList<>();
        PriorityQueue<Integer> pq = new PriorityQueue<>(k,Comparator.reverseOrder());
        for(int a: input) {
            if (pq.size() < k) pq.add(a);
            else if (pq.peek() > a){
                pq.poll();
                pq.add(a);
            }
        }
        while (pq.size() > 0) {
            int a = pq.poll();
            result.addFirst(a);
        }
        return result;
    }
}
```

### 面试题41 数据流中的中位数
题目:[Acwing]()
如何得到一个数据流中的中位数？
如果从数据流中读出奇数个数值，那么中位数就是所有数值排序之后位于中间的数值。
如果从数据流中读出偶数个数值，那么中位数就是所有数值排序之后中间两个数的平均值。

- 思路: 用一个最大堆表示中位数左边, 一个最小堆表示中位数右边, 始终保持两个堆的size相差不超过1
- 必须要存下所有的元素
```java
import java.util.Comparator;
import java.util.PriorityQueue;

class Solution {
    private PriorityQueue<Integer> max = new PriorityQueue<>(Comparator.reverseOrder());
    private PriorityQueue<Integer> min = new PriorityQueue<>();
    public void insert(Integer num) {
        if (((min.size() + max.size()) & 1 )== 0) {
            if (min.size() > 0 && num > min.peek()) {
                min.add(num);
                num = min.poll();
            }
            max.add(num);
        }
        else {
            if (num < max.peek()) {
                max.add(num);
                num = max.poll();
            }
            min.add(num);
        }
    }
    public Double getMedian() {
        if (min.size() + max.size() == 0) return 0.; // 注意这个边界情况
        if (((min.size() + max.size()) & 1) == 1) {
            return (double) max.peek();
        }
        else {
            return (min.peek() + max.peek()) / 2.;
        }
    }
}
```

### 面试题42 连续子数组的最大和
题目: [Acwing](https://www.acwing.com/problem/content/50/)

- [x] 独立&&完美
- 思路: 之前的子数组之和如果大于0, 则能够继续延长, 对整体是正向的作用, 如果为负, 则直接丢弃, 为负作用
- 边界条件: 全负数, 归零, 正常
```java
class Solution {
    public int maxSubArray(int[] nums) {
        if (nums == null || nums.length == 0) return 0;
        int cnt = 0, max = Integer.MIN_VALUE;
        for (int i = 0; i < nums.length; i++) {
            cnt += nums[i];
            max = max < cnt? cnt : max;
            if (cnt <= 0) cnt = 0;
        }
        return max;
    }
}
```

### 面试题43 从1到n整数中1出现的次数
题目: [Acwing](https://www.acwing.com/problem/content/51/)
方法一:

```java
class Solution {
    public int numberOf1Between1AndN_Solution(int n) {
        int cnt = 0, base = 1, m = n;
        while (m != 0) {
            int thisDigit = m % 10; // 当前位
            m /= 10; // 左边的位
            if (thisDigit > 1) {
                cnt += (m + 1) * base;
            }
            else if (thisDigit == 1) {
                cnt += m * base + n % base + 1;
            }
            else cnt += m * base;
            
            base *= 10;
        }
        return cnt;
    }
}
```
方法二
- 思路: 用递归来做, 难想到一点, 但其实思路更清晰. 现将区段划分成两部分,例如对于21234分为1-1234和1235-21234,对于大的这部分, 分两种情况考虑, 出现在最高位的1和出现在后面的位的1; 对于1-1234可以用递归接着往下分

### 面试题44 数字序列中某一位的数字
题目:[Acwing](https://www.acwing.com/problem/content/52/)

- [ ] 独立&&完美

方法一
- 思路: 从手动计算中找规律
- 边界条件: n为最大正整数
```java
class Solution {
    public int digitAtIndex(int n) {
        if (n < 10) return n;
        n -= 10;
        int cnt = 10, base = 10, numOfDigital = 2;
        while ((long) n > (long) 9 * base * numOfDigital) {
            n -= 9 * base * numOfDigital;
            cnt += 9 * base;
            numOfDigital++;
            base *= 10;
        }
        int num = cnt + n / numOfDigital;
        int digit = n % numOfDigital;
        // System.out.println("" + num + " " + digit);
        int temp = numOfDigital - digit - 1;
        while (temp > 0) {
            num /= 10;
            temp--;
        }
        return num % 10;
    }
}
```



### 面试题45 把数组排成最小的数
题目: [Acwing](https://www.acwing.com/problem/content/54/)

- 思路: 总体思路正确, 没有抓住 a+b和b+a等长的特点 大数比较的基本思路是转化为字符串比较
- 边界条件: [321, 32], [323, 32], [3232, 32]
- Java知识点: Comparator是函数式接口, 因此匿名类可以进一步简化为`(s1,s2)->(s1+s2).compareTo(s2+s1)`的lambda表达式
```java
import java.util.ArrayList;
import java.util.*;
public class Solution {
    public String PrintMinNumber(int [] numbers) {
        List<Integer> list = new ArrayList<>();
        for (int a: numbers) list.add(a);
        list.sort(
            (Integer a, Integer b)->{
                String s1 = a.toString();
                String s2 = b.toString();
                return (s1 + s2).compareTo(s2 + s1);
        });
        String s = "";
        for (Integer i: list) {
            s += i;
        }
        return s;
    }
}
```

### 面试题46 把数字翻译成字符串
题目: [Acwing](https://www.acwing.com/problem/content/55/)

- [ ] 独立&&完美
- 思路: 思路总体是对的, 但没必要用Map这么重型的数据结构, 可以用一个length大小的数组表示后面的字符串的可能性
```java
class Solution {
    private Map<String, Integer> map = new HashMap<>();
    public int getTranslationCount(String s) {
        int result = getTranslationCount(s, 0);
        return result;
    }
    private int getTranslationCount(String s, int begin) {
        // if (begin == s.length()) return 0;
        if (begin >= s.length()-1) return 1;
        String sub = s.substring(begin);
        if (map.containsKey(sub)) return map.get(sub);
        int ret = getTranslationCount(s, begin+1);
        if (s.charAt(begin) != '0' && Integer.parseInt(s.substring(begin, begin+2)) < 26) {
            ret += getTranslationCount(s, begin+2);
        }
        map.put(sub, ret);
        return ret;
    }
}
```

### 面试题48 礼物的最大价值

- [ ] 独立&&完美
- 思路:可进一步优化，二维数组可以变成一维数组, 原地迭代
```java
class Solution {
    int[][] values;
    public int getMaxValue(int[][] grid) {
        if (grid == null || grid.length == 0 || grid[0].length == 0) return 0;
        int m = grid.length, n = grid[0].length;
        values = new int[m][n];
        for (int i = m-1; i >= 0; i--) {
            for (int j = n-1; j >= 0; j--) {
                int down = 0, right = 0;
                if (i < m - 1) down = values[i+1][j];
                if (j < n - 1) right = values[i][j+1];
                values[i][j] = grid[i][j] + down > grid[i][j] + right? grid[i][j] + down : grid[i][j] + right;
            }
        }
        return values[0][0];
    }
}
```

### 面试题48 最长不含重复字符的子字符串
题目: [Acwing](https://www.acwing.com/problem/content/57/)

- 思路: 总体思路正确, 实现的具体方法有所不同, 书本中的方法: 用一个hash表(数组)记录该字符最后一次出现的位置, 同时用curLength和maxLength两个变量记录当前子字符串的长度和最长子字符串的长度, 当当前字符最后一次出现大于0 并且当前位置减去上一次出现位置小于curLength时, 说明这个字符在当前子字符串中出现了, 重新设置curLength并将当前字符的最后一次出现位置更新.

```java
// 原思路
class Solution {
    private boolean[] hash = new boolean[26];
    public int longestSubstringWithoutDuplication(String s) {
        if (s == null || s.length() == 0) return 0;
        int cnt = 0, max = 0, begin = 0;
        for (int i = 0; i < s.length(); i++) {
            if (!hash[s.charAt(i)-'a']) cnt++;
            else {
                while (begin < i && s.charAt(begin) != s.charAt(i)) {
                    hash[s.charAt(begin)-'a'] = false;
                    begin++;
                    cnt--;
                }
                begin++;
            }
            hash[s.charAt(i)-'a'] = true;
            max = max > cnt ? max:cnt;
        }
        return max;
    }
}
```

### 面试题49 丑数
我们把只包含质因子2、3和5的数称作丑数（Ugly Number）。

例如6、8都是丑数，但14不是，因为它包含质因子7。

求第n个丑数的值

- [ ] 独立&&完美
- 思路: 记录下之前的丑数, 下一个丑数一定是之前的丑数乘以2, 3, 5后比当前丑数大且最小的那一个.
```java
public class Solution {
    public int GetUglyNumber_Solution(int index) {
        if (index == 1) return 1;
        if (index < 1) return 0;
        int[] ugly = new int[index+1];
        ugly[1] = 1;
        int ptr2 = 1;
        int ptr3 = 1;
        int ptr5 = 1;
        int n = 1;
        while (n < index) {
            while (ptr2 <= n && ugly[ptr2] * 2 <= ugly[n]) ptr2++;
            ugly[n+1] = ugly[ptr2] * 2;
            while (ptr3 <= n && ugly[ptr3] * 3 <= ugly[n]) ptr3++;
            ugly[n+1] = Math.min(ugly[ptr3] * 3, ugly[n+1]);
            while (ptr5 <= n && ugly[ptr5] * 5 <= ugly[n]) ptr5++;
            ugly[n+1] = Math.min(ugly[ptr5] * 5, ugly[n+1]);
            n++;
        }
        return ugly[index];
    }
}
```

### 面试题50 第一个只出现一次的字符
#### 题目1 字符串中第一个只出现一次的字符
题目: [Acwing](https://www.acwing.com/problem/content/59/)

- 思路: hash表 用一个hash表去记录出现的位置, 当出现次数多于一次时, 使其无效
```java
class Solution {
    public char firstNotRepeatingChar(String s) {
        if (s == null || s.length() == 0) return '#';
        int[] firstAppear = new int[128];
        int first = s.length();
        char ret = ' ';
        Arrays.fill(firstAppear, -1);
        for (int i = 0; i < s.length(); i++) {
            if (firstAppear[s.charAt(i)] == -1) firstAppear[s.charAt(i)] = i;
            else firstAppear[s.charAt(i)] = -2;
        }
        for (int i = 0; i < 128; i++) {
            if (firstAppear[i] >= 0 && first > firstAppear[i]) {
                first = firstAppear[i];
                ret = (char)i;
            }
        }
        return first == s.length() ? '#': ret;
    }
}
```
#### 题目2 字符流中第一个只出现一次的字符
题目: [Acwing](https://www.acwing.com/problem/content/60/)

- 思路: 本题和上题几乎是一样的, 只是将循环查询移到了`firstAppearingOnce`中
```java
class Solution {
    static final int MAXSIZE = 256;
    int[] hashmap = new int[MAXSIZE];
    int cnt = 0; 
    {
        Arrays.fill(hashmap, -1);
    }   
    //Insert one char from stringstream   
    public void insert(char ch){
        if (hashmap[ch] == -1) hashmap[ch] = cnt;
        else if (hashmap[ch] >= 0) hashmap[ch] = -2;
        cnt++;
    }
    //return the first appearence once char in current stringstream
    public char firstAppearingOnce(){
        char ret = ' ';
        int first = cnt+1;
        for (int i = 0; i < MAXSIZE; i++) {
            if (hashmap[i] >= 0 && hashmap[i] < first) {
                first = hashmap[i];
                ret = (char)i;
            }
        }
        return first > cnt? '#':ret;
    }
}
```

### 面试题51 数组中的逆序对
题目: [Acwing](https://www.acwing.com/problem/content/61/)

- 思路: 说到逆序对, 首先想到, 插入排序就是每次交换消除一个逆序对, 希尔排序能够一次减少多个逆序对, 所以效率更高但是总体也是O(n^2)的复杂度. 要能够计算逆序对数量的, 首先必须是稳定排序, 不稳定排序一下打乱了没法计数. 这时想到归并排序是nlogn的稳定排序, 它比插入排序快在一次消除多个逆序对: 一旦有一个右边的子数组的元素插在了左边子数组剩余元素的前面, 说明左边子数组的剩余元素都和这个右边的元素构成逆序对. 这样计算上也有了依据.

```java
public class Solution {
    public int InversePairs(int [] array) {
        if (array == null || array.length == 0) return 0;
        int[] aux = new int[array.length];
        return sort(array, aux, 0, array.length-1);
    }
    private int sort(int[] array, int[] aux, int start, int end) {
        if (start == end) return 0;
        int mid = (start + end) >> 1;
        int left = sort(array, aux, start, mid);
        int right = sort(array, aux, mid+1, end);
        long cur = merge(array, aux, start, mid, end);
        return (int)((cur + left + right) % 1000000007);
    }
    private long merge(int[] array, int[] aux, int start, int mid, int end) {
        long cnt = 0;
        if (array[mid] < array[mid+1]) return cnt;
        for (int i = start; i <= end; i++) aux[i] = array[i];
        int left = start, right = mid + 1, ptr = start;
        while (left <= mid && right <= end) {
            if (aux[left] < aux[right]) array[ptr++] = aux[left++];
            else {
                array[ptr++] = aux[right++];
                cnt += mid - left + 1;
            }
        }
        while (left <= mid) array[ptr++] = aux[left++];
        while (right <= end) array[ptr++] = aux[right++];
        return cnt;
    }
}

```

### 面试题51 两个链表的第一个公共结点
题目: [Acwing](https://www.acwing.com/problem/content/62/)

- 思路: 共同链部分的长度一定相同, 但是因为是单向链表不能从尾往头扫描, 但是可以先分别统计链的长度, 对于长的那个, 长的部分一定是不共链的, 因此这条链上的指针先走两个长度只差的步数, 之后一起往前走, 知道遇到两个节点指针指向的对象相同.
```java
class Solution {
    public ListNode findFirstCommonNode(ListNode headA, ListNode headB) {
        int lengthA = 0, lengthB = 0;
        ListNode ptrA = headA, ptrB = headB;
        while (ptrA != null) {
            lengthA++;
            ptrA = ptrA.next;
        }
        while (ptrB != null) {
            lengthB++;
            ptrB = ptrB.next;
        }
        ptrA = headA; ptrB = headB;
        while (lengthA - lengthB > 0 && ptrA != null) {ptrA = ptrA.next; lengthA--;}
        while (lengthB - lengthA > 0 && ptrA != null) {ptrB = ptrB.next; lengthB--;}
        while (ptrA != null && ptrB != null && ptrA != ptrB) {
            ptrA = ptrA.next;
            ptrB = ptrB.next;
        }
        if (ptrA == null || ptrB == null) return null;
        else return ptrA;
    }
}
```
### 面试题53 数字在排序数组中出现的次数
题目:[Acwing](https://www.acwing.com/problem/content/63/)

- 思路: 暴力法是O(n)的, 想一下有没有更快的方法, 因为是有序的, 考虑使用二分法, 找到对一个元素后需要向两边搜索, 找到所有的.
```java
class Solution {
    public int getNumberOfK(int[] nums, int k) {
        if (nums == null || nums.length == 0) return 0;
        if (nums[0] > k && nums[nums.length-1] < k) return 0;
        int left = 0, right = nums.length, mid = (left+right) / 2;
        while (nums[mid] != k && left <= right) {
            if (nums[mid] > k) right = mid - 1;
            else left = mid + 1;
            mid = (left+right) / 2;
        }
        if (left > right) return 0;
        int cnt = 1;
        left = mid-1;right = mid + 1;
        while (left >= 0 && nums[left] == k) {
            cnt++;
            left--;
        }
        while (right < nums.length && nums[right] == k) {
            cnt++;
            right++;
        }
        return cnt;
    }
}
```



### 面试题54 二叉搜索树的第k个结点
题目: [Acwing](https://www.acwing.com/problem/content/66/)

- 思路: 二叉搜索树的中序遍历得到的就是有序数组, 因此可以按照中序找到第k小的
```java
class Solution {
    private int cnt;
    private TreeNode result;
    public TreeNode kthNode(TreeNode root, int k) {
        cnt = k;
        inOrder(root);
        return result;
    }
    private void inOrder(TreeNode node) {
        if (cnt < 0) return ;
        if (node.left != null) inOrder(node.left);
        cnt--;
        if (cnt == 0) result = node;
        if (node.right != null) inOrder(node.right);
        
    }
}
```

### 面试题55 二叉树的深度
题目: [Acwing](https://www.acwing.com/problem/content/67/)

- 思路: 任意一种遍历, 如果采用递归, 可以很方便的记录层数
```java
class Solution {
    private int maxDepth;
    public int treeDepth(TreeNode root) {
        maxDepth = 0;
        preOrder(root, 1);
        return maxDepth;
    }
    private void preOrder(TreeNode node, int depth) {
        if (node == null) return ;
        maxDepth = Math.max(maxDepth, depth);
        preOrder(node.left, depth+1);
        preOrder(node.right, depth+1);
    }
}
```
### 面试题56 数组中数字的出现次数****
#### 数组中只出现一次的两个数字
题目: [Acwing](https://www.acwing.com/problem/content/69/)

思路: 两个相同的数字的异或为0. 先考虑只有一个出现一次的数字, 则对整个数组的数字逐个异或就可以得到. 现在考虑如何把两个出现一次的数字分开来. 由于两个数字不同, 则异或后一定有某一位上有1, 这表示一个数字的该位为1, 另一个数字的该位为0. 按照这个规律, 可以把该位为1和该位为0的元素分成两组, 分别逐个异或.
```java
public class Solution {
    public void FindNumsAppearOnce(int [] array,int num1[] , int num2[]) {
        int diff = 0;
        for (int i: array) {
            diff = diff ^ i;
        }
        int mask = 1;
        while ((mask & diff) ==0) mask = mask << 1;
        num1[0] = 0; num2[0] = 0;
        for (int i: array) {
            if ((mask & i) == 0) num1[0] = num1[0] ^ i;
            else num2[0] = num2[0] ^ i;
        }
    }
}
```

#### 数组中唯一只出现一次的数字
题目: [Acwing](https://www.acwing.com/problem/content/70/)

思路: 首先, 由于其他数字都出现三次, 前面的方法就不能用了. 但是依然可以考虑位操作, 如果对整个数组的元素的各位的1统计, 对于重复三次的数字, 为1的位能够被3整除, 如果某一位对3取余剩余1, 说明这一位是只出现一次的那个数的.
```java
class Solution {
    public int findNumberAppearingOnce(int[] nums) {
        int[] bitmap = new int[32];
        for (int a: nums) {
            for(int i = 0; i < 32; i++) {
                bitmap[i] += (a & 1);
                a >>= 1;
            }
        }
        int result = 0;
        for (int i = 31; i >= 0; i--) {
            int rest = bitmap[i] % 3;
            result <<= 1;
            result += rest;
            
        }
        return result;
    }
}
```

### 面试题57 和为S的数字
#### 和为S的两个数字(2-SUM问题)
题目:[Acwing](https://www.acwing.com/problem/content/71/)
Acwing提供的这道题目, 数组是无序的, 因此可以用hash来解决. 当有序的时候, 可以用双指针,一头一尾向中间移动.

```java
class Solution {
    public int[] findNumbersWithSum(int[] nums, int target) {
        if (nums == null || nums.length == 0) return null;
        Set<Integer> hash = new HashSet<>();
        int[] result = new int[2];
        for (int a: nums) {
            if (hash.contains(target-a)) {
                result[0] = target-a;
                result[1] = a;
                return result;
            }
            else hash.add(a);
        }
        return null;
    }
}
```
#### 和为S的连续正数序列
题目: [Acwing](https://www.acwing.com/problem/content/72/)

思路: 和上题类似的思路, 但是变为记录头和尾, 头尾逐渐递增, 直到small大于(s+1)/2. 当sum大于k时, 减去最小的数, 当sum小于k时, 加上最大的一个数.
```java
import java.util.ArrayList;
public class Solution {
    public ArrayList<ArrayList<Integer> > FindContinuousSequence(int sum) {
        int listsum = 3, small = 1, big = 2;
        ArrayList<ArrayList<Integer>> results = new ArrayList<>();
        while (small < (sum+1)/2) {
            if (listsum < sum) {
                big++;
                listsum += big;
            }
            else if (listsum > sum) {
                listsum -= small++;
            }
            else {
                ArrayList<Integer> list = new ArrayList<>();
                for (int i = small; i <= big; i++) list.add(i);
                results.add(list);
                listsum -= small++;
            }
        }
        return results;
    }
}
```
### 面试题58 翻转字符串
题目: [Acwing](https://www.acwing.com/problem/content/73/)

- 思路: 全局翻转和分段翻转, 左旋字符串也可以采用相同的思路.
- 边界条件: 空, 长度为0, 全都是空格, 只有一个空格 没有空格

```java
public class Solution {
    public String ReverseSentence(String str) {
        if (str == null || str.length() == 0) return str;
        char[] chars = str.toCharArray();
        Reverse(chars, 0, chars.length-1);
        int start = 0, end = 0;
        while (start < chars.length) {
            if (chars[start] == ' ') {start++;}
            else if (end == chars.length || chars[end] == ' ') {
                Reverse(chars, start, end-1);
                start = end + 1;
            }
            end++;
        }
        return new String(chars);
    }
    private void Reverse(char[] chars, int start, int end) {
        if (chars != null && chars.length > 0 && start <= end) {
            int i = start - 1, j = end+1;
            while (++i < --j) {
                char temp = chars[i];
                chars[i] = chars[j];
                chars[j] = temp;
            }
        }
    }
}
```

### 面试题59 队列的最大值

#### 滑动窗口的最大值
题目: [Acwing](https://www.acwing.com/problem/content/75/)

- 思路: 使用一个队列记录当前的最大值. 每向右访问一个元素, 如果该元素比队列右端的元素大, 则队列可以从右往左清空, 直到队列右端的元素比当前元素大, 如果该元素比队列右端的小, 依然需要从右端入队, 它可能是将来的最大值. 每次获得当前窗口的最大值都在队列的左端拿. 还有一个问题就是如何判断队列左端的元素是否还在窗口中, 可以在队列中记录的是元素的下标而非本身, 根据当前下标和元素下标, 判断是否还在队列中.
- 边界条件: 空, 零, size比num.length大, size为负, size为0,1, 等于数组长度, 数组递增, 递减

```java
import java.util.*;
public class Solution {
    public ArrayList<Integer> maxInWindows(int [] num, int size)
    {
        ArrayList<Integer> result = new ArrayList<>();
        if (num == null || size == 0|| num.length < size) return result;
        Deque<Integer> dq = new LinkedList<Integer>();
        int start = 0, end = 0;
        while (start < num.length) {
            while (!dq.isEmpty() && num[dq.getLast()] <= num[start]) {
                dq.removeLast();
            }
            dq.addLast(start);
            start++;
            if (start >= size) {
                result.add(num[dq.getFirst()]);
                if (dq.getFirst() == end) dq.removeFirst();
                end++;
            }
        }
        return result;
    }
}
```

### 面试题60 n个骰子的点数
题目: [Acwing](https://www.acwing.com/problem/content/76/)

- 思路: 用递归实现全排列
- 边界条件: n < 1

```java
// 基于全排列的递归做法, 每次排列一个骰子
class Solution {
    public int[] numberOfDice(int n) {
        int[] result = new int[5*n+1];
        arrange(result, 0, n, 0);
        return result;
    }
    private void arrange(int[] result, int sum, int n, int k) {
        if (k == n-1) {
            for (int i = 1; i <= 6; i++) {
                int temp = sum + i;
                result[temp-n] += 1;
            }
        }
        else {
            for (int i = 1; i <= 6; i++) {
                arrange(result, sum + i, n, k+1);
            }
        }
    }
}

// 基于循环的做法, 因为添加第k个骰子时, 对于sum=n, 其出现的次数是上一轮中n-1,n-2,n-3...n-6的次数之和, 同时小于k的情况都为0
class Solution {
    private int gMax = 6; // 每个骰子最大为6
    public int[] numberOfDice(int n) {
        int[] result = new int[5*n+1]; // n ~ 6n
        calCnt(result, n);
        return result;
    }
    private void calCnt(int[] result, int n) {
        int[][] counts = new int[2][];
        counts[0] = new int[gMax * n + 1];
        counts[1] = new int[gMax * n + 1];
        int flag = 0; // 选择当前轮用哪个数组
        for (int i = 1; i <= gMax; i++) {
            counts[flag][i] = 1; // 第一个骰子进来时, 1-6的次数都是1
        }
        for (int k = 2; k <= n; k++) {
            for (int i = 1; i < k; i++) {
                counts[1-flag][i] = 0; // 小于k的情况都为0
            }
            for (int i = k; i <= gMax * n; i++) {
                counts[1-flag][i] = 0; // 先清空以前的内容
                for (int j = 1; j <= i && j <= gMax; j++) {
                    counts[1-flag][i] += counts[flag][i-j]; // 往前1-gMax之和
                }
            }
            flag = 1 - flag;
        }
        for (int i = n; i <= gMax * n; i++) {
            result[i-n] = counts[flag][i];
        }
    }
}
```

### 面试题61 扑克中的顺子
题目: [Acwing](https://www.acwing.com/problem/content/77/)

- 思路: 先排序, 然后记录好王的数量, 从最小的非0开始, 如果正好递增则继续向右, 否则减少一张王
- 边界条件: 只有一个不是0, 递增非0, 

```java
public class Solution {
    public boolean isContinuous(int [] numbers) {
        if (numbers == null || numbers.length == 0) return false;
        Arrays.sort(numbers);
        int cntKing = 0, index = 0, success = 0;
        while (numbers[index] == 0) {index++; cntKing++;}
        while (index < numbers.length) {
            if (index == 0 || numbers[index-1] == 0) {success = numbers[index++];}
            else if (numbers[index] != ++success) {
                if (cntKing > 0) cntKing--;
                else return false;
            }
            else index++;
        }
        return true;
    }
}
```

### 面试题62 圆圈中最后剩下的数字***
题目: [Acwing](https://www.acwing.com/problem/content/78/)

- 思路: 常规思路采用模拟过程来解决. 但是这道题是可以通过数学规律推推导表达式的. 设函数$f(n,m)$为最终剩下的数, 第一轮被抽走的数是$k=(m-1)\%n$, 剩下的数中最终剩下的数用函数表示为$f'(n-1, m)$, 注意这两个函数是不一样的, 因为在第二轮中是从$k+1$开始往后数的. 但是如果能够找到$f(n-1, m)$和$f'(n-1, m)$之间的关系, 则有机会得到递推式. 观察两者的区别, 起始的数字不一样
```
k+1 -> 0
k+2 -> 1
...
0 -> n-2
1 -> n-1
```
两者之间的关系是$p(x) = (x-(k+1) + n) \% n$, 反函数则为$p(x)^{-1} = (x + k+1) \% n$, 因此$p(f(n-1, m))^{-1} = f'(n-1, m) = f(n, m)$, 所以有$f(n, m) = (f(n-1, m)+k+1)\%n$, 带入$k=(m-1)\%n$, 有$f(n, m) = (f(n-1, m)+m)\%n$. 而$f(1, m) = 0$.
- 边界条件:

```java
import java.util.Arrays;
public class Solution {
    public int LastRemaining_Solution(int n, int m) {
        if (n < 1 || m < 1) return -1;
        int start = 0;
        for (int i = 2; i <= n; i++) {
            start = (m+start) % i;
        }
        return start;
    }
}
```

### 面试题63 股票的最大利润
题目: [Acwing](https://www.acwing.com/problem/content/79/)

- 思路: 记录一个最小, 记录一个最大
- 边界条件:

```java
class Solution {
    public int maxDiff(int[] nums) {
        if (nums == null || nums.length == 0) return 0;
        int min = Integer.MAX_VALUE, maxInterval = Integer.MIN_VALUE;
        for (int i = 0; i < nums.length; i++) {
            min = Math.min(min, nums[i]);
            maxInterval = Math.max(maxInterval, nums[i]-min);
        }
        return maxInterval;
    }
}
```

### 面试题65 不用加减乘除做加法
题目: [Acwing](https://www.acwing.com/problem/content/81/)

- 思路: 把不需要进位的部分和需要进位的部分分离, 用位运算做
- 边界条件:

```java
class Solution {
    public int add(int num1, int num2) {
        int sum, carry;
        while (true) {
            sum = num1 ^ num2;
            carry = (num1 & num2) << 1;
            num1 = sum;
            num2 = carry;
            if (num2 == 0) {
                break;
            }
        }
        return num1;
    }
}
```
### 面试题66 构建乘积数组
题目: [Acwing](https://www.acwing.com/problem/content/82/)

- 思路: 不需要用n^2的时间, 拆分成两个部分
- 边界条件:

```java
public class Solution {
    public int[] multiply(int[] A) {
        if (A == null || A.length == 0) return new int[0];
        int[] B = new int[A.length];
        int[] as = new int[A.length];
        int[] ar = new int[A.length];
        for (int i = 0; i < A.length; i++) {
            if (i == 0) as[i] = 1;
            else as[i] = as[i-1] * A[i-1];
        }
        for (int i = A.length-1; i >= 0; i--) {
            if (i == A.length-1) ar[i] = 1;
            else ar[i] = ar[i+1] * A[i+1];
        }
        for (int i = 0; i < A.length; i++) {
            B[i] = as[i] * ar[i];
        }
        return B;
    }
}
```

### 面试题67 把字符串转化为整数
题目: [Acwing](https://www.acwing.com/problem/content/83/)

- 思路: 不难, 但是边界条件, 主要考虑超出int范围时的情况
- 边界条件: "" " " "+" "-" "+1999efe" "-" "-2147483648" "-21474836488"

```java
// 字符串转数值的边界条件一定包括了整型范围
public class Solution {
    public int StrToInt(String str) {
        str = str.trim();
        int start = -1;
        long sum = 0;
        boolean negative = false, first = true;
        if (str == null || str.length() == 0) return 0;
        if (str.charAt(0) == '-') {start++; negative = true;}
        else if (str.charAt(0) == '+') start++;
        while (++start < str.length()) {
            if (str.charAt(start) >= '0' && str.charAt(start) <= '9') {
                if (first && str.charAt(start) == '0') return 0;
                sum = sum * 10 + str.charAt(start) - '0';
                first = false;
            }
            else return 0;
        }
        sum = negative ? -sum : sum;
        if (sum > Integer.MAX_VALUE || sum < Integer.MIN_VALUE) return 0;
        return (int)sum;
    }
}
```

### 面试题68 树中两个节点的最低公共祖先
题目: [Acwing](https://www.acwing.com/problem/content/84/)

- 思路: 路径从根节点一定是相同的, 得到路径后往下找, 不相同的节点
```java
class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        LinkedList<TreeNode> pPath = new LinkedList<>();
        LinkedList<TreeNode> qPath = new LinkedList<>();
        boolean pExists = dfsTree(pPath, root, p);
        boolean qExists = dfsTree(qPath, root, q);
        TreeNode ancestor = null;
        if (!pExists || !qExists) return ancestor;
        while (pPath.size() > 0 && qPath.size() > 0 && pPath.getFirst() == qPath.getFirst()) {
            ancestor = pPath.removeFirst();
            qPath.removeFirst();
        }
        return ancestor;
    }
    private boolean dfsTree(LinkedList<TreeNode> path, TreeNode root, TreeNode target) {
        if (root == null) return false;
        if (dfsTree(path, root.left, target)) {
            path.addFirst(root);
            return true;
        };
        if (root == target) {
            path.addFirst(root);
            return true;
        }
        if (dfsTree(path, root.right, target)) {
            path.addFirst(root);
            return true;
        }
        return false;
    }
}
```
### 57 0到n-1中缺失的数字
一个长度为n-1的递增排序数组中的所有数字都是唯一的，并且每个数字都在范围0到n-1之内。

在范围0到n-1的n个数字中有且只有一个数字不在该数组中，请找出这个数字。

- [x] 独立&&完美
- 思路: 暴力法是O(n)的, 思考有没有更快的方法, 有序所以想到用二分法搜索, 需要四个变量, 索引的左边界, 索引的右边界, 理论上数值的左边界, 数值的右边界, 例如最开始, 索引的左边界是0, 右边界是n-2, 数值的左边界是0, 右边界是n-1. 通过二分法进一步找到索引范围小于理论数值范围的部分, 一直缩小范围到只有数值范围为1, 索引范围为0, 就找到了缺失的数
```java
class Solution {
    public int getMissingNumber(int[] nums) {
        int idL = 0, idR = nums.length-1;
        int lo = 0, hi = nums.length;
        while (idL <= idR) {
            int idMid = (idL + idR) / 2;
            if (nums[idMid]-lo > idMid - idL) { // 缺失的数小于nums[idMid]
                hi = nums[idMid] - 1;
                idR = idMid - 1;
                if (nums[idMid]-lo == 1) return hi;
            }
            else {
                lo = nums[idMid] + 1;
                idL = idMid + 1;
                if (nums[idMid]-lo == 1) return lo;
            }
            idMid = (idL+idR) / 2;
        }
        return hi;
    }
}
```

### 58 数组中数值和下标相等的元素
假设一个单调递增的数组里的每个元素都是整数并且是唯一的。

请编程实现一个函数找出数组中任意一个数值等于其下标的元素。

例如，在数组[-3, -1, 1, 3, 5]中，数字3和它的下标相等。

- [x] 独立&&完美
- 思路: 暴力法能够在O(n)完成, 序列有序, 考虑二分法, 通过举例发现, 如果当前索引的数值小于索引, 则索引左边不可能出现, 若大于则索引右边不可能出现(因为所有数是唯一的)
```java
class Solution {
    public int getNumberSameAsIndex(int[] nums) {
        int left = 0, right = nums.length-1;
        while (left <= right) {
            int mid = (left+right) / 2;
            if (nums[mid] > mid) right = mid-1;
            else if (nums[mid] < mid) left = mid + 1;
            else return mid; 
        }
        return -1;
    }
}
```

