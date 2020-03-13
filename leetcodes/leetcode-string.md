# 字符串问题

- [字符串问题](#%e5%ad%97%e7%ac%a6%e4%b8%b2%e9%97%ae%e9%a2%98)
  - [子字符串, 子序列](#%e5%ad%90%e5%ad%97%e7%ac%a6%e4%b8%b2-%e5%ad%90%e5%ba%8f%e5%88%97)
  - [其他](#%e5%85%b6%e4%bb%96)
    - [1. 字符串循环移位包含](#1-%e5%ad%97%e7%ac%a6%e4%b8%b2%e5%be%aa%e7%8e%af%e7%a7%bb%e4%bd%8d%e5%8c%85%e5%90%ab)
    - [2. 字符串循环移位](#2-%e5%ad%97%e7%ac%a6%e4%b8%b2%e5%be%aa%e7%8e%af%e7%a7%bb%e4%bd%8d)
    - [3. 字符串中单词的翻转](#3-%e5%ad%97%e7%ac%a6%e4%b8%b2%e4%b8%ad%e5%8d%95%e8%af%8d%e7%9a%84%e7%bf%bb%e8%bd%ac)
    - [4. 两个字符串包含的字符是否完全相同](#4-%e4%b8%a4%e4%b8%aa%e5%ad%97%e7%ac%a6%e4%b8%b2%e5%8c%85%e5%90%ab%e7%9a%84%e5%ad%97%e7%ac%a6%e6%98%af%e5%90%a6%e5%ae%8c%e5%85%a8%e7%9b%b8%e5%90%8c)
    - [5. 字符串同构](#5-%e5%ad%97%e7%ac%a6%e4%b8%b2%e5%90%8c%e6%9e%84)
    - [6. 统计二进制字符串中连续 1 和连续 0 数量相同的子字符串个数](#6-%e7%bb%9f%e8%ae%a1%e4%ba%8c%e8%bf%9b%e5%88%b6%e5%ad%97%e7%ac%a6%e4%b8%b2%e4%b8%ad%e8%bf%9e%e7%bb%ad-1-%e5%92%8c%e8%bf%9e%e7%bb%ad-0-%e6%95%b0%e9%87%8f%e7%9b%b8%e5%90%8c%e7%9a%84%e5%ad%90%e5%ad%97%e7%ac%a6%e4%b8%b2%e4%b8%aa%e6%95%b0)



## 子字符串, 子序列


## 其他

### 1. 字符串循环移位包含

[编程之美 3.1](#)

```html
s1 = AABCD, s2 = CDAA
Return : true
```

给定两个字符串 s1 和 s2，要求判定 s2 是否能够被 s1 做循环移位得到的字符串包含。

s1 进行循环移位的结果是 s1s1 的子字符串，因此只要判断 s2 是否是 s1s1 的子字符串即可。

### 2. 字符串循环移位

[编程之美 2.17](#)

```html
s = "abcd123" k = 3
Return "123abcd"
```

将字符串向右循环移动 k 位。

将 abcd123 中的 abcd 和 123 单独翻转，得到 dcba321，然后对整个字符串进行翻转，得到 123abcd。

### 3. 字符串中单词的翻转

[程序员代码面试指南](#)

```html
s = "I am a student"
Return "student a am I"
```

将每个单词翻转，然后将整个字符串翻转。

### 4. 两个字符串包含的字符是否完全相同

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

### 5. 字符串同构

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



### 6. 统计二进制字符串中连续 1 和连续 0 数量相同的子字符串个数

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
