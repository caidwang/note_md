# Algorithms 4th

<!-- @import "[TOC]" {cmd="toc" depthFrom=2 depthTo=4 orderedList=false} -->

<!-- code_chunk_output -->

* [第一章 基础准备](#第一章-基础准备)
	* [1.1 基础编程模型](#11-基础编程模型)
		* [1.1.1 java程序的基本结构](#111-java程序的基本结构)
		* [1.1.2 原始数据类型和表达式](#112-原始数据类型和表达式)
		* [1.1.4 简便记法](#114-简便记法)
		* [1.1.5 数组](#115-数组)
		* [1.1.6 静态方法](#116-静态方法)
		* [1.1.7 API](#117-api)
		* [1.1.8 字符串](#118-字符串)
		* [1.1.9 输入输出](#119-输入输出)
		* [1.1.10 答疑](#1110-答疑)
	* [1.2 数据抽象](#12-数据抽象)
	* [1.3 背包,队列和栈](#13-背包队列和栈)
	* [1.4 算法分析](#14-算法分析)
	* [1.5 Union-Find算法](#15-union-find算法)
* [第二章 排序](#第二章-排序)
	* [2.1初等排序](#21初等排序)
		* [2.1.1 选择排序](#211-选择排序)
		* [2.1.2 插入排序](#212-插入排序)
		* [2.1.3 希尔排序](#213-希尔排序)
	* [2.2 归并排序](#22-归并排序)
	* [2.3 快速排序](#23-快速排序)
	* [2.4 优先队列与堆排序](#24-优先队列与堆排序)
		* [2.4.1 基于二叉堆的优先队列](#241-基于二叉堆的优先队列)
		* [2.4.2 堆排序](#242-堆排序)
		* [2.4.3 带索引的最大堆](#243-带索引的最大堆)

<!-- /code_chunk_output -->

## 第一章 基础准备
---
### 1.1 基础编程模型

#### 1.1.1 java程序的基本结构

- **原始数据类型** 整型,浮点数,布尔量等,定义包括取值范围和能够对相应值进行的操作. 它们能够被组合成类似于数学公式定义的表达式.
- **语句** 六种语句: 声明, 赋值, 条件, 循环, 调用, 返回
- **数组** 多个同种数据类型的值的集合
- **静态方法** 可以封装并重用代码, 使我们可以用独立的模块开发程序
- **字符串** 字符串是一连串的字符, java内置了对它们的操作
- **标准输入/输出** 
- **数据抽象** 数据抽象封装和重用代码, 使我们可以定义非原始数据类型, 进而支持面向对象的编程.

#### 1.1.2 原始数据类型和表达式

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

#### 1.1.4 简便记法

(1) 声明并初始化
数据类型 变量名 = 字面量;

#### 1.1.5 数组

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

#### 1.1.6 静态方法

java的程序分为两类: 静态方法库和数据类型
调用方法时, 方法的参数的传入是值传递, 因此当数组作为参数传入的时候,传入的数组的别名(引用).
方法的副作用: 方法可以具有副作用, 例如想控制台输出等.
关于递归: 递归函数的被调用函数解决的子问题不应该与其负问题有交集.
关于单元测试： 在小的算法程序中,建议将单元测试写在静态方法库中.
常用外部库: java.lang 具有基本的数据类型及其对象 java.util 具有一些实用方法

#### 1.1.7 API

api目的: 将程序的描述和实现分离开来, 使程序变得高可复用.
利用StdDraw库对算法的性能进行可视化的分析和可视化的展示

#### 1.1.8 字符串

自动转换: 在进行输出等操作的时候, 若+的参数为字符串, 则其他类型的数据会调用`toString`方法转为字符串.
与其他数据类型之间的转换: 在数的对象类型中通常有将字符串转换为整形或浮点型的方法

#### 1.1.9 输入输出

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

#### 1.1.10 答疑

- 1/0 抛出异常,但是1.0/0.0表示无穷大
- /操作和%操作的区别: 表达式a/b的商总是向0取整, 但是余数%的定义是(a/b)*b + a%b = a, 因此-14%3 = -2, 14 % -3 = 2

### 1.2 数据抽象

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

## 第二章 排序

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

### 2.1初等排序

#### 2.1.1 选择排序

Intuition: 找到数组中最小的放到第一位, 找到第二小的放到第二位....
使用到的数据结构: 数组
复杂度: n^2, 提供了算法下限.
是否稳定: 稳定
原地排序: 是
运行时间与输入无关, 数据移动最少

#### 2.1.2 插入排序

Intuition: 位于数组前部的元素都是有序的, 从第二个元素起, 将其向前插入到有序的数组中.
使用到的数据结构: 数组
复杂度: n^2, 当元素呈部分有序时, 速度较快, 适合小规模, 成本与比较和交换元素的成本有关.
是否稳定: 稳定
原地排序: 是

```java
public static void sort(Comparable[] a) {
    for (int i = 1; i < a.length; i++) {
        for (int j = i; j > 0; j--) {
            if (less(a[j], a[j-1])) exch(a, j, j - 1);
            else break;
        }
        /*
        这里可以简化代码为
        for (int j = i; j > 0 && less(a[j], a[j-1]); i--) exch(a, j - 1, j);
        性能提高, 可读性增强
        */
    }
}
```

<!-- 补充几种排序的代码 -->

#### 2.1.3 希尔排序

Intuition: 进行多次间距不同的插入排序, 提高纠正逆序对的效率. 希尔排序的间距取值有讲究. 不同的取值对应不同的实验复杂度下限.取h = h * 3 + 1的序列, 或斐波那契数列等方式
使用到的数据结构: 数组
复杂度: \<n^2 , 在不同的h取值策略表现不同, 适用于中等规模的任意顺序序列
是否稳定: 稳定
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

### 2.2 归并排序

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

### 2.3 快速排序

Intuition: 快排在实现过程中稍有不慎很容易出错,关键在于这几个点:

- 随机性 通过在开始排序前进行shuffle或者进行三取样得到用于切分的值, 保证即使输入部分有序也能够有较好的性能表现
- 比较过程中, 遇到相同的值的处理办法: 停下, 尽管造成不必要的交换, 避免序列向一边倾斜导致的n^2的复杂度
- 循环终止条件 i >= j, 等于的情况,一定是i所指向的value和用于切分的val相等的情况, 这时候退出足矣, 如果使用i > j的条件, 在两端的边界情况会造成非法索引
- 内循环的递增: 内循环的递增要使用 ++i和--j的形式, 保证遇到相同的元素后在下一次循环能够继续向前移动.
- 结束的时候, 交换暂存val的位置的值和j(若val的位置在0), 保证切分位置前的值小于等于切分val的性质不变

复杂度: n^2的下限, 对于随机数组能够接近nlgn
是否稳定: 否
是否是原地排序: 是

```java
public  static void sort(Comparable[] a) {
        StdRandom.shuffle(a);
        sort(a, 0, a.length - 1);
}
private static void sort(Comparable[] a, int lo, int hi) {
    if (hi - lo < H) Insertion.sort(a, lo, hi + 1);
    else {
        Comparable val = a[lo];
        int i = lo;
        int j = hi + 1;
        while (true) {
            while (less(a[++i], val)) if (i == hi) break;
            while (less(val, a[--j])) if (j == lo) break; // less 是严格小, 所以遇到相等的情况会停
            if (i >= j) break; // 等号成立时, 等于val, 否则i,j错位 一定会造成边界问题 思考val最小或最大的情况
            exch(a, i, j);
        }
        exch(a, j, lo);
        sort(a, lo, j - 1);
        sort(a, j + 1, hi);
    }
}
```
shuffle的复杂度是O(n), 如果不采用shuffle的话可以采用三采样的方式, 三采样方式的注意点是首尾已经通过哨兵保证了不会越界，因此内循环可以进一步简化.
### 2.4 优先队列与堆排序

#### 2.4.1 基于二叉堆的优先队列

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

#### 2.4.2 堆排序

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

#### 2.4.3 带索引的最大堆

有时候对数组排序, 该数组还具有与之无关的其他属性构成的数组, 排序时,他们也要同时变化.
