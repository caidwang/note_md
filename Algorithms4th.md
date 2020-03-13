
- [第一章 基础准备](#第一章-基础准备)
  - [1.1 基础编程模型](#11-基础编程模型)
    - [.1 java程序的基本结构](#1-java程序的基本结构)
    - [.2 原始数据类型和表达式](#2-原始数据类型和表达式)
    - [.4 简便记法](#4-简便记法)
    - [.5 数组](#5-数组)
    - [.6 静态方法](#6-静态方法)
    - [.7 API](#7-api)
    - [.8 字符串](#8-字符串)
    - [.9 输入输出](#9-输入输出)
    - [.10 答疑](#10-答疑)
  - [1.2 数据抽象](#12-数据抽象)
    - [1.3 背包,队列和栈](#13-背包队列和栈)
    - [1.4 算法分析](#14-算法分析)
    - [1.5 Union-Find算法](#15-union-find算法)
- [第二章 排序](#第二章-排序)
  - [2.1初等排序](#21初等排序)
    - [.1 选择排序](#1-选择排序)
    - [.2 插入排序](#2-插入排序)
    - [.3 希尔排序](#3-希尔排序)
  - [2.2 归并排序](#22-归并排序)
  - [2.3 快速排序](#23-快速排序)
  - [2.4 优先队列与堆排序](#24-优先队列与堆排序)
    - [.1 基于二叉堆的优先队列](#1-基于二叉堆的优先队列)
    - [.2 堆排序](#2-堆排序)
    - [.3 带索引的最大堆](#3-带索引的最大堆)


# 第一章 基础准备

---
## 1.1 基础编程模型

### .1 java程序的基本结构

- **原始数据类型** 整型,浮点数,布尔量等,定义包括取值范围和能够对相应值进行的操作. 它们能够被组合成类似于数学公式定义的表达式.
- **语句** 六种语句: 声明, 赋值, 条件, 循环, 调用, 返回
- **数组** 多个同种数据类型的值的集合
- **静态方法** 可以封装并重用代码, 使我们可以用独立的模块开发程序
- **字符串** 字符串是一连串的字符, java内置了对它们的操作
- **标准输入/输出** 
- **数据抽象** 数据抽象封装和重用代码, 使我们可以定义非原始数据类型, 进而支持面向对象的编程.

### .2 原始数据类型和表达式

**基本数据类型**

整型, 双精度实数类型, 布尔型, 字符型

**java程序的基本组成**

|术语|定义|
|---|---|
|原始数据类型|一组数据和对其所能进行的操作的集合|
|标识符|由字母,数字,下划线,$组成的字符串,首字母不能是数字|
|变量|表示某种数据类型的值, 由标识符表示|
|运算符|表示某种数据类型的运算|
|字面量|值在源码中的表示|
|表达式|字面量,变量或能够计算出结果的字面量,变量和运算符的组合|

**类型转换**

如果不损失信息, 数值会被自动提升为更高级的数据类型. 浮点数强制转换整型时丢失小数部分信息而非四舍五入.

**其他原始数据类型**

- int 范围是$-2^{31} \quad  to \quad 2^{31}-1$
- long 64位整数
- short 16位整数
- byte 8位整数
- float 32位单精度整数

### .4 简便记法

(1) 声明并初始化
数据类型 变量名 = 字面量;

### .5 数组

(1) 创建数组
&emsp;a. 声明数组的变量名和类型
&emsp;b. 创建数组
&emsp;c. 初始化数组元素

```java
// 简化写法
double[] a = new double[n];
// 声明初始化
int[] a = {1, 1, 2, 3, 5, 8};
```

> 在简化写法中, 数值类型默认初始值为0, 布尔型默认初始值为false.

(2) java中不能够创建泛型数组, 通常创建一个Object数组再进行强制类型转换.
(3) 数组的复制和起别名
　和cpp类似, 数组变量名只保存数组首个元素的地址, 因此, 直接将数组变量名赋值给另一个数组变量并不能达到复制的效果, 这种赋值成为 *起别名* , 即对同一个数组增加一个变量名的引用. 要想复制数组, 可以用for循环遍历, 或者使用array的deepcopy方法进行复制.

### .6 静态方法

java的程序分为两类: 静态方法库和数据类型
调用方法时, 方法的参数的传入是值传递, 因此当数组作为参数传入的时候,传入的数组的别名(引用).
方法的副作用: 方法可以具有副作用, 例如想控制台输出等.
关于递归: 递归函数的被调用函数解决的子问题不应该与其负问题有交集.
关于单元测试： 在小的算法程序中,建议将单元测试写在静态方法库中.
常用外部库: java.lang 具有基本的数据类型及其对象 java.util 具有一些实用方法

### .7 API

api目的: 将程序的描述和实现分离开来, 使程序变得高可复用.
利用StdDraw库对算法的性能进行可视化的分析和可视化的展示

### .8 字符串

自动转换: 在进行输出等操作的时候, 若+的参数为字符串, 则其他类型的数据会调用`toString`方法转为字符串.
与其他数据类型之间的转换: 在数的对象类型中通常有将字符串转换为整形或浮点型的方法

### .9 输入输出

使用Intellj时, 命令行参数的位置以及重定向输入的方法

在intellj 中通过debug方式运行需要使用重定向的程序,  方法是先将文件读进`fieStream`, 然后将对象赋给`System.stdin`, 具体代码如下:

```java
try {
    FileInputStream input = new FileInputStream("compress");
    System.setIn(input);
}
catch (FileNotFoundException e)  {
    e.printStackTrace();
}
```

格式化输入输出 与c基本一致
![格式化输入输出](file:///tmp/WizNote/a5df4ab8-f1c4-4e8a-b4d8-228896d0b0d9/index_files/20180514234933630.jpg)

### .10 答疑

- 1/0 抛出异常,但是1.0/0.0表示无穷大
- /操作和%操作的区别: 表达式a/b的商总是向0取整, 但是余数%的定义是(a/b)*b + a%b = a, 因此-14%3 = -2, 14 % -3 = 2

## 1.2 数据抽象

API的实现: API的使用和实现隔离, 使得数据类型的使用不需要了解其实现的细节.
API和抽象数据类型的实现: 以API名实现的数据类型具有通用性, 在API前使用前缀使用不同的数据结构实现API比较几者之间的性能特点.
断言: 在运行时使用`-ea`启用断言, 作为调试手段之一, 功能的实现不应依赖于断言.
抛出异常时可能出现的错误:

```txt
can't find symbol
symbol :method Counter(String)
```

java的内存模型只有new一种, 即通过引用实现指针的功能, 被称为安全指针.

### 1.3 背包,队列和栈

背包, 队列和栈都是集合的不同实现方式
Java中的自动装箱: java泛型参数要求是引用类型, 因此基本数据类型在使用泛型的实现实现中, 会被自动转化为封装类型, 而在返回的时候又会自动拆箱成基本数据类型.
背包是不具有删除功能的集合, 用于收集和遍历对象
队列是先进先出的集合类型
栈是先进后出的集合类型.
Dijkstra双栈算术式求和: 局限性, 两个操作数和一个操作符外就需要设置一对括号.双栈算术式求和:

- 遇到操作符压入操作符栈
- 遇到操作数压入操作数栈
- 遇到左括号忽略
- 遇到右括号, 弹出一个操作符和操作符需要的操作数, 计算结果加入到操作数栈中
- 结束时, 操作数栈只剩一个结果, 操作符栈为空
- 返回结果

在需要动态调整数组大小的栈和栈的实现中, 注意扩容和缩容的尺寸不同(1/4), 注意避免元素游离, 在数组高于N的位置, 都应该为null.

### 1.4 算法分析

时间分析
求运行时间的模型

- 确定输入模型, 定义问题规模
- 识别内循环
- 根据内循环中的操作确定成本模型
- 对给定的输入, 判断这些操作的执行频率.

> 成本模型 在内循环总进行的操作种类, 例如比较操作

倍率实验与倍率定理:
判断一个算法的时间复杂度, 可以通过对N, 2N, 4N, 8N...规模的问题进行求解, 得到求解这些问题的时间比值, 根据倍率定理, T(2N)/T(N) ~ 2^b, 其中b是O(N^b)
倍率实验尽量覆盖到2^b的数据规模, 使得计算结果更加准确.参考书本p121

内存分析

java中的内存分配如下:
一个对象的对象开销为16bytes, 若对象有对外引用, 需要额外开销8bytes, 一个实例变量(引用变量)的开销8bytes, 若实例变量为基本数据类型还需要按照基本数据类型计算, 同时要注意8字节补全.
在计算内存开销时, 我们并不会把引用指向的内容(例如Integer或string)所占用的内存计算在内.
按照上述的计算规则, 一个数组的内存开销是(24+4N), 16bytes对象开销, 4bytes长度信息和4bytes的填充空间.
注意jdk7u6之前String模型中字符串只存储一次, 若有相同的部分, 通过偏移量得到新的String对象(substring方法为常数复杂度).

### 1.5 Union-Find算法

基本UF

- 数据结构: 数组
- 查找操作: 返回数组中该下标元素的内容(为属于的集合的编号), 常数复杂度
- 链接操作: 遍历数组, 将与其中一个元素在同一个集合的元素的内容都改为另一个元素的所在集合编号,N复杂度
- 判断是否在同一个集合: 比较两个下标的内容, 常数复杂度
- 问题: 链接操作的复杂度不适合大规模问题

quick-union及其加权方法

- 数据结构: 利用数组表示的堆
- 查找操作: lgN复杂度
- 链接操作: 常数复杂度
- 判断是否在同一个集合: lgN复杂度
- 考虑到堆的深度对查找的速度影响较大, 通过将较小的堆合并到较大的堆的方法得到更好的性能.

# 第二章 排序

---
排序算法的框架以及性能测试程序

```java
import edu.princeton.cs.algs4.StdOut;
import edu.princeton.cs.algs4.StdRandom;
import edu.princeton.cs.algs4.Stopwatch;

public class Sort {
    private static void exch(Comparable[] a, int i, int j) { Comparable temp = a[i]; a[i] = a[j]; a[j] = temp;}
    private static boolean less(Comparable a, Comparable b) { return a.compareTo(b) < 0; }
    private static boolean isSorted(Comparable[] a) {
        for (int i = 1; i < a.length; i++) {
            if (less(a[i], a[i - 1])) return false;
        }
        return true;
    }
    public static void sort(Comparable[] a);
    public static void main(String[] args) {
        double preTime = 0;
        for (int N = 100; N < 100000; N = 2 * N) {
            Integer[] a = new Integer[N];
            for (int i = 0; i < N; i++) {
                a[i] = StdRandom.uniform(5000);
            }
            Stopwatch timer = new Stopwatch();
            Insertsort.sort(a);
            double time = timer.elapsedTime();
            if (!Insertsort.isSorted(a)) throw new RuntimeException("the sort algorithm is wrong.");
            StdOut.printf("size: %d\ttime: %.2f\t %.2f\n", N, time, time / preTime);
            preTime = time;
        }
    }
}
```

## 2.1初等排序

### .1 选择排序

Intuition: 找到数组中最小的放到第一位, 找到第二小的放到第二位....
使用到的数据结构: 数组
复杂度: n^2, 提供了算法下限.
是否稳定: 稳定
原地排序: 是
运行时间与输入无关, 数据移动最少
```java
public static void sort(Comparable[] a) {
    for (int i = 0; i < a.length; i++) {
        int min = i;
        for (int j = i+1; j < a.length; j++) {
            if (less(a[j], a[min])) min = j;
        }
        if (min != i) exch(a, i, min);
    }
}
```

### .2 插入排序

Intuition: 位于数组前部的元素都是有序的, 从第二个元素起, 将其向前插入到有序的数组中.
使用到的数据结构: 数组
复杂度: n^2, 当元素呈部分有序时, 速度较快, 适合小规模, 成本与比较和交换元素的成本有关.
是否稳定: 稳定
原地排序: 是

```java
public static void sort(Comparable[] a) {
    for (int i = 1; i < a.length; i++) {
        for (int j = i; j > 0; j--) {
            for (int j = i; j > 0 && less(a[j], a[j-1]); i--) 
                exch(a, j - 1, j);
        }
    }
}
```

<!-- 补充几种排序的代码 -->

### .3 希尔排序

Intuition: 进行多次间距不同的插入排序, 提高纠正逆序对的效率. 希尔排序的间距取值有讲究. 不同的取值对应不同的实验复杂度下限.取h = h * 3 + 1的序列, 或斐波那契数列等方式
使用到的数据结构: 数组
复杂度: \<n^2 , 在不同的h取值策略表现不同, 适用于中等规模的任意顺序序列
是否稳定: 不稳定
原地排序: 是

```java
public  static void sort(Comparable[] a) {
    int N = a.length;
    int h = 1;
    while (h < N / 3) h = 3 * h + 1; // h 的序列不是直接从N/3 往下除, 思考若N为3的倍数的情况, 不能得到 h = 1
    while (h >= 1) {
        for (int i = 1; i < N; i++)
            for (int j = i; j >= h && less(a[j], a[j-h]); j -= h) { // j的递减间距
                exch(a, j-h, j);
            }
        h /= 3;
    }
}
```

## 2.2 归并排序

Intuition: 分治思想, 将一个大的排序划分为两个小的排序, 然后将两个有序序列合并为一个有序序列, 可用于外排序, 在小数组的时候转为插入排序,提高性能
复杂度: nlogN的复杂度保证
是否稳定: 稳定
是否是原地排序: 否, 需要一个辅助数组, 最好在一开始开个大的避免重复开小数组.

```java
private static Comparable[] aux;
private static int H = 5;
public static void sort(Comparable[] a) {
    aux = new Comparable[a.length];
    sort(a, 0, a.length - 1);
    aux = null; // 防止内存泄露
}
private static void sort(Comparable[] a, int lo, int hi) {
    if (hi - lo < H) Insertion.sort(a, lo, hi+1);
    else {
        int mid = lo + (hi - lo) / 2; // 取mid的时候, 王孙超常犯错误之一就是忘了加上lo
        sort(a, lo, mid);
        sort(a, mid + 1, hi);
        merge(a, lo, mid, hi);
    }
}
private static void merge(Comparable[] a, int lo, int mid, int hi) {
    if (!less(a[mid+1], a[mid])) return ;
    for (int i = lo; i <= hi; i++) {
        aux[i] = a[i];
    }
    int ro = mid + 1;
    int t = lo;
    while (t <= hi) { // 合并过程的四种情况
        if (lo > mid)                       a[t++] = aux[ro++];
        else if (ro > hi)                   a[t++] = aux[lo++];
        else if (less(aux[ro], aux[lo]))    a[t++] = aux[ro++];
        else                                a[t++] = aux[lo++];
    }
}
```

## 2.3 快速排序

Intuition: 快排在实现过程中稍有不慎很容易出错,关键在于这几个点:

- 随机性 通过在开始排序前进行shuffle或者进行三取样得到用于切分的值, 保证即使输入部分有序也能够有较好的性能表现
- 比较过程中, 遇到相同的值的处理办法: 停下, 尽管造成不必要的交换, 避免序列向一边倾斜导致的n^2的复杂度
- 循环终止条件 i >= j, 等于的情况,一定是i所指向的value和用于切分的val相等的情况, 这时候退出足矣, 如果使用i > j的条件, 在两端的边界情况会造成非法索引
- 内循环的递增: 内循环的递增要使用 ++i和--j的形式, 保证遇到相同的元素后在下一次循环能够继续向前移动.
- 结束的时候, 交换暂存val的位置的值和j(若val的位置在0), 保证切分位置前的值小于等于切分val的性质不变

复杂度: n^2的下限, 对于随机数组能够接近nlgn, 当数组已经是有序的情况, 如果不shuffle会落入n^2复杂度, 当数组元素完全相同时, 总会得到n^2的复杂度

是否稳定: 否

是否是原地排序: 是

优化思路: 在部分有序的情形下, 关键问题在于如何选择pivot能够使得大于小于的数量差不多, 比如三采样或者打乱, 对于大量重复元素的情况, 采用3路切分能够提高效率.
```java
// 传统快排
class QuickSort extends Sort {
    public void sort(Comparable[] a) {
        if (a == null || a.length == 0) return ;
        sort(a, 0, a.length-1);
    }
    private void sort(Comparable[] a, int left, int right) {
        if (left >= right) return ;
        int mid = partition(a, left, right);
        sort(a, left, mid-1);
        sort(a, mid+1, right);
    }
    private int partition(Comparable[] a, int left, int right) {
        Comparable pivot = a[left];
        int i = left, j = right + 1;
        while (true) {
            // while (++i < j && less(a[i], pivot));
            // while (--j >= i && less(pivot, a[j])); // 如果想这样写, 就需要>= 否则全大于的情况就会出错 但是这样写的确不好记
            while (less(a[++i], pivot)) if (i == right) break;
            while (less(pivot, a[--j])) if (j == left) break; // less 是严格小, 所以遇到相等的情况会停
            if (i >= j) break; // 等号成立时, 等于val, 否则i,j错位 一定会造成边界问题 思考val最小或最大的情况
            exch(a, i, j);
        }
        exch(a, left, j);
        return j;
    }
}

// 用三采样来优化
    private int partition(Comparable[] a, int left, int right) {
        // 三采样
        int mid = (left + right) >>> 1;
        if (less(a[right], a[left])) exch(a, left, right);
        if (less(a[right], a[mid])) exch(a, mid, right);
        if (less(a[mid], a[left])) exch(a, mid, left);
        // 此时 a[left] <= a[mid] <= a[right]
        if (right - left < 3) return mid; // 注意 如果长度小于3的话, 交换就已经够了 往下会发生错误
        exch(a, mid, left+1); // 把mid藏到left+1的位置
        int i = left+1, j = right;
        Comparable pivot = a[left+1];
        while (true) {
            while (less(a[++i], pivot)); // 因为有了两边的哨兵, 所以可以去除检查
            while (less(pivot, a[--j]));
            if (i >= j) break;
            exch(a, i, j);
        }
        exch(a, j, left+1);
        return j;
    }

// 用shuffle打乱成随机数组
    private static void shuffle(Object[] a) {
        for (int i = a.length-1; i > 0; i--) {
            exch(a, i, (int)(Math.random()*i)); // random范围[0, 1), 在0-a之间随机选择一个数和a+1交换, a逐渐减小
        }
    }
    public void sort(Comparable[] a) {
        if (a == null || a.length == 0) return ;
        shuffle(a);
        sort(a, 0, a.length-1);
    }
```

shuffle的复杂度是O(n), 如果不采用shuffle的话可以采用三采样的方式, 三采样方式的注意点是首尾已经通过哨兵保证了不会越界，因此内循环可以进一步简化.

三采样的方式的复杂度同样也是O(n), 虽然看似是O(1)的操作, 但是每次切分都要执行, 执行的次数可以按照以下递推式计算$T(n)=2T(n/2)+1, T(3)=1$, 得到的依然是个O(n)的表达式

以上两种方法可以在一定程度上解决有序的问题, 对于更大规模的数组, 可以采用更加细致的抽样中位数方式, 例如js中对于大于1000的数组, 每两百个抽样一个数, 取结果的中位数

但是上述方法还是无法处理重复元素的问题, 当重复元素较多时, 可以采用三路切分的方法, 将数组分为小于, 等于和大于三个部分.
## 2.4 优先队列与堆排序

### .1 基于二叉堆的优先队列

优先队列以基于数组的完全二叉树为基本数据结构, 具有对于k节点,其子节点索引为2k和2k+1的特点. 最重要的方法是插入,删除最大值和建立堆. 用到的方法是上游和下沉.
易错点: 数组使用1到n, 因为2 * 0 不能够指向子节点. 因此在申请初始数组大小的时候也需要注意.

```java
private void swim(int i) {
    while (i/2 > 0 && less(i/2, i)) {
        exch(i, i/2);
        i /= 2;
    }
}

private void sink(int i) {
    while (i * 2 <= n) {
        int k = 2 * i;
        if (k + 1 <= n && less(k, k+1)) k += 1;
        if (less(k, i)) break;
        exch(i, k);
        i = k;
    }
}
```

### .2 堆排序

堆排序是建立在`swim`和`sink`两个函数上的排序方法,优点是简洁,具有O(nlogn)的复杂度保证, 缺点是无法有效利用缓存, 数组中的元素很少和它临近的其他元素进行比较,因此缓存未命中的次数远高于大多数比较都在相邻元素之间的算法,如快排, 归并排序,甚至希尔排序.

```java
public pirvate sort(Comparable[] a) {
    int N = a.length;
    for (int k = N/2; k > 0; k--) {
        sink(a, k, n);
    }
    while (N) {
        exch(a, 1, N--);
        sink(a, 1, N);
    }
}
```

### .3 带索引的最大堆

有时候对数组排序, 该数组还具有与之无关的其他属性构成的数组, 排序时,他们也要同时变化.

# 第三章 搜索与树算法

## 二叉搜索树的遍历
二叉搜索树的遍历, 常考知识点包括了各种遍历以及重建. 首先是遍历, 前中后序遍历的递归实现非常简洁, 但是其非递归实现才是经常被问到. **递归的本质就是栈.** 因此, 这三种遍历的非递归实现都依赖栈.

三种遍历的非递归写法的模板.
```java
while( 栈非空 || p 非空)
{
if( p 非空)
{
    // 处理左儿子
}
else
{
    // 处理pop和右儿子
}
}
```

### 前序遍历
前序遍历是在第一次遇到节点的时候, 将其加入序列当中, 因此在入栈时刻将其加入即可. 
```java
// 递归版本
private void preOrder(TreeNode root) {
    if (root == null) return ;
    array.add(root.val);
    preOrder(root.left);
    preOrder(root.right);
}

// 非递归版本
private void preOrder2(TreeNode root) {
    Stack<TreeNode> s = new Stack<>();
    TreeNode p = root;
    while (p != null || !s.isEmpty()) {
        while (p != null) {
            array.add(p.val);
            s.push(p);
            p = p.left;
        }
        if (!s.isEmpty()) {
            p = s.pop();
            p = p.right;
        }
    }
}

// 最优雅的版本 因为栈的FILO特点, 先压右节点再压左节点
public List<Integer> preorderTraversal(TreeNode root) {
    List<Integer> list = new ArrayList<>();
    if (root == null) {
        return list;
    }
    Stack<TreeNode> stack = new Stack<>();
    stack.push(root);
    while (!stack.isEmpty()) {
        TreeNode cur = stack.pop();
        if (cur == null) {
            continue;
        }
        list.add(cur.val);
        stack.push(cur.right);
        stack.push(cur.left);
    }
    return list;
}
```

### 中序遍历
中序遍历是在第二次遇到该节点的时候, 将其加入到序列中, 因此非递归实现将加入时机放到出栈时即可.
```java
// 递归版本
private void inOrder(TreeNode root) {
    if (root == null) return ;
    inOrder(root.left);
    array.add(root.val);
    inOrder(root.right);
}

// 非递归版本
private void inOrder2(TreeNode root) {
    Stack<TreeNode> s = new Stack<>();
    TreeNode p = root;
    while (p != null || !s.isEmpty()) {
        while (p != null) {
            s.push(p);
            p = p.left;
        }
        if (!s.isEmpty()) {
            p = s.pop();
            array.add(p.val);
            p = p.right;
        }
    }
}
```

### 后序遍历
后续的非递归实现, 相比前面两个稍微有一点不同, 但是只要记住实现是靠**栈加上检查上一个是否是右儿子**就够了.
```java
// 递归版本
private void postOrder(TreeNode root) {
    if (root == null) return ;
    postOrder(root.left);
    postOrder(root.right);
    array.add(root.val);
}

// 非递归版本
public List<Integer> postorderTraversal(TreeNode root) {
    List<Integer> result = new LinkedList<>();
    Stack<TreeNode> s = new Stack<>();
    TreeNode p = root, q = null;
    while (p != null || !s.isEmpty()) {
        while (p != null) {
            s.push(p);
            p = p.left;
        }
        if (!s.isEmpty()) {
            p = s.peek();
            if (p.right == null || q == p.right) {
                result.add(p.val);
                s.pop();
                q = p;
                p = null;
            }
            else {
                p = p.right;
            }
        }
    }
    return result;
}

// 最优雅的版本
public List<Integer> postorderTraversal(TreeNode root) {
    List<Integer> list = new ArrayList<>();
    if (root == null) {
        return list;
    }
    Stack<TreeNode> stack = new Stack<>();
    stack.push(root);
    stack.push(root);
    while (!stack.isEmpty()) {
        TreeNode cur = stack.pop();
        if (cur == null) {
            continue;
        }
        if (!stack.isEmpty() && cur == stack.peek()) {
            stack.push(cur.right);
            stack.push(cur.right);
            stack.push(cur.left);
            stack.push(cur.left);
        } else {
            list.add(cur.val);
        }
    }
    return list;
}
```
## 红黑树
红黑树是2-3查找树的代码实现. 2-3查找树是一类平衡树, 包括2-节点和3-节点两种节点, 分别包含一个元素和两个链接,以及两个元素和三个链接. 2-3查找树的生长是自底向上的, 首先把叶子节点先长大成3-节点, 如果已经是3-节点暂时变为4-节点后, 向上传递中间节点, 如果父节点是个2-节点则会生长为3-节点, 如果一路上都是3-节点, 到根节点时根节点会从3-节点往上生长一层, 因为每次树的层数增加都是在根节点发生的, 所以所有叶子节点的深度相同.

![根的生长示意图](http://cdn.hustcaid.com/FvQiAE3gxkb5QGripFpjUsbTBPrp.png)

2-3查找树的插入共有六种情形, 在下图中进行了总结

![插入的情形](http://cdn.hustcaid.com/FrdD5bLUcwsCCKyrT610eIQlAKSW.png)

2-3查找树虽然具有很好的性质, 但是2-节点和3-节点两种节点混杂, 给实现造成了一定的困难, 而红黑树的思想就是用红的左链接链接3-节点的两个元素, 黑的链接表示2-3查找树中的普通链接, 当红链接平放时, 红黑树就是2-3查找树. 通过这样的变换, 能够统一树的节点, 也不用修改BST中get等操作.

红黑树的特性:
- 红链接一定是左链接
- 没有两条连续的红链接
- 该树*完美黑色平衡*, 即从根到任何叶子节点的黑链接数量相同.

红黑树和AVL树的比较:
- AVL树的定义是左子树和右子树的高度差不超过1; 红黑树的定义是从叶子节点到根的黑链接相等(2-3树平衡)
- 由于红黑树不追求严格平衡, 在增删时的旋转操作比AVL更少, 增删性能更好
- 由于AVL树的严格平衡, 查找的平均次数比红黑树少, 查和改的性能更好
- 对于查找远多于增删的情况, 用AVL, 对于增删改查折中的情况, 用红黑树
- AVL应用--win NT内核, 红黑树-HashMap, epoll的sockfd管理.

红黑树实现中的三种变换

左旋转 & 右旋转

![](http://cdn.hustcaid.com/Fqu0pvOrFZFUfBfk_lOYSTOmDka3.png)

左旋转在出现右链接为红的时候使用, 而右旋转使用的情况在两个连续的红色的左链接出现时. 

颜色转换

![](http://cdn.hustcaid.com/Ftngl-HfiA4_oPZf7GaAqDofXNDk.png)

- 如果右儿子是红色的, 则进行左旋转
- 如果左儿子是红色的并且它的左儿子是红色, 则进行右旋转
- 如果左右儿子都是红色的, 进行颜色转换

![](http://cdn.hustcaid.com/FgRK16SyRQxa5CG3SkjfRq5wpU6v.png)

```java
private Node put(Node h, Key k, Value v) {
    if (h == null)
        return new Node(k, v, RED);
    int comp = h.key.compareTo(k);
    if (comp < 0) h.right = put(h.right, k, v); // key比h大
    else if (comp > 0) h.left = put(h.left, k, v);
    else h.val = val;
    // 按照递归在新节点的路径上从下往上 处理红黑边关系
    // 处理顺序按照 是否有左旋 -> 是否有右旋 -> 是否颜色转换
    if (isRed(h.right) && !isRed(h.left)) h = RotateLeft(h);
    if (isRed(h.left) && isRed(h.left.left)) h = RotateRight(h); // isRed的先后不能换, left为null时, 第一个为false
    if (isRed(h.left) && isRed(h.right)) flipColor(h);

    // 如果计算N
    h.N = size(h.left) + size(h.right) + 1;
    return h;
}

private Node RotateLeft(Node h) {
    Node x = h.right;
    h.right = x.left;
    x.left = h;
    x.color = h.color;
    h.color = RED;
    return x;
}

private Node RotateRight(Node h) {
    Node x = h.left;
    h.left = x.right;
    x.right = h;
    x.color = h.color;
    h.color = RED;
    return x;
}

private void flipColor(Node h) {
    h.left.color = BLACK;
    h.right.color = BLACK;
    h.color = RED;
}
```

# 第五章 字符串

## 子字符串查找

### KMP算法

KMP算法的底层是一个确定有限状态自动机DFA, 随着字符串流流过改变状态, 通过回退状态代替指针的回退. KMP的关键在于如何构造DFA, 而构造DFA的方法就是对匹配模式(Patten)使用DFA本身进行匹配.

DFA的表示: 可以使用一个二维数组表示DFA, DFA[字符c][状态i]表示在状态i时遇到c字符会转向的状态. 数组维护字符集的每个字符, 在所有状态的转移状态.

DFA的构造步骤:
- 初始化0时刻的状态, 把`Pat.charAt(0)`位置更新为1, 重启后状态X置0
- 将重启状态X的内容复制到当前时刻
- 更新当前时刻如果匹配上的转移状态
- 更新重启状态遇到当前时刻的字符后的重启状态

```java
dfa[pat.charAt(0)][0] = 1;
for (int j = 1, X = 0; j < M; j++) {
    // 复制X状态的转移情况到当前
    for (int c = 0; c < R; c++) {
        dfa[c][j] = dfa[c][x];
    }
    // 更新和X状态不一样的匹配状态
    dfa[pat.charAt(j)][j] = j + 1;
    // 重启状态遇到当前字符后的重启状态
    X = dfa[pat.charAt(j)][X];
}
```

**重启状态的实质是从j=1开始匹配, 到当前位置时的DFA所在的状态**

算法总结:
- 时间复杂度: 平均O(m+n), 最坏O(m+n)
- 空间复杂度: MR, M是pattern长度, R是字符表大小
- 优点: 不需要回退, 适合流数据


