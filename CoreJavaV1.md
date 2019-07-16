# Java核心技术1

- [## 基础程序设计结构](#-基础程序设计结构)
  - [基础数据类型](#基础数据类型)
  - [变量](#变量)
  - [运算符](#运算符)
  - [字符串](#字符串)
  - [输入输出](#输入输出)
  - [大数值](#大数值)
  - [数组](#数组)
- [对象与类](#对象与类)
- [继承](#继承)

## 基础程序设计结构
---

### 基础数据类型

Java包含8种基础数据类型:

整型类:

- int: 4字节
- short: 2字节
- long: 8字节
- byte: 1字节

浮点数类:

- double: 8字节, 精度小数点后11-15位
- float: 4字节, 精度小数点后5-7位

char: java中的字符类型是unicode的一个代码单元,unicode编码可能占据1个代码单元,也可能占据2个, 因此使用char访问是一种过于底层的方法, 通常并不建议, 如果需要访问, 可以按照码点位置访问.`String.codePoints`可以获得字符串的码点位置.

boolean类: 取值true或false

### 变量

Java中基本数据类型没有c++中声明和定义分离的情况, 变量的初始化使用

```java
int i = 5;
double d = 5.;
```

#### Tips

- Java中常量通过`final`修饰, 被修饰的变量的值在初始化时被定义不能再修改, Java把`const`列为关键字但没有使用.
- Java中变量不能够像C++那样进行向boolean的类型转换, 需要显式的调用方法给出boolean变量作为判断条件.
- this

### 运算符

<img src="" width=50%>(缺图)</img>

枚举类型:

和C++中的枚举类型相似, 可以给出有限个元素和索引对应, 语法举例如下:
```java
enum Car[TOYOTA, HONDA, FORD];
Car car1 = TOYOTA;
```

#### Tips

- 待定

### 字符串

**不可变字符串:** String类是java中的很重要的类, 内存模型上, String类是不可变的, 即对String的修改实际上是创建了一个新的String对象, 如果要频繁修改String对象的内容, 可以使用StringBuilder类, **对于多线程都可能修改内容的情况, 使用StringBuffer类**.

**拼接:** String类可以使用`+`进行拼接, 这也是Java中符号唯一的重载, 返回的是新创建的两个String类拼接后的新对象.

**判断相等:** 为检测两个字符串是否相等, 不能使用等号, String提供的方法有`String.equal(String other)`方法, 同时也可以使用`String.compareTo(String other)`, 后者和C语言中的`strcpy`表现一致, 相等时返回0, 第一个不相等的字符小于other时返回负数,否则返回正数. 

**空串与null:** 字符串可以为空, 即`String new1 = ""`, 这和`String new2 = null`是不相同的, 前者是String对象, 后者不是, 对后者调用String方法会产生错误, 因此判断时需要先判断是否为`null`再判断`length`是否为0.

### 输入输出

#### 终端的输入输出

终端最基本的输出方式是采用`system.out.println()`调用`system.out`对象的`println`方法, 与之相似的是`print`方法(输出不换行). 最基本的从终端输入的方式相比更加复杂一些,

```java
import java.utils.* // Scaner位于utils包中
Scaner in = new Scaner(System.in)
String input = in.nextLine()
```

首先需要用`System.in`对象创建一个Scaner对象, 然后从Scaner对象使用`nextLine`方法读取数据, 相似的方法有`nextInt`读取一个整型, `nextDouble`读取一个浮点数.

某些终端输出的场景需要采用格式化的输出, 在这种情况下, 可以使用与C语言语法一致的`printf`方法, 控制输出格式, 格式控制符如下:

<img src="" width=50%>格式控制符</img>

> String类也给出使用格式化语法构建对象的方法, `String s = String.format(expression, params)`

某些终端输入场景例如输出密码的场景,不能够采用明文的输入方式, Java提供了Console类, 通过( )解决.

#### 文件的输入输出

文件的读取和终端的输入类似, 可以使用`Scaner(filePath, encodingType)`创建一个新的对象, 然后读取, 当path不存在是报错; 文件的写入使用`PrintWriter(filePath)`创建一个新的对象, 当文件不存在时会创建新的文件.(那如果文件存在呢)

### 大数值

为了解决上下溢出的问题, Java提供了?? `LargeInt`和`LargeDouble`类, 前者可以表示任意大小的整数, 后者可以表示任意大小的浮点数, 由于Java不能够对操作符进行重载, 这两类有自己的运算符,加(.add), 减(.subtract),乘(.multiple), 除(.divide), 可以使用`.valueOf(int/double)`转换.

### 数组

Java中的数组数据类型声明为`int[] a`, 但定义一个数组对象需要指明大小`int[] a = new int[100]`. 数组的初始化可以采用以下方式:

```java
int[] a = {1, 2, 3, 4}; // 这种情形不需要new
int[] a = new ??
?? //匿名数组的使用
```

**数组遍历:** 对于数组和实现了Iterable接口的对象, 可以使用`for(type: Iterable)`的for each 语句进行遍历.

**数组拷贝:** 数组存在深拷贝和浅拷贝的问题, Java中默认使用的是引用赋值的方式, 因此直接赋值其实是传递地址, 两个数组对象指向相同内存. 若要深拷贝, 可以使用`Arrays.copy(Array, int length)`方法.

**命令行参数:** Java的main函数总是带着`String[] args`的参数, 用以获取命令行参数, 与C++不同的是, java的`args`不包含执行命令, 即`args[0]`直接是后面跟的参数.

**多维数组:** Java中的没有多维数组的概念, 实质上是数组的数组, 外层数组的元素其实是数组指针, 因此数组元素与数组元素之间的长度不一定需要相等, 即可以用`type[num][] a`定义一个多维数组, 再依次创建type[n]的对象, 这一点和C++是有所不同, 但是和C++里指针数组又是一致的.

## 对象与类

## 继承
