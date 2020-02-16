## Java 常考知识点

### 基本语法
#### Java基本类型和大小
- int: 4字节, 大小刚好超过20亿
- short: 2字节
- long: 8字节
- byte: 1字节
- double: 8字节
- float: 4字节
- boolean: 1字节
- char: 2字节

#### 值传递和引用传递区别, Java中有引用传递么?
结论: Java中没有引用传递, 只有值传递.

### 创建线程的方法
Runable和Callable的区别是什么?


### 并发
####　Lock和synchronized的区别：
- Lock是一个接口，而synchronized是Java中的关键字，synchronized是内置的语言实现, synchonized在编译时用管程实现了互斥和同步
- synchronized在发生异常时，会自动释放线程占有的锁，因此不会导致死锁现象发生；而Lock在发生异常时，如果没有主动通过unLock()去释放锁，则很可能造成死锁现象，因此使用Lock时需要在finally块中释放锁；
- Lock可以让等待锁的线程响应中断，而synchronized却不行，使用synchronized时，等待的线程会一直等待下去，不能够响应中断；
- 通过Lock可以知道有没有成功获取锁，而synchronized却无法办到。
- Lock可以提高多个线程进行读操作的效率。
- 在性能上来说，如果竞争资源不激烈，两者的性能是差不多的，而当竞争资源非常激烈时（即有大量线程同时竞争），此时Lock的性能要远远优于synchronized。所以说，在具体使用时要根据适当情况选择。

#### volatile关键字的作用
保证线程之间的可见性和运行的有序性(禁止指令重排). 并发的三个概念: 原子性, 有序性, 可见性 被修饰的变量,线程取变量要从主存取,计算完直接写入主存而不是高速缓存.

### JVM
#### JVM内存结构

#### JMM线程模型

#### JVM内存模型