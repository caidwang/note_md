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