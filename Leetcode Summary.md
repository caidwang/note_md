# LeetCode 刷题总结

主要筛选自[cyc2018题库](https://github.com/CyC2018/CS-Notes/blob/master/notes/Leetcode%20%E9%A2%98%E8%A7%A3%20-%20%E7%9B%AE%E5%BD%95.md), 加上自己的补充

- 算法思想
  - [双指针](leetcodes/leetcode-two-points.md)
  - 排序
  - 贪心思想
  - [二分查找](leetcodes/leetcode-binSearch.md)
  - [分治](leetcodes/leetcode-branch.md)
  - [搜索](leetcodes/leetcode-search.md)
  - [动态规划](leetcodes/leetcode-dp.md)
  - 数学

- 数据结构相关
  - [链表](leetcodes/leetcode-linkedlist.md)
  - [树](leetcodes/leetcode-tree.md)
  - [栈与队列](leetcodes/leetcode-stack&queue.md)
  - [哈希表](leetcodes/leetcode-hash.md)
  - [字符串](leetcodes/leetcode-string.md)
  - [数组与矩阵](leetcodes/leetcode-array-matrix.md)
  - 图
  - 位运算
  - [回文串类型](leetcodes/leetcode-palindrome.md)





**Java 算法题技巧**

- ArrayList<Integer> 和 int[] 的转换
  ```
  int [] ints = list.stream().mapToInt(Integer::intValue).toArray();
  ```
  并不常用, 如果ArrayList的长度事前有办法确定, 尽量不用这样的转换而直接初始化primitive type的数组, stream方法的速度很慢.

- Primitive Type Array 排序
  直接用`Arrays.sort`可以排, 但是逆序的没有办法排, 可以先正序排然后swap成逆序.

- 偶数判断, 偶数判断中, 效率最高的是比较二进制最后一位. 位与的优先级低于`==`因此写法如下
  ```java
  if((x & 1) == 0) // then do something
  ``` 