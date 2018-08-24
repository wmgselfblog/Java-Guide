# java基础
## jvm内存划分
内存泄漏,无限a = new object() vector.add(a) a=null 
当集合里面的对象属性被修改后 hashcode变了  hashmap里面的没有变
## 垃圾回收
垃圾回收算法
## 集合
### ArrayList和LinkedList 
### hashmap concurrenthashmap
hashmap如何解决链表过长？红黑树有哪些特性？
### set
## 线程安全
## 线程池

[线程池的四种](https://blog.csdn.net/fanzhijian110/article/details/53572691)

`ewCachedThreadPool`存型线程池，先查看池中有没有以前建立的线程，如果有，就重用，如果没有，就建一个新的线程加入池中。如果线程池长度超过处理需要，可灵活回收空闲线程，若无可回收，则新建线程

`newFixedThreadPool` 定长线程池，可控制线程最大并发数。如果当前需要执行的任务超过池大小，那么多出的任务处于等待状态，直到有空闲下来的线程执行任务，如果当前需要执行的任务小于池大小，空闲的线程也不会去销毁。 

`newScheduledThreadPool` 调度型线程池,支持定时及周期性任务执行，也是一个固定长度的线程池。 

`newSingleThreadExecutor`  单线程化的线程池，它只会用唯一的工作线程来执行任务，保证所有任务按照指定顺序(FIFO, LIFO, 优先级)执行。如果当前线程意外终止，会创建一个新线程继续执行任务，这和我们直接创建线程不同，也和newFixedThreadPool(1)不同。 


1000个多并发线程，10台机器，每台机器4核的，设计线程池大小。
## 锁
[锁](https://www.cnblogs.com/dolphin0520/p/3923167.html)

怎么样实现公平锁？实现机制？

**Lock和synchronized的选择** 

　   1）Lock是一个接口，而synchronized是Java中的关键字，synchronized是内置的语言实现；

　　2）synchronized在发生异常时，会自动释放线程占有的锁，因此不会导致死锁现象发生；而Lock在发生异常时，如果没有主动通过unLock()去释放锁，则很可能造成死锁现象，因此使用Lock时需要在finally块中释放锁；

　　3）Lock可以让等待锁的线程响应中断，而synchronized却不行，使用synchronized时，等待的线程会一直等待下去，不能够响应中断；

　　4）通过Lock可以知道有没有成功获取锁，而synchronized却无法办到。

　　5）Lock可以提高多个线程进行读操作的效率。



ReadWriteLock就是读写锁，它是一个接口，ReentrantReadWriteLock实现了这个接口。 可以通过readLock()获取读锁，通过writeLock()获取写锁。 

### 锁优化
减少锁的时间
减少锁的粒度
锁粗话
读写锁
cas 
## Synchronized Lock
JDK动态加载。
## io

Java 的引用类型有哪几种：强引用、软引用、弱引用和虚引用
class字节码文件格式是什么


# 算法
## 排序
## 链表
## 外排序
## topk
LRU

# 数据库
## 索引
## 悲观乐观锁
## Sql优化

除非必要，否则不要在关键词前加% 

避免在索引字段上使用not，<>，!= 

避免对索引字段进行计算操作 

**避免在WHERE子句中使用in，not  in，or 或者having**。 




# 计算机网络
## 四挥手
## 三握手



# web方向
http与https
一次请求过程
session cookice
 http头部格式



## Redis

https://blog.csdn.net/xlgen157387/article/details/79530877

缓存穿透
找不到去查库、并且对该key并发请求量很大
对查询结果为空的情况也进行缓存
对key进行过滤

缓存雪崩
大量缓存集中在某一个时间段失效、不同的key，设置不同的过期时间、二级缓存。

缓存预热
缓存更新
缓存降级

bitmap
hash

两个10G的文件，里面是一些url，内存只有1G，如何将这两个文件合并，找到相同的url？

代码题：两个有序数组，数组中存在重复数字，合并成一个有序数组，去除重复数字。
比较关心平时的学习方式，项目中团队成员之间的沟通，如何解决分歧这些问题

字符串左旋
翻转左边，右边 翻转整体



###  面试大体上包括下面几方面知识类型：

Java基础、多线程、IO与NIO、虚拟机、设计模式

数据结构与算法（要有手写算法的能力）

计算机网络（TCP三次握手和四次挥手）

数据通信(RESTful、RPC、消息队列)

操作系统（Linux的基本命令以及使用）

主流框架（Spring底层原理与源码问的很多）

数据存储（最常见的是MySQL、Redis）

分布式

除了这些东西还有什么其他问题：

实际场景题

生活方面的问题

性格/其他方面的问题

### 面试常问的知识点

1）集合相关问题（必问）
HashMap、LinkedHashMap、ConcurrentHashMap、ArrayList、LinkedList的底层实现

HashMap和Hashtable的区别

ArrayList、LinkedList、Vector的区别

HashMap和ConcurrentHashMap的区别

HashMap和LinkedHashMap的区别

HashMap是线程安全的吗

ConcurrentHashMap是怎么实现线程安全的

HashMap 的长度为什么是2的幂次方

2）多线程并发相关问题（必问）
创建线程的3种方式

什么是线程安全

Runnable接口和Callable接口的区别

wait方法和sleep方法的区别

synchronized、Lock、ReentrantLock、ReadWriteLock

介绍下CAS(无锁技术)，什么是悲观锁和乐观锁

volatile关键字的作用和原理

什么是ThreadLocal

创建线程池的4种方式

ThreadPoolExecutor的内部工作原理

分布式环境下，怎么保证线程安全

synchronized和lock区别以及volatile和synchronized的区别

3）JVM相关问题
介绍下垃圾收集机制（在什么时候，对什么，做了什么）。

垃圾收集有哪些算法，各自的特点。

标记-清除算法、复制算法、标记-整理算法、分代收集算法

![](http://pic.wmgblog.pw/20180824180153.jpg)

类加载的过程。

![](http://pic.wmgblog.pw/20180824184042.png)

![](http://hi.csdn.net/attachment/201009/25/0_1285421756PHyZ.gif)



双亲委派模型。



如果一个类加载器收到了类加载的请求，它首先不会自己尝试去加载这个类，而是把这个请求委派给父类加载器，每一个层次的类加载器都是加此，因此所有的加载请求最终到达顶层的启动类加载器，只有当父类加载器反馈自己无法完成加载请求时（指它的搜索范围没有找到所需的类），子类加载器才会尝试自己去加载

有哪些类加载器。

能不能自己写一个类叫java.lang.String。

不能自己写以"java."开头的类，其要么不能加载进内存，要么即使你用自定义的类加载器去强行加载，也会收到一个SecurityException。

4）设计模式相关问题（必问）
设计模式比较常见的就是让你手写一个单例模式（注意单例模式的几种不同的实现方法）或者让你说一下某个常见的设计模式在你的项目中是如何使用的，另外面试官还有可能问你抽象工厂和工厂方法模式的区别、工厂模式的思想这样的问题。

另外，建议把代理模式、观察者模式、（抽象）工厂模式好好看一下，这三个设计模式很有用。

5）数据库相关问题，针对MySQL（必问）
给题目让你手写SQL。

有没有SQL优化经验。

MySQL索引的数据结构。

SQL怎么进行优化。

SQL关键字的执行顺序。

有哪几种索引。

什么时候该（不该）建索引。

Explain包含哪些列。

6）框架相关问题
Hibernate和Mybatis的区别。

Spring MVC和Struts2的区别。

Spring用了哪些设计模式。

Spring中AOP主要用来做什么。

Spring注入bean的方式。

什么是IOC，什么是依赖注入。

Spring是单例还是多例，怎么修改。

Spring事务隔离级别和传播性。

介绍下Mybatis/Hibernate的缓存机制。

Mybatis的mapper文件中#和$的区别。

Mybatis的mapper文件中resultType和resultMap的区别。

7）其他遇到问题
介绍下栈和队列。

IO和NIO的区别。

接口和抽象类的区别。

int和Integer的自动拆箱/装箱相关问题。

常量池相关问题。

==和equals的区别。

什么是JDK?什么是JRE？什么是JVM？三者之间的联系与区别

Java和C++的区别

重载和重写的区别。

String和StringBuilder、StringBuffer的区别。

静态变量、实例变量、局部变量线程安全吗，为什么。

try、catch、finally都有return语句时执行哪个。

介绍下B树、二叉树。

分布式锁的实现。

分布式session存储解决方案。

常用的linux命令。

四  一些经验分享
先投一些普通公司，等面出了心得再去投理想的公司。

不熟悉的技术不要主动提。

对于那种实习期6个月还打8折的公司，除非你没有其他选择了，否则不要去。 另外，小公司喜欢在薪水上压你，开的时候适当提高。

不要去参加招聘会，纯粹是浪费时间。

把面试当作一次技术的交流，不要太在意是否能被录取。

公司一般面完就决定是否录取了，让你回去等消息这种情况一般没戏，无论你自己觉得面的有多好。

尽量少通过电话面试，效果不好。

在面试的日子里，要保持每天学习，无论是学习新东西还是复习旧东西。

拿到offer了，问问自己这个公司让自己100%满意了吗，如果不是，请继续努力找更好的。

通过面试官可以大概判断这家公司的情况。

拉勾投的简历很多会被筛掉，但是拉勾还是面试机会的最主要来源。 理想的公司可以多投几次，我有好几次都是第一次投被筛掉，多投几次就过的经验。 问到自己有深入研究过的知识，抓住机会好好表现，不要轻易放过。
