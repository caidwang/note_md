## 分治

- [分治](#%e5%88%86%e6%b2%bb)
  - [Majority Element](#majority-element)

### Majority Element
Moore's voting最大投票算法, [算法介绍](https://blog.csdn.net/huanghanqian/article/details/74188349) 使用的是分治思想, 即如果当`count`降为零时, 说明在前面的子序列中不存在超过1/k的元素.

**169.Majority Element**

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

**229.Majority Element II**

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
