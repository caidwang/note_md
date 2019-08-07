- [数组与矩阵](#数组与矩阵)
  - [283. Move Zeroes](#283-move-zeroes)
  - [k-Sum类题目 [双指针, Hash, 排序]](#k-sum类题目-双指针-hash-排序)
    - [2Sum](#2sum)
    - [3Sum & 4Sum](#3sum--4sum)
  - [119. Pascal's Triangle II [原地迭代]](#119-pascals-triangle-ii-原地迭代)
- [字符串](#字符串)
- [栈与队列](#栈与队列)
- [哈希表](#哈希表)
  - [1002 Find Common Character](#1002-find-common-character)
  - [888. Fair Candy Swap](#888-fair-candy-swap)
- [排序](#排序)
- [图](#图)
- [动态规划](#动态规划)
- [分治](#分治)
  - [Majority Element](#majority-element)

# 数组与矩阵

## 283. Move Zeroes

注意全零的边界条件

```java
class Solution {
    public void moveZeroes(int[] nums) {
        int idx = 0;
        for (int i = 0; i < nums.length; i++) {
            if (nums[i]! = 0) {
                nums[idx++] = nums[i];
            }
        }
        while (idx < nums.length) {
            nums[idx++] = 0;
        }
    }
}
```

## k-Sum类题目 [双指针, Hash, 排序]
k-sum类型是以2-sum为基础的变种和拓展, 包括k发生变化(2,3,4), 初始序列是否有序, 输出类型(true/false, 成立的下标, 子集的集合).
### 2Sum
对于2 Sum而言, 暴力算法的时间复杂度为$O(n^2)$, 更好的解法有:
- 若序列有序, 可以设置双指针从首尾向中间移动, 时间复杂度为O(n); 
- 若无序, 考虑以O(n)对序列建立hash表(使用STL的map), 之后以O(1)的复杂度判断是否有解
- 也可以边hash边检查当前数字和hash表中已有的元素是否能够构成解

综上, 2sum问题的时间复杂度为O(n)
> 采用hash表时,注意存在多个相同元素时的覆盖问题和自己和自己相加等于target的问题, 这种情况, 先检查已有元素, 再将当前数字加入hash表
### 3Sum & 4Sum
对于3Sum及以上, 暴力算法的时间复杂度都在$O(n^2)$以上, 因此首先对序列进行排序的方法是可接受的.排序后, 固定部分元素将问题转化为有序序列的2Sum问题. 这类题目的输出类型常为所有可能的子集的集合, 对于一个加数相同的数字只使用一次, 不同的加数可以相等, 这类题目的另一个重要的提高速度的方法是, 寻找合适的条件剪枝, 例如3sum中, 最小的三个数之和大于target或者最大三个数之和小于target的情况可以直接剪枝.

## 119. Pascal's Triangle II [原地迭代]
注意问题:
1. 如果完全建一棵树出来, 可以做, 但是空间开销过大, 是k^2级的, 因此不可行
2. 如果使用二项式公式, 当k较大时会上溢, 在k=21时就已经不行了, 阶乘很容易爆, 基本不要用.
3. 最终的策略是原地迭代. 可以把每行新加的一个元素放在头上, 则当前元素更新需要用到的位置就是当前位置的值和下一个位置的值, 可行. 但是不能够将新加的元素放在尾上.

```java
class Solution {
    public List<Integer> getRow(int rowIndex) {
        List<Integer> ret = new ArrayList<>();
        if (rowIndex < 0) return ret;
        for (int i = 0; i <= rowIndex; i++) {
            ret.add(0, 1);
            for (int j = 1; j < i; j++) {
                ret.set(j, ret.get(j) + ret.get(j+1));
            }
        }
        return ret;
    }
}
```




# 字符串

# 栈与队列

# 哈希表

## 1002 Find Common Character

总体思路是对的, 使用两个map结构分别记录总体的字符出现数量和当前string 的字符出现数量, 去两者中小的. 这里能够取巧的是范围是小写字母, 因此可以用int[26]代替Map记录, 比较两个结构和记录的时候速度都更快. 修改后的结果:
```java
class Solution {
    public List<String> commonChars(String[] A) {
        List<String> ans = new ArrayList<>();
        int[] count = new int[26]; 
        Arrays.fill(count, Integer.MAX_VALUE);
        for (String a : A) {
            int[] t = new int[26];
            for (char c : a.toCharArray()) { 
                t[c - 'a']++; 
            }
            for (int i = 0; i < 26; ++i) {
                count[i] = Math.min(t[i], count[i]);
            }
        }
        for (int i = 0; i < 26; ++i) {
             if (count[i] == Integer.MAX_VALUE) 
                 continue;
             while (count[i]> 0) { 
                 ans.add("" + (char)(i + 'a')); 
                 count[i]--;
             }
        }
        return ans;
    }
}
```

## 888. Fair Candy Swap

这道题可以先排序再用双指针从头开始扫, 但是这样的性能不是最好的, 可以对B哈希.

```java
class Solution {
    public int[] fairCandySwap(int[] A, int[] B) {
        int[] ans = new int[2];
        int sumA = 0, sumB = 0, diff;
        for (int i: A) sumA += i;
        boolean[] hashtable = new boolean[100001];
        for (int i: B) {
            sumB += i;
            hashtable[i] = true;
        }
        diff = (sumA - sumB) / 2;
        for (int i: A) {
            // 你这个问题非常大, 写一个下标不考虑下标的范围么??!!!
            if (i - diff > 0 && i - diff <= 100000 && hashtable[i - diff]) {
                ans[0] = i;
                ans[1] = i - diff;
                break;
            }
        }
        return ans;
    }
}
```

# 排序

# 图

# 动态规划

# 分治

## Majority Element
Moore's voting最大投票算法, [算法介绍](https://blog.csdn.net/huanghanqian/article/details/74188349) 使用的是分治思想, 即如果当`count`降为零时, 说明在前面的子序列中不存在超过1/k的元素.

**169. Majority Element**

基本的思路是可以拿map做, 但是这里精巧之处在于超过n/2, 也就是说, 所有其他的都没有它一个人加起来多, 因此可以用它和其他数字抵消, 来达到count最后能为正数的元素的效果.
```java
class Solution {
    public int majorityElement(int[] nums) {
        int count = 0, candidate = nums[0];
        for (int i : nums) {
            if (i == candidate) count++;
            else {
                if (count == 0) {
                    count = 1;
                    candidate = i;
                }
                else count--;
            }
        }
        return candidate;
    }
}
```

**229. Majority Element II**

上一题的扩展, 对于n/3的情形, 最多只有可能有两个元素, 和上一题的思路类似, 记录两个元素, `cnt`记录了当前元素需要配对的数量, 如果出现了两个元素以外的元素, 则构成一个三元对, 能够消除. 需要注意的点:
若列表中只有一种元素怎么处理; 虽然`candidate`有值, 但是可能只是在子列中超过三分之一, 需要最后遍历一遍进行检查.

```java
class Solution {
    public List<Integer> majorityElement(int[] nums) {
        List<Integer> ret = new ArrayList<>();
        if (nums.length == 0) return ret;
        int candidate1 = nums[0], candidate2 = nums[0];
        int cnt1 = 0; int cnt2 = 0;
        int n = nums.length;
        for (int v : nums) {
            if (v == candidate1) {
                cnt1++;
            }
            else if (v == candidate2) {
                cnt2++;
            }
            else if (cnt1 == 0) {
                candidate1 = v;
                cnt1 = 1;
            }
            else if (cnt2 == 0) {
                candidate2 = v;
                cnt2 = 1;
            }
            else {
                cnt1--;
                cnt2--;
            }
        }
        cnt1 = 0;
        cnt2 = 0;
        for (int v : nums) {
            if (v == candidate1) cnt1++;
            if (v == candidate2) cnt2++;
        }
        if (cnt1 > n / 3) ret.add(candidate1);
        if (candidate2 != candidate1 && cnt2 > n / 3) ret.add(candidate2);
        
        return ret;
    }
}
```
