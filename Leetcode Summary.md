- [Java 技巧](#java-%e6%8a%80%e5%b7%a7)
- [算法思想](#%e7%ae%97%e6%b3%95%e6%80%9d%e6%83%b3)
  - [双指针](#%e5%8f%8c%e6%8c%87%e9%92%88)
    - [有序2-SUM](#%e6%9c%89%e5%ba%8f2-sum)
    - [k-diff](#k-diff)
      - [532. K-diff Pairs in an Array](#532-k-diff-pairs-in-an-array)
    - [双指针代替栈](#%e5%8f%8c%e6%8c%87%e9%92%88%e4%bb%a3%e6%9b%bf%e6%a0%88)
    - [2. 两数平方和](#2-%e4%b8%a4%e6%95%b0%e5%b9%b3%e6%96%b9%e5%92%8c)
    - [3. 反转字符串中的元音字符](#3-%e5%8f%8d%e8%bd%ac%e5%ad%97%e7%ac%a6%e4%b8%b2%e4%b8%ad%e7%9a%84%e5%85%83%e9%9f%b3%e5%ad%97%e7%ac%a6)
    - [4. 回文字符串](#4-%e5%9b%9e%e6%96%87%e5%ad%97%e7%ac%a6%e4%b8%b2)
    - [5. 归并两个有序数组](#5-%e5%bd%92%e5%b9%b6%e4%b8%a4%e4%b8%aa%e6%9c%89%e5%ba%8f%e6%95%b0%e7%bb%84)
    - [6. 判断链表是否存在环](#6-%e5%88%a4%e6%96%ad%e9%93%be%e8%a1%a8%e6%98%af%e5%90%a6%e5%ad%98%e5%9c%a8%e7%8e%af)
    - [7. 最长子序列](#7-%e6%9c%80%e9%95%bf%e5%ad%90%e5%ba%8f%e5%88%97)
  - [排序](#%e6%8e%92%e5%ba%8f)
  - [贪心思想](#%e8%b4%aa%e5%bf%83%e6%80%9d%e6%83%b3)
  - [二分查找](#%e4%ba%8c%e5%88%86%e6%9f%a5%e6%89%be)
  - [分治](#%e5%88%86%e6%b2%bb)
    - [Majority Element](#majority-element)
      - [169. Majority Element](#169-majority-element)
      - [229. Majority Element II](#229-majority-element-ii)
  - [搜索](#%e6%90%9c%e7%b4%a2)
  - [动态规划](#%e5%8a%a8%e6%80%81%e8%a7%84%e5%88%92)
  - [数学](#%e6%95%b0%e5%ad%a6)
- [数据结构相关](#%e6%95%b0%e6%8d%ae%e7%bb%93%e6%9e%84%e7%9b%b8%e5%85%b3)
  - [链表](#%e9%93%be%e8%a1%a8)
  - [树](#%e6%a0%91)
  - [栈与队列](#%e6%a0%88%e4%b8%8e%e9%98%9f%e5%88%97)
  - [哈希表](#%e5%93%88%e5%b8%8c%e8%a1%a8)
    - [1002 Find Common Character](#1002-find-common-character)
    - [888. Fair Candy Swap](#888-fair-candy-swap)
    - [2. 判断数组是否含有重复元素](#2-%e5%88%a4%e6%96%ad%e6%95%b0%e7%bb%84%e6%98%af%e5%90%a6%e5%90%ab%e6%9c%89%e9%87%8d%e5%a4%8d%e5%85%83%e7%b4%a0)
    - [3. 最长和谐序列](#3-%e6%9c%80%e9%95%bf%e5%92%8c%e8%b0%90%e5%ba%8f%e5%88%97)
    - [4. 最长连续序列](#4-%e6%9c%80%e9%95%bf%e8%bf%9e%e7%bb%ad%e5%ba%8f%e5%88%97)
  - [字符串](#%e5%ad%97%e7%ac%a6%e4%b8%b2)
      - [1. 字符串循环移位包含](#1-%e5%ad%97%e7%ac%a6%e4%b8%b2%e5%be%aa%e7%8e%af%e7%a7%bb%e4%bd%8d%e5%8c%85%e5%90%ab)
      - [2. 字符串循环移位](#2-%e5%ad%97%e7%ac%a6%e4%b8%b2%e5%be%aa%e7%8e%af%e7%a7%bb%e4%bd%8d)
      - [3. 字符串中单词的翻转](#3-%e5%ad%97%e7%ac%a6%e4%b8%b2%e4%b8%ad%e5%8d%95%e8%af%8d%e7%9a%84%e7%bf%bb%e8%bd%ac)
      - [4. 两个字符串包含的字符是否完全相同](#4-%e4%b8%a4%e4%b8%aa%e5%ad%97%e7%ac%a6%e4%b8%b2%e5%8c%85%e5%90%ab%e7%9a%84%e5%ad%97%e7%ac%a6%e6%98%af%e5%90%a6%e5%ae%8c%e5%85%a8%e7%9b%b8%e5%90%8c)
      - [5. 计算一组字符集合可以组成的回文字符串的最大长度](#5-%e8%ae%a1%e7%ae%97%e4%b8%80%e7%bb%84%e5%ad%97%e7%ac%a6%e9%9b%86%e5%90%88%e5%8f%af%e4%bb%a5%e7%bb%84%e6%88%90%e7%9a%84%e5%9b%9e%e6%96%87%e5%ad%97%e7%ac%a6%e4%b8%b2%e7%9a%84%e6%9c%80%e5%a4%a7%e9%95%bf%e5%ba%a6)
      - [6. 字符串同构](#6-%e5%ad%97%e7%ac%a6%e4%b8%b2%e5%90%8c%e6%9e%84)
      - [7. 回文子字符串个数](#7-%e5%9b%9e%e6%96%87%e5%ad%90%e5%ad%97%e7%ac%a6%e4%b8%b2%e4%b8%aa%e6%95%b0)
      - [8. 判断一个整数是否是回文数](#8-%e5%88%a4%e6%96%ad%e4%b8%80%e4%b8%aa%e6%95%b4%e6%95%b0%e6%98%af%e5%90%a6%e6%98%af%e5%9b%9e%e6%96%87%e6%95%b0)
      - [9. 统计二进制字符串中连续 1 和连续 0 数量相同的子字符串个数](#9-%e7%bb%9f%e8%ae%a1%e4%ba%8c%e8%bf%9b%e5%88%b6%e5%ad%97%e7%ac%a6%e4%b8%b2%e4%b8%ad%e8%bf%9e%e7%bb%ad-1-%e5%92%8c%e8%bf%9e%e7%bb%ad-0-%e6%95%b0%e9%87%8f%e7%9b%b8%e5%90%8c%e7%9a%84%e5%ad%90%e5%ad%97%e7%ac%a6%e4%b8%b2%e4%b8%aa%e6%95%b0)
  - [数组与矩阵](#%e6%95%b0%e7%bb%84%e4%b8%8e%e7%9f%a9%e9%98%b5)
    - [283. Move Zeroes](#283-move-zeroes)
    - [k-Sum类题目 [双指针, Hash, 排序]](#k-sum%e7%b1%bb%e9%a2%98%e7%9b%ae-%e5%8f%8c%e6%8c%87%e9%92%88-hash-%e6%8e%92%e5%ba%8f)
      - [2Sum](#2sum)
      - [3Sum & 4Sum](#3sum--4sum)
    - [119. Pascal's Triangle II [原地迭代]](#119-pascals-triangle-ii-%e5%8e%9f%e5%9c%b0%e8%bf%ad%e4%bb%a3)
    - [844. Backspace String Compare[双指针代替栈]](#844-backspace-string-compare%e5%8f%8c%e6%8c%87%e9%92%88%e4%bb%a3%e6%9b%bf%e6%a0%88)
  - [图](#%e5%9b%be)
  - [位运算](#%e4%bd%8d%e8%bf%90%e7%ae%97)
  - [回文串类型](#%e5%9b%9e%e6%96%87%e4%b8%b2%e7%b1%bb%e5%9e%8b)
    - [234. Palindrome Linked List](#234-palindrome-linked-list)
    - [125. Valid Palindrome](#125-valid-palindrome)
    - [9. Palindrome Number](#9-palindrome-number)

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

# 算法思想
## 双指针
双指针主要用于遍历数组，两个指针指向不同的元素，从而协同完成任务。

双指针分为两种情况, 一种是搜索一种是交换. 

搜索又包括了一左一右向中间搜索, 和两个都从左边出发向右边搜索. 双指针搜索的前提是有序, 如果无序可以考虑先排序或用hash. 搜索时通常只有一层while循环, 因此边界条件相对简单, 需要处理的就是元素重复的问题. 

交换的情况稍微复杂一些, 因为有一个外循环和一个寻找条件符合的内循环(也可以用一层循环, 但是每次移动一格效率更低), 如果采用两层循环, 需要处理内层边界条件的问题, 可以参考快排的切分实现, 模板如下:
```java
while (left < right) {
    while (valid(array[++left])) // 采用++a的形式避免卡在!valid的位置 
        {if (left == array.length-1) break;} // 需要哨兵
    while (valid(array[--right])) {if (right == 0) break;}
    if (left >= right) break;
    exch(array, left, right);
}
```

双指针最常见的两种模式是快慢指针和首尾向中间移动.

### 有序2-SUM
[2-sum问题](#2sum)

### k-diff
k-diff类型给定一个数组判断数组中两个元素之差小于等于k或只等于k的数量.

#### 532. K-diff Pairs in an Array
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
                i++; // 如果有重复计数
                while (i < nums.length && nums[i] == nums[i-1]) i++;
                }
                else j++;
            }
        }
        return ret;
    }    
}
```

### 双指针代替栈
[844. Backspace String Compare](#844-backspace-string-compare%e5%8f%8c%e6%8c%87%e9%92%88%e4%bb%a3%e6%9b%bf%e6%a0%88)



### 2. 两数平方和

633\. Sum of Square Numbers (Easy)

[Leetcode](https://leetcode.com/problems/sum-of-square-numbers/description/) / [力扣](https://leetcode-cn.com/problems/sum-of-square-numbers/description/)

```html
Input: 5
Output: True
Explanation: 1 * 1 + 2 * 2 = 5
```

题目描述：判断一个非负整数是否为两个整数的平方和。

可以看成是在元素为 0\~target 的有序数组中查找两个数，使得这两个数的平方和为 target，如果能找到，则返回 true，表示 target 是两个整数的平方和。

本题和 167\. Two Sum II - Input array is sorted 类似，只有一个明显区别：一个是和为 target，一个是平方和为 target。本题同样可以使用双指针得到两个数，使其平方和为 target。

本题的关键是右指针的初始化，实现剪枝，从而降低时间复杂度。设右指针为 x，左指针固定为 0，为了使 0<sup>2</sup> + x<sup>2</sup> 的值尽可能接近 target，我们可以将 x 取为 sqrt(target)。

因为最多只需要遍历一次 0\~sqrt(target)，所以时间复杂度为 O(sqrt(target))。又因为只使用了两个额外的变量，因此空间复杂度为 O(1)。

```java
 public boolean judgeSquareSum(int target) {
     if (target < 0) return false;
     int i = 0, j = (int) Math.sqrt(target);
     while (i <= j) {
         int powSum = i * i + j * j;
         if (powSum == target) {
             return true;
         } else if (powSum > target) {
             j--;
         } else {
             i++;
         }
     }
     return false;
 }
```

### 3. 反转字符串中的元音字符

345\. Reverse Vowels of a String (Easy)

[Leetcode](https://leetcode.com/problems/reverse-vowels-of-a-string/description/) / [力扣](https://leetcode-cn.com/problems/reverse-vowels-of-a-string/description/)

```html
Given s = "leetcode", return "leotcede".
```

<div align="center"> <img src="https://cs-notes-1256109796.cos.ap-guangzhou.myqcloud.com/a7cb8423-895d-4975-8ef8-662a0029c772.png" width="400px"> </div><br>

使用双指针，一个指针从头向尾遍历，一个指针从尾到头遍历，当两个指针都遍历到元音字符时，交换这两个元音字符。

为了快速判断一个字符是不是元音字符，我们将全部元音字符添加到集合 HashSet 中，从而以 O(1) 的时间复杂度进行该操作。

- 时间复杂度为 O(N)：只需要遍历所有元素一次
- 空间复杂度 O(1)：只需要使用两个额外变量

<div align="center"> <img src="https://cs-notes-1256109796.cos.ap-guangzhou.myqcloud.com/ef25ff7c-0f63-420d-8b30-eafbeea35d11.gif" width="400px"> </div><br>

```java
private final static HashSet<Character> vowels = new HashSet<>(
        Arrays.asList('a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U'));

public String reverseVowels(String s) {
    if (s == null) return null;
    int i = 0, j = s.length() - 1;
    char[] result = new char[s.length()];
    while (i <= j) {
        char ci = s.charAt(i);
        char cj = s.charAt(j);
        if (!vowels.contains(ci)) {
            result[i++] = ci;
        } else if (!vowels.contains(cj)) {
            result[j--] = cj;
        } else {
            result[i++] = cj;
            result[j--] = ci;
        }
    }
    return new String(result);
}
```

### 4. 回文字符串

680\. Valid Palindrome II (Easy)

[Leetcode](https://leetcode.com/problems/valid-palindrome-ii/description/) / [力扣](https://leetcode-cn.com/problems/valid-palindrome-ii/description/)

```html
Input: "abca"
Output: True
Explanation: You could delete the character 'c'.
```

题目描述：可以删除一个字符，判断是否能构成回文字符串。

所谓的回文字符串，是指具有左右对称特点的字符串，例如 "abcba" 就是一个回文字符串。

使用双指针可以很容易判断一个字符串是否是回文字符串：令一个指针从左到右遍历，一个指针从右到左遍历，这两个指针同时移动一个位置，每次都判断两个指针指向的字符是否相同，如果都相同，字符串才是具有左右对称性质的回文字符串。

<div align="center"> <img src="https://cs-notes-1256109796.cos.ap-guangzhou.myqcloud.com/fcc941ec-134b-4dcd-bc86-1702fd305300.gif" width="250px"> </div><br>

本题的关键是处理删除一个字符。在使用双指针遍历字符串时，如果出现两个指针指向的字符不相等的情况，我们就试着删除一个字符，再判断删除完之后的字符串是否是回文字符串。

在判断是否为回文字符串时，我们不需要判断整个字符串，因为左指针左边和右指针右边的字符之前已经判断过具有对称性质，所以只需要判断中间的子字符串即可。

在试着删除字符时，我们既可以删除左指针指向的字符，也可以删除右指针指向的字符。

<div align="center"> <img src="https://cs-notes-1256109796.cos.ap-guangzhou.myqcloud.com/db5f30a7-8bfa-4ecc-ab5d-747c77818964.gif" width="300px"> </div><br>

```java
public boolean validPalindrome(String s) {
    for (int i = 0, j = s.length() - 1; i < j; i++, j--) {
        if (s.charAt(i) != s.charAt(j)) {
            return isPalindrome(s, i, j - 1) || isPalindrome(s, i + 1, j);
        }
    }
    return true;
}

private boolean isPalindrome(String s, int i, int j) {
    while (i < j) {
        if (s.charAt(i++) != s.charAt(j--)) {
            return false;
        }
    }
    return true;
}
```

### 5. 归并两个有序数组

88\. Merge Sorted Array (Easy)

[Leetcode](https://leetcode.com/problems/merge-sorted-array/description/) / [力扣](https://leetcode-cn.com/problems/merge-sorted-array/description/)

```html
Input:
nums1 = [1,2,3,0,0,0], m = 3
nums2 = [2,5,6],       n = 3

Output: [1,2,2,3,5,6]
```

题目描述：把归并结果存到第一个数组上。

需要从尾开始遍历，否则在 nums1 上归并得到的值会覆盖还未进行归并比较的值。

```java
public void merge(int[] nums1, int m, int[] nums2, int n) {
    int index1 = m - 1, index2 = n - 1;
    int indexMerge = m + n - 1;
    while (index1 >= 0 || index2 >= 0) {
        if (index1 < 0) {
            nums1[indexMerge--] = nums2[index2--];
        } else if (index2 < 0) {
            nums1[indexMerge--] = nums1[index1--];
        } else if (nums1[index1] > nums2[index2]) {
            nums1[indexMerge--] = nums1[index1--];
        } else {
            nums1[indexMerge--] = nums2[index2--];
        }
    }
}
```

### 6. 判断链表是否存在环

141\. Linked List Cycle (Easy)

[Leetcode](https://leetcode.com/problems/linked-list-cycle/description/) / [力扣](https://leetcode-cn.com/problems/linked-list-cycle/description/)

使用双指针，一个指针每次移动一个节点，一个指针每次移动两个节点，如果存在环，那么这两个指针一定会相遇。

```java
public boolean hasCycle(ListNode head) {
    if (head == null) {
        return false;
    }
    ListNode l1 = head, l2 = head.next;
    while (l1 != null && l2 != null && l2.next != null) {
        if (l1 == l2) {
            return true;
        }
        l1 = l1.next;
        l2 = l2.next.next;
    }
    return false;
}
```

### 7. 最长子序列

524\. Longest Word in Dictionary through Deleting (Medium)

[Leetcode](https://leetcode.com/problems/longest-word-in-dictionary-through-deleting/description/) / [力扣](https://leetcode-cn.com/problems/longest-word-in-dictionary-through-deleting/description/)

```
Input:
s = "abpcplea", d = ["ale","apple","monkey","plea"]

Output:
"apple"
```

题目描述：删除 s 中的一些字符，使得它构成字符串列表 d 中的一个字符串，找出能构成的最长字符串。如果有多个相同长度的结果，返回字典序的最小字符串。

通过删除字符串 s 中的一个字符能得到字符串 t，可以认为 t 是 s 的子序列，我们可以使用双指针来判断一个字符串是否为另一个字符串的子序列。

```java
public String findLongestWord(String s, List<String> d) {
    String longestWord = "";
    for (String target : d) {
        int l1 = longestWord.length(), l2 = target.length();
        if (l1 > l2 || (l1 == l2 && longestWord.compareTo(target) < 0)) {
            continue;
        }
        if (isSubstr(s, target)) {
            longestWord = target;
        }
    }
    return longestWord;
}

private boolean isSubstr(String s, String target) {
    int i = 0, j = 0;
    while (i < s.length() && j < target.length()) {
        if (s.charAt(i) == target.charAt(j)) {
            j++;
        }
        i++;
    }
    return j == target.length();
}
```

## 排序

## 贪心思想

## 二分查找

## 分治
### Majority Element
Moore's voting最大投票算法, [算法介绍](https://blog.csdn.net/huanghanqian/article/details/74188349) 使用的是分治思想, 即如果当`count`降为零时, 说明在前面的子序列中不存在超过1/k的元素.

#### 169. Majority Element
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

#### 229. Majority Element II

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


## 搜索

## 动态规划

## 数学

# 数据结构相关
## 链表

## 树

## 栈与队列

## 哈希表
### 1002 Find Common Character

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

### 888. Fair Candy Swap

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

哈希表使用 O(N) 空间复杂度存储数据，并且以 O(1) 时间复杂度求解问题。

- Java 中的   **HashSet**   用于存储一个集合，可以查找元素是否在集合中。如果元素有穷，并且范围不大，那么可以用一个布尔数组来存储一个元素是否存在。例如对于只有小写字符的元素，就可以用一个长度为 26 的布尔数组来存储一个字符集合，使得空间复杂度降低为 O(1)。

 Java 中的   **HashMap**   主要用于映射关系，从而把两个元素联系起来。HashMap 也可以用来对元素进行计数统计，此时键为元素，值为计数。和 HashSet 类似，如果元素有穷并且范围不大，可以用整型数组来进行统计。在对一个内容进行压缩或者其它转换时，利用 HashMap 可以把原始内容和转换后的内容联系起来。例如在一个简化 url 的系统中 [Leetcdoe : 535. Encode and Decode TinyURL (Medium)

[Leetcode](https://leetcode.com/problems/encode-and-decode-tinyurl/description/)，利用 HashMap 就可以存储精简后的 url 到原始 url 的映射，使得不仅可以显示简化的 url，也可以根据简化的 url 得到原始 url 从而定位到正确的资源�) / [力扣](https://leetcode-cn.com/problems/encode-and-decode-tinyurl/description/)，利用 HashMap 就可以存储精简后的 url 到原始 url 的映射，使得不仅可以显示简化的 url，也可以根据简化的 url 得到原始 url 从而定位到正确的资源�)


###1. 数组中两个数的和为给定值

1\. Two Sum (Easy)

[Leetcode](https://leetcode.com/problems/two-sum/description/) / [力扣](https://leetcode-cn.com/problems/two-sum/description/)

可以先对数组进行排序，然后使用双指针方法或者二分查找方法。这样做的时间复杂度为 O(NlogN)，空间复杂度为 O(1)。

用 HashMap 存储数组元素和索引的映射，在访问到 nums[i] 时，判断 HashMap 中是否存在 target - nums[i]，如果存在说明 target - nums[i] 所在的索引和 i 就是要找的两个数。该方法的时间复杂度为 O(N)，空间复杂度为 O(N)，使用空间来换取时间。

```java
public int[] twoSum(int[] nums, int target) {
    HashMap<Integer, Integer> indexForNum = new HashMap<>();
    for (int i = 0; i < nums.length; i++) {
        if (indexForNum.containsKey(target - nums[i])) {
            return new int[]{indexForNum.get(target - nums[i]), i};
        } else {
            indexForNum.put(nums[i], i);
        }
    }
    return null;
}
```

### 2. 判断数组是否含有重复元素

217\. Contains Duplicate (Easy)

[Leetcode](https://leetcode.com/problems/contains-duplicate/description/) / [力扣](https://leetcode-cn.com/problems/contains-duplicate/description/)

```java
public boolean containsDuplicate(int[] nums) {
    Set<Integer> set = new HashSet<>();
    for (int num : nums) {
        set.add(num);
    }
    return set.size() < nums.length;
}
```

### 3. 最长和谐序列

594\. Longest Harmonious Subsequence (Easy)

[Leetcode](https://leetcode.com/problems/longest-harmonious-subsequence/description/) / [力扣](https://leetcode-cn.com/problems/longest-harmonious-subsequence/description/)

```html
Input: [1,3,2,2,5,2,3,7]
Output: 5
Explanation: The longest harmonious subsequence is [3,2,2,2,3].
```

和谐序列中最大数和最小数之差正好为 1，应该注意的是序列的元素不一定是数组的连续元素。

```java
public int findLHS(int[] nums) {
    Map<Integer, Integer> countForNum = new HashMap<>();
    for (int num : nums) {
        countForNum.put(num, countForNum.getOrDefault(num, 0) + 1);
    }
    int longest = 0;
    for (int num : countForNum.keySet()) {
        if (countForNum.containsKey(num + 1)) {
            longest = Math.max(longest, countForNum.get(num + 1) + countForNum.get(num));
        }
    }
    return longest;
}
```

### 4. 最长连续序列

128\. Longest Consecutive Sequence (Hard)

[Leetcode](https://leetcode.com/problems/longest-consecutive-sequence/description/) / [力扣](https://leetcode-cn.com/problems/longest-consecutive-sequence/description/)

```html
Given [100, 4, 200, 1, 3, 2],
The longest consecutive elements sequence is [1, 2, 3, 4]. Return its length: 4.
```

要求以 O(N) 的时间复杂度求解。

```java
class Solution {
    public int longestConsecutive(int[] nums) {
        if (nums == null || nums.length ==0 ) return 0;
        HashSet<Integer> set = new HashSet<>();
        for (int i : nums) {
            set.add(i);
        }
        int longest = 0;
        boolean incr = true;
        while (!set.isEmpty()) {
            Iterator<Integer> it = set.iterator();
            int cur = it.next(), temp = 1;
            int left = cur, right = cur;
            while (set.contains(++right)) {set.remove(right); temp++;}
            while (set.contains(--left)) {set.remove(left); temp++;}
            set.remove(cur);
            if (temp > longest) longest = temp;
        }
        return longest;
    }
}
```


## 字符串

#### 1. 字符串循环移位包含

[编程之美 3.1](#)

```html
s1 = AABCD, s2 = CDAA
Return : true
```

给定两个字符串 s1 和 s2，要求判定 s2 是否能够被 s1 做循环移位得到的字符串包含。

s1 进行循环移位的结果是 s1s1 的子字符串，因此只要判断 s2 是否是 s1s1 的子字符串即可。

#### 2. 字符串循环移位

[编程之美 2.17](#)

```html
s = "abcd123" k = 3
Return "123abcd"
```

将字符串向右循环移动 k 位。

将 abcd123 中的 abcd 和 123 单独翻转，得到 dcba321，然后对整个字符串进行翻转，得到 123abcd。

#### 3. 字符串中单词的翻转

[程序员代码面试指南](#)

```html
s = "I am a student"
Return "student a am I"
```

将每个单词翻转，然后将整个字符串翻转。

#### 4. 两个字符串包含的字符是否完全相同

242\. Valid Anagram (Easy)

[Leetcode](https://leetcode.com/problems/valid-anagram/description/) / [力扣](https://leetcode-cn.com/problems/valid-anagram/description/)

```html
s = "anagram", t = "nagaram", return true.
s = "rat", t = "car", return false.
```

可以用 HashMap 来映射字符与出现次数，然后比较两个字符串出现的字符数量是否相同。

由于本题的字符串只包含 26 个小写字符，因此可以使用长度为 26 的整型数组对字符串出现的字符进行统计，不再使用 HashMap。

```java
public boolean isAnagram(String s, String t) {
    int[] cnts = new int[26];
    for (char c : s.toCharArray()) {
        cnts[c - 'a']++;
    }
    for (char c : t.toCharArray()) {
        cnts[c - 'a']--;
    }
    for (int cnt : cnts) {
        if (cnt != 0) {
            return false;
        }
    }
    return true;
}
```

#### 5. 计算一组字符集合可以组成的回文字符串的最大长度

409\. Longest Palindrome (Easy)

[Leetcode](https://leetcode.com/problems/longest-palindrome/description/) / [力扣](https://leetcode-cn.com/problems/longest-palindrome/description/)

```html
Input : "abccccdd"
Output : 7
Explanation : One longest palindrome that can be built is "dccaccd", whose length is 7.
```

使用长度为 256 的整型数组来统计每个字符出现的个数，每个字符有偶数个可以用来构成回文字符串。

因为回文字符串最中间的那个字符可以单独出现，所以如果有单独的字符就把它放到最中间。

```java
public int longestPalindrome(String s) {
    int[] cnts = new int[256];
    for (char c : s.toCharArray()) {
        cnts[c]++;
    }
    int palindrome = 0;
    for (int cnt : cnts) {
        palindrome += (cnt / 2) * 2;
    }
    if (palindrome < s.length()) {
        palindrome++;   // 这个条件下 s 中一定有单个未使用的字符存在，可以把这个字符放到回文的最中间
    }
    return palindrome;
}
```

#### 6. 字符串同构

205 Isomorphic Strings

[Leetcode](https://leetcode.com/problems/isomorphic-strings/description/) / [力扣](https://leetcode-cn.com/problems/isomorphic-strings/description/)

```html
Given "egg", "add", return true.
Given "foo", "bar", return false.
Given "paper", "title", return true.
```

记录一个字符上次出现的位置，如果两个字符串中的字符上次出现的位置一样，那么就属于同构。

```java
public boolean isIsomorphic(String s, String t) {
    int[] preIndexOfS = new int[256];
    int[] preIndexOfT = new int[256];
    for (int i = 0; i < s.length(); i++) {
        char sc = s.charAt(i), tc = t.charAt(i);
        if (preIndexOfS[sc] != preIndexOfT[tc]) {
            return false;
        }
        preIndexOfS[sc] = i + 1;
        preIndexOfT[tc] = i + 1;
    }
    return true;
}
```

#### 7. 回文子字符串个数

647\. Palindromic Substrings (Medium)

[Leetcode](https://leetcode.com/problems/palindromic-substrings/description/) / [力扣](https://leetcode-cn.com/problems/palindromic-substrings/description/)

```html
Input: "aaa"
Output: 6
Explanation: Six palindromic strings: "a", "a", "a", "aa", "aa", "aaa".
```

从字符串的某一位开始，尝试着去扩展子字符串。

```java
private int cnt = 0;

public int countSubstrings(String s) {
    for (int i = 0; i < s.length(); i++) {
        extendSubstrings(s, i, i);     // 奇数长度
        extendSubstrings(s, i, i + 1); // 偶数长度
    }
    return cnt;
}

private void extendSubstrings(String s, int start, int end) {
    while (start >= 0 && end < s.length() && s.charAt(start) == s.charAt(end)) {
        start--;
        end++;
        cnt++;
    }
}
```

#### 8. 判断一个整数是否是回文数

9\. Palindrome Number (Easy)

[Leetcode](https://leetcode.com/problems/palindrome-number/description/) / [力扣](https://leetcode-cn.com/problems/palindrome-number/description/)

要求不能使用额外空间，也就不能将整数转换为字符串进行判断。

将整数分成左右两部分，右边那部分需要转置，然后判断这两部分是否相等。

```java
public boolean isPalindrome(int x) {
    if (x == 0) {
        return true;
    }
    if (x < 0 || x % 10 == 0) {
        return false;
    }
    int right = 0;
    while (x > right) {
        right = right * 10 + x % 10;
        x /= 10;
    }
    return x == right || x == right / 10;
}
```

#### 9. 统计二进制字符串中连续 1 和连续 0 数量相同的子字符串个数

696\. Count Binary Substrings (Easy)

[Leetcode](https://leetcode.com/problems/count-binary-substrings/description/) / [力扣](https://leetcode-cn.com/problems/count-binary-substrings/description/)

```html
Input: "00110011"
Output: 6
Explanation: There are 6 substrings that have equal number of consecutive 1's and 0's: "0011", "01", "1100", "10", "0011", and "01".
```

```java
public int countBinarySubstrings(String s) {
    int preLen = 0, curLen = 1, count = 0;
    for (int i = 1; i < s.length(); i++) {
        if (s.charAt(i) == s.charAt(i - 1)) {
            curLen++;
        } else {
            preLen = curLen;
            curLen = 1;
        }

        if (preLen >= curLen) {
            count++;
        }
    }
    return count;
}
```
## 数组与矩阵

### 283. Move Zeroes

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

### k-Sum类题目 [双指针, Hash, 排序]
k-sum类型是以2-sum为基础的变种和拓展, 包括k发生变化(2,3,4), 初始序列是否有序, 输出类型(true/false, 成立的下标, 子集的集合).
#### 2Sum
对于2 Sum而言, 暴力算法的时间复杂度为$O(n^2)$, 更好的解法有:
- 若序列有序, 可以设置双指针从首尾向中间移动, 时间复杂度为O(n); 
- 若无序, 考虑以O(n)对序列建立hash表(使用STL的map), 之后以O(1)的复杂度判断是否有解
- 也可以边hash边检查当前数字和hash表中已有的元素是否能够构成解

综上, 2sum问题的时间复杂度为O(n)
> 采用hash表时,注意存在多个相同元素时的覆盖问题和自己和自己相加等于target的问题, 这种情况, 先检查已有元素, 再将当前数字加入hash表
#### 3Sum & 4Sum
对于3Sum及以上, 暴力算法的时间复杂度都在$O(n^2)$以上, 因此首先对序列进行排序的方法是可接受的.排序后, 固定部分元素将问题转化为有序序列的2Sum问题. 这类题目的输出类型常为所有可能的子集的集合, 对于一个加数相同的数字只使用一次, 不同的加数可以相等, 这类题目的另一个重要的提高速度的方法是, 寻找合适的条件剪枝, 例如3sum中, 最小的三个数之和大于target或者最大三个数之和小于target的情况可以直接剪枝.

### 119. Pascal's Triangle II [原地迭代]
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

### 844. Backspace String Compare[双指针代替栈]

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

## 图

## 位运算

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





