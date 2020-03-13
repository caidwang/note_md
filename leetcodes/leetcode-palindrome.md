## 回文串

- [回文串](#%e5%9b%9e%e6%96%87%e4%b8%b2)
  - [1. 计算一组字符集合可以组成的回文字符串的最大长度](#1-%e8%ae%a1%e7%ae%97%e4%b8%80%e7%bb%84%e5%ad%97%e7%ac%a6%e9%9b%86%e5%90%88%e5%8f%af%e4%bb%a5%e7%bb%84%e6%88%90%e7%9a%84%e5%9b%9e%e6%96%87%e5%ad%97%e7%ac%a6%e4%b8%b2%e7%9a%84%e6%9c%80%e5%a4%a7%e9%95%bf%e5%ba%a6)
  - [2. 回文子字符串个数](#2-%e5%9b%9e%e6%96%87%e5%ad%90%e5%ad%97%e7%ac%a6%e4%b8%b2%e4%b8%aa%e6%95%b0)
  - [2. 判断一个整数是否是回文数](#2-%e5%88%a4%e6%96%ad%e4%b8%80%e4%b8%aa%e6%95%b4%e6%95%b0%e6%98%af%e5%90%a6%e6%98%af%e5%9b%9e%e6%96%87%e6%95%b0)
  - [234. Palindrome Linked List](#234-palindrome-linked-list)
  - [125. Valid Palindrome](#125-valid-palindrome)
  - [9. Palindrome Number](#9-palindrome-number)



### 1. 计算一组字符集合可以组成的回文字符串的最大长度

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

### 2. 回文子字符串个数

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

### 2. 判断一个整数是否是回文数

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
