## 双指针

- [双指针](#%e5%8f%8c%e6%8c%87%e9%92%88)
  - [k-Sum类题目 [双指针, Hash, 排序]](#k-sum%e7%b1%bb%e9%a2%98%e7%9b%ae-%e5%8f%8c%e6%8c%87%e9%92%88-hash-%e6%8e%92%e5%ba%8f)
    - [2Sum](#2sum)
    - [3Sum & 4Sum](#3sum--4sum)
  - [k-diff](#k-diff)
    - [532. K-diff Pairs in an Array](#532-k-diff-pairs-in-an-array)
  - [1. 双指针代替栈](#1-%e5%8f%8c%e6%8c%87%e9%92%88%e4%bb%a3%e6%9b%bf%e6%a0%88)
  - [2. 两数平方和](#2-%e4%b8%a4%e6%95%b0%e5%b9%b3%e6%96%b9%e5%92%8c)
  - [3. 反转字符串中的元音字符](#3-%e5%8f%8d%e8%bd%ac%e5%ad%97%e7%ac%a6%e4%b8%b2%e4%b8%ad%e7%9a%84%e5%85%83%e9%9f%b3%e5%ad%97%e7%ac%a6)
  - [4. 回文字符串](#4-%e5%9b%9e%e6%96%87%e5%ad%97%e7%ac%a6%e4%b8%b2)
  - [5. 归并两个有序数组](#5-%e5%bd%92%e5%b9%b6%e4%b8%a4%e4%b8%aa%e6%9c%89%e5%ba%8f%e6%95%b0%e7%bb%84)
  - [6. 判断链表是否存在环](#6-%e5%88%a4%e6%96%ad%e9%93%be%e8%a1%a8%e6%98%af%e5%90%a6%e5%ad%98%e5%9c%a8%e7%8e%af)
  - [7. 最长子序列](#7-%e6%9c%80%e9%95%bf%e5%ad%90%e5%ba%8f%e5%88%97)




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
上述代码中内循环的break条件，可以通过安放哨兵的方式消除。在数组左侧放置一个不满足右指针valid条件的值，在数组的右侧放置一个不满足左指针valid条件的值，保证循环能在边界停下。具体示例可以参考完整的快排切分方法：
```java
int partition(int[] list, int start, int end) {
    // 三采样
    int mid = start + (end - start) / 2;
    if (less(list, mid, start)) {
        swap(list, mid, start);
    }
    if (less(list, end, mid)) {
        swap(list, mid, end); // 放置了右侧哨兵位 这个值满足切分右侧的条件 因此不需要在最后还原位置
    }
    // 放置了左侧哨兵位
    swap(list, mid, start);

    int left = start;
    int right = end;
    while(true) {
        while(less(list, ++left, start)) ;
        while(less(list, start, --right)) ;

        if (left >= right) {
            break;
        }
        swap(list, left, right);
    }
    swap(list, start, right); // 还原左侧哨兵的正确位置
    return right;
} 
```

双指针最常见的两种模式是快慢指针和首尾向中间移动.

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

### 1. 双指针代替栈
844.Backspace String Compare[双指针代替栈]

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
