- [Java 技巧](#java-%e6%8a%80%e5%b7%a7)
- [数组与矩阵](#%e6%95%b0%e7%bb%84%e4%b8%8e%e7%9f%a9%e9%98%b5)
  - [283. Move Zeroes](#283-move-zeroes)
  - [k-Sum类题目 [双指针, Hash, 排序]](#k-sum%e7%b1%bb%e9%a2%98%e7%9b%ae-%e5%8f%8c%e6%8c%87%e9%92%88-hash-%e6%8e%92%e5%ba%8f)
    - [2Sum](#2sum)
    - [3Sum & 4Sum](#3sum--4sum)
  - [119. Pascal's Triangle II [原地迭代]](#119-pascals-triangle-ii-%e5%8e%9f%e5%9c%b0%e8%bf%ad%e4%bb%a3)
  - [844. Backspace String Compare[双指针代替栈]](#844-backspace-string-compare%e5%8f%8c%e6%8c%87%e9%92%88%e4%bb%a3%e6%9b%bf%e6%a0%88)
  - [回文串类型](#%e5%9b%9e%e6%96%87%e4%b8%b2%e7%b1%bb%e5%9e%8b)
    - [234. Palindrome Linked List](#234-palindrome-linked-list)
    - [125. Valid Palindrome](#125-valid-palindrome)
    - [9. Palindrome Number](#9-palindrome-number)
  - [k-diff类型](#k-diff%e7%b1%bb%e5%9e%8b)
    - [532. K-diff Pairs in an Array[双指针]](#532-k-diff-pairs-in-an-array%e5%8f%8c%e6%8c%87%e9%92%88)
- [字符串](#%e5%ad%97%e7%ac%a6%e4%b8%b2)
- [栈与队列](#%e6%a0%88%e4%b8%8e%e9%98%9f%e5%88%97)
- [哈希表](#%e5%93%88%e5%b8%8c%e8%a1%a8)
  - [1002 Find Common Character](#1002-find-common-character)
  - [888. Fair Candy Swap](#888-fair-candy-swap)
- [排序](#%e6%8e%92%e5%ba%8f)
- [图](#%e5%9b%be)
- [动态规划](#%e5%8a%a8%e6%80%81%e8%a7%84%e5%88%92)
- [分治](#%e5%88%86%e6%b2%bb)
  - [Majority Element](#majority-element)

# Java 技巧

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
- 

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

## 844. Backspace String Compare[双指针代替栈]

用指针模拟栈移动, 从序列的尾端往前遍历遇到出栈条件时, 进行记录, 在向前移时消费出栈记录, 当两个栈都没有出栈记录可以消费时, 必须进行比较.

```java
class Solution {
    public boolean backspaceCompare(String S, String T) {
        int cnt1 = 0, cnt2 = 0;
        int ptr1 = S.length() - 1, ptr2 = T.length() - 1;
        while (ptr1 >= 0 && ptr2 >= 0) {
            ptr1 = getCurrentPtr(S, ptr1);
            ptr2 = getCurrentPtr(T, ptr2);
            if (ptr1 >= 0 && ptr2 >= 0) {
                if (S.charAt(ptr1)  != T.charAt(ptr2)) return false;
                ptr1--;
                ptr2--;
            }
        }
        return (getCurrentPtr(S, ptr1) == getCurrentPtr(T, ptr2));
    }
    
    // 栈指针模拟, 反向遍历
    private int getCurrentPtr(String S, int ptr) {
        if (ptr < 0) return ptr;
        int cnt = 0;
        while (cnt > 0 || S.charAt(ptr) == '#') {
                if (S.charAt(ptr) == '#')  {
                    cnt++;
                    ptr--;
                }
                else {
                    ptr--; cnt--;
                }
                if (ptr < 0) break;
        }
        return ptr;
    }
}
```

## 回文串类型
### 234. Palindrome Linked List
链表回文串的通用思路:

对前半段进行翻转然后进行比较, 关键在于翻转操作, 翻转操作有以下要点:
- 处理好0和1的情况
- 处理好长度奇偶的情况
- 翻转一个节点需要3个指针, 分别指向翻转点前一个和后一个
- 最后来处理头结点的问题

```java
class Solution {
    public boolean isPalindrome(ListNode head) {
        if (head == null || head.next ==null) return true;
        int len = 0;
        ListNode ptr = head;
        while (ptr != null) {
            len ++;
            ptr = ptr.next;
        }
        ptr = head;
        ListNode root = ptr.next;
        ListNode temp = root.next;

        for (int i = 0; i < len / 2 - 1; i++)  {
            root.next = ptr;
            ptr = root;
            root = temp;
            temp = temp.next;
        }
        head.next = null;
        if (len % 2 == 1) root = temp;
        while (root != null && ptr != null) {
            if (root.val != ptr.val) return false;
            root = root.next; 
            ptr = ptr.next;
        }
        return true;
    }
}
```
### 125. Valid Palindrome 
字符串回文串的基本思路:

双指针比较两头的字符.
- 处理0的情况
- 转换成char的数组
- 双指针遍历

```java
class Solution {
    public boolean isPalindrome(String s) {
        if (s.length() == 0) return true;
        int i = 0, j = s.length() - 1;
        char[] a = s.toCharArray();
        while (i < j) {
            while(!isChar(a[i]) && i < j) i++;
            while(!isChar(a[j]) && i < j) j--;
            if (Character.toLowerCase(a[i]) != Character.toLowerCase(a[j])) return false;
            i ++;
            j--;
        }
        return true;
    }
    private static boolean isChar(char x) {
        return (x >= 'a' && x <= 'z') || (x >= 'A' && x <= 'Z') || (x >= '0' && x <= '9');
    }
}
```

### 9. Palindrome Number
数字回文串的基本思路:

对前半段数字进行翻转, 构建新的数字进行比较. 注意事项如下:
- 结尾为0的数字不会是回文串, 但是0除外
- 考虑负号时, 负数不会是回文串
- 翻转整段数字可能导致超过最大整型数
  
```java
class Solution {
    public boolean isPalindrome(int x) {
        if (x < 0 || (x %10 == 0 && x != 0)) return false;
        int revert = 0;
        while (x > revert) {
            revert  = revert * 10 + x % 10;
            x /= 10;
        }
        return (x == revert) || (x == revert / 10);
    }
}
```
## k-diff类型
k-diff类型给定一个数组判断数组中两个元素之差小于等于k或只等于k的数量.

### 532. K-diff Pairs in an Array[双指针]

这道题的关键是想到排序才能解决.
```java
class Solution {
    public int findPairs(int[] nums, int k) {
        if (nums.length < 2 && k < 0) return 0;
        Arrays.sort(nums);
        int i = 0, j = 1, ret = 0;
        while (i < nums.length && j < nums.length) {
            if (nums[j] - nums[i] < k) j++;
            else if (nums[j] - nums[i] > k) i++;
            else  {
                if (i != j) {
                ret += 1;
                i++;
                while (i < nums.length && nums[i] == nums[i-1]) i++;
                }
                else j++;
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
