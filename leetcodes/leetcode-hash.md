## 哈希表

- [哈希表](#%e5%93%88%e5%b8%8c%e8%a1%a8)
  - [1002 Find Common Character](#1002-find-common-character)
  - [888. Fair Candy Swap](#888-fair-candy-swap)
  - [1. 数组中两个数的和为给定值](#1-%e6%95%b0%e7%bb%84%e4%b8%ad%e4%b8%a4%e4%b8%aa%e6%95%b0%e7%9a%84%e5%92%8c%e4%b8%ba%e7%bb%99%e5%ae%9a%e5%80%bc)
  - [2. 判断数组是否含有重复元素](#2-%e5%88%a4%e6%96%ad%e6%95%b0%e7%bb%84%e6%98%af%e5%90%a6%e5%90%ab%e6%9c%89%e9%87%8d%e5%a4%8d%e5%85%83%e7%b4%a0)
  - [3. 最长和谐序列](#3-%e6%9c%80%e9%95%bf%e5%92%8c%e8%b0%90%e5%ba%8f%e5%88%97)
  - [4. 最长连续序列](#4-%e6%9c%80%e9%95%bf%e8%bf%9e%e7%bb%ad%e5%ba%8f%e5%88%97)


哈希表使用 O(N) 空间复杂度存储数据，并且以 O(1) 时间复杂度求解问题。

- Java 中的   **HashSet**   用于存储一个集合，可以查找元素是否在集合中。如果元素有穷，并且范围不大，那么可以用一个布尔数组来存储一个元素是否存在。例如对于只有小写字符的元素，就可以用一个长度为 26 的布尔数组来存储一个字符集合，使得空间复杂度降低为 O(1)。

 - Java 中的   **HashMap**   主要用于映射关系，从而把两个元素联系起来。HashMap 也可以用来对元素进行计数统计，此时键为元素，值为计数。和 HashSet 类似，如果元素有穷并且范围不大，可以用整型数组来进行统计。在对一个内容进行压缩或者其它转换时，利用 HashMap 可以把原始内容和转换后的内容联系起来。例如在一个简化 url 的系统中 [Leetcdoe : 535. Encode and Decode TinyURL (Medium)，利用 HashMap 就可以存储精简后的 url 到原始 url 的映射，使得不仅可以显示简化的 url，也可以根据简化的 url 得到原始 url 从而定位到正确的资源

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

### 1. 数组中两个数的和为给定值

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
