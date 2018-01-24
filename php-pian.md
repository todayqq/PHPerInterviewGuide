PHP 篇收集了一些常见的基础、进阶面试题，基础的面试题不再作答。

### 基础篇

- Get 和 POST 的区别
- Cookie 和 Session 的区别和关系
- 单引号和双引号的区别
- isset 和 empty 的区别
- echo、print_r、print、var_dump 之间的区别
- 什么是 MVC？
- 传值和传引用的区别？

### 进阶篇

- 简述 S.O.L.I.D 设计原则


- | - | -
---|--- | ---
SRP	| 单一职责原则	 | 一个类有且只有一个更改的原因
OCP	| 开闭原则	| 能够不更改类而扩展类的行为
LSP	| 里氏替换原则	| 派生类可以替换基类使用
ISP	| 接口隔离原则	| 使用客户端特定的细粒度接口
DIP	| 依赖反转原则	| 依赖抽象而不是具体实现

- PHP7 和 PHP5 的区别，具体多了哪些新特性？

> 1. 性能提升了两倍 
> 2. 增加了结合比较运算符 (<=>)
> 3. 增加了标量类型声明、返回类型声明
> 4. `try...catch` 增加多条件判断，更多 Error 错误可以进行异常处理
> 5. 增加了匿名类，现在支持通过new class 来实例化一个匿名类，这可以用来替代一些“用后即焚”的完整类定义

- 为什么 PHP7 比 PHP5 性能提升了？

> 1. 变量存储字节减小，减少内存占用，提升变量操作速度
> 2. 改善数组结构，数组元素和 hash 映射表被分配在同一块内存里，降低了内存占用、提升了 cpu 缓存命中率
> 3. 改进了函数的调用机制，通过优化参数传递的环节，减少了一些指令，提高执行效率

- 简述一下 PHP 垃圾回收机制（GC）

> PHP 5.3 版本之前都是采用引用计数的方式管理内存，PHP 所有的变量存在一个叫 `zval` 的变量容器中，当变量被引用的时候，引用计数会+1，变量引用计数变为0时，PHP 将在内存中销毁这个变量。
> 
> 但是引用计数中的循环引用，引用计数不会消减为 0，就会导致内存泄露。
> 
> 在 5.3 版本之后，做了这些优化：
> 
> 1. 并不是每次引用计数减少时都进入回收周期，只有根缓冲区满额后在开始垃圾回收；
> 2. 可以解决循环引用问题；
> 3. 可以总将内存泄露保持在一个阈值以下。

了解更多可以查看 PHP 手册，[垃圾回收机制](http://docs.php.net/manual/zh/features.gc.performance-considerations.php)。

- 如何解决 PHP 内存溢出问题

> 1. 增大 PHP 脚本的内存分配
> 2. 变量引用之后及时销毁
> 3. 将数据分批处理

- Redis、Memecached 这两者有什么区别？

> 1.  Redis 支持更加丰富的数据存储类型，String、Hash、List、Set 和 Sorted Set。Memcached 仅支持简单的 key-value 结构。
> 2.  Memcached key-value存储比 Redis 采用 hash 结构来做 key-value 存储的内存利用率更高。
> 3.  Redis 提供了事务的功能，可以保证一系列命令的原子性
> 4.  Redis 支持数据的持久化，可以将内存中的数据保持在磁盘中
> 5. Redis 只使用单核，而 Memcached 可以使用多核，所以平均每一个核上 Redis 在存储小数据时比 Memcached 性能更高。

- Redis 如何实现持久化？

> 1. RDB 持久化，将 Redis 在内存中的的状态保存到硬盘中，相当于备份数据库状态。
> 2. AOF 持久化（Append-Only-File），AOF 持久化是通过保存 Redis 服务器锁执行的写状态来记录数据库的。相当于备份数据库接收到的命令，所有被写入 AOF 的命令都是以 Redis 的协议格式来保存的。

### 扩展阅读

- [3年PHPer的面试总结](http://coffeephp.com/articles/4?utm_source=laravel-china.org)
- [垃圾回收机制](http://docs.php.net/manual/zh/features.gc.performance-considerations.php)
- [S.O.L.I.D 面向对象设计](https://laravel-china.org/articles/4160/solid-object-oriented-design-and-programming-oodoop-notes?order_by=created_at&)
- [浅谈IOC--说清楚IOC是什么](http://www.cnblogs.com/DebugLZQ/archive/2013/06/05/3107957.html)
- [Redis和Memcached的区别](https://www.biaodianfu.com/redis-vs-memcached.html)