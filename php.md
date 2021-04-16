PHP 篇收集了一些常见的基础、进阶面试题。

### 基础篇

- Get 和 POST 的区别

> 1. 传值方式：get 把参数数据加到表单action指定的url后面，参数与数据一一对应，可以在url中看到。post采用HTTP post的机制，将表单的参数内容添加到Html 头内一起传递到action所指的url地址，用户看不到此过程。
> 2. 大小：get传送的数据很小，不能大于2kb（2048字节，1024字符）。post传送的数据大小默认无限制。
> 3. 执行效率：get 的执行效率比post好。
> 4. 安全性：post安全性比get好。
> 5. 使用创景：做数据查询时，建议用get方式。做数据增加、删除、更新，建议用post方式。

- 单引号和双引号的区别

> 1. 单引号不会读取里面的变量；作为纯字符串处理，读取速度快。
> 2. 双引号会尝试读取里面的变量（即使里面没有），这样读取速度慢。

- isset、empty、is_null 的区别

> 1. isset 判断变量是否已存在(是否声明，是否赋值)，如果变量存在则返回 TRUE，否则返回 FALSE。
> 2. empty 若变量已存在、非空字符串或者非零，则返回 false 值；否则返回 true。
> 3. is_null 检测变量是否为NULL。

\- | - | - | -
--- | --- | --- | ---
| 变量  | isset($a) | empty($a) | is_null($a) |
| $a=""     | true | true | false |
| $a=null   | true | true | true |
| $a=array() | true | true | false |
| $a=false | true | true | false |
| $a=true | true | false | false|
| $a=1 | true | false | false |
| $a=0 | true | true | false |
| $a="0" | true | true | false |

- echo、print、print_r()、var_export()、var_dump()之间的区别

> 1. echo和print是语言结构，非函数，能打印整型和字符串。
> 2. print_r()和var_export()打印整型、字符串外，还能打印数组、对象，以键值对形式打印数组、对象。var_export()还可打印布尔值，var_export()在第二个参数设置true，不会打印变量，而是将其以字符串形式返回，返回值可以赋值给php变量。
> 3. var_dump()除了打印整型、字符串、数组、对象，还能打印布尔型。而且是输出变量类型、长度和值。

- include、require、include_once、 require_once的区别

> 1. require 和 include 几乎完全一样，除了处理失败的方式不同之外。require 在出错时产生 E_COMPILE_ERROR 级别的错误。换句话说将导致脚本中止而 include 只产生警告（E_WARNING），脚本会继续运行。
> 2. include_once 和 requrei_once 语句在脚本执行期间包含并运行指定文件, 并只会包含进来一次。

- 传值、传地址、传引用的区别？

> 1. 传值是把实参的值赋值给行参，那么对行参的修改，**不会影响实参的值**。
> 2. 传地址是传值的一种特殊方式，只是他传递的是地址，不是普通的如int，那么传地址以后，实参和行参都指向同一个对象。
> 3. 传引用真正的以地址的方式传递参数，传递以后，行参和实参都是同一个对象，只是他们名字不同而已，**对行参的修改将影响实参的值**。

- Cookie 和 Session 的区别和关系

> 1. Cookie 在客户端（浏览器），Session 在服务器端
> 2. Session 比 Cookie 安全性更高
> 3. 单个 Cookie 保存的数据不能超过 4K
> 4. Session 是基于 Cookie，如果浏览器禁用了 Cookie，Session 也会失效（但是可以通过其它方式实现，比如在 url 中传递 Session ID）

- 什么是 MVC？

> MVC（Model-View-Controller）是软件工程中的一种软件架构模式。MVC 的目标是将业务逻辑从用户界面的考虑中分离。
> 在 MVC 中 ，Model 代表数据和业务规则；View 包含了用户界面元素，例如文本，表单等；Controller 则管理模型和视图中的通信。

- RESTFul 架构

> 1. 每一种URI都是一种资源
> 2. 客户端和服务器之间，传递这种资源的某种表现层
> 3. 客户端通过HTTP动词[Get(Select)，Post(Create)，Delete(Delete)，Patch(Update), Put(Update)]，对服务器端资源进行操作，实现“表现层状态转变”


了解更多，请看[理解RESTful架构](http://www.ruanyifeng.com/blog/2011/09/restful)
RESTFul API 设计，请看[RESTful API 设计指南](http://www.ruanyifeng.com/blog/2014/05/restful_api.html)

### 进阶篇

- 简述 S.O.L.I.D 设计原则

\- | - | -
--- | --- | ---
SRP	| 单一职责原则	| 一个类有且只有一个更改的原因
OCP	| 开闭原则	| 能够不更改类而扩展类的行为
LSP	| 里氏替换原则	| 派生类可以替换基类使用
ISP	| 接口隔离原则	| 使用客户端特定的细粒度接口
DIP	| 依赖反转原则	| 依赖抽象而不是具体实现

- 列举一些 PHP 中的设计模式？

> - **单例模式**：保证在整个应用程序的生命周期中，任何一个时刻，单例类的实例都只存在一个，同时这个类还必须提供一个访问该类的全局访问点。
> - **工厂模式**：定义一个创建对象的接口，但是让子类去实例化具体类。工厂方法模式让类的实例化延迟到子类中。
> - **观察者模式**：观察者模式有时也被称作发布/订阅模式，该模式用于为对象实现发布/订阅功能：一旦主体对象状态发生改变，与之关联的观察者对象会收到通知，并进行相应操作。
> - **适配器模式**：适配器模式将一个类的接口转换成客户希望的另外一个接口，使得原本由于接口不兼容而不能一起工作的那些类可以在一起工作。
> - **依赖注入模式**：依赖注入（Dependency Injection）是控制反转（Inversion of Control）的一种实现方式。要实现控制反转，通常的解决方案是将创建被调用者实例的工作交由 IoC 容器来完成，然后在调用者中注入被调用者（通过构造器/方法注入实现），这样我们就实现了调用者与被调用者的解耦，该过程被称为依赖注入。
> - **门面模式**：门面模式（Facade）又称外观模式，用于为子系统中的一组接口提供一个一致的界面。 

了解更多，请看[PHP 设计模式系列](http://laravelacademy.org/post/2465.html)。

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

- Redis、Memcached 这两者有什么区别？

> 1. Redis 支持更加丰富的数据存储类型，String、Hash、List、Set 和 Sorted Set。Memcached 仅支持简单的 key-value 结构。
> 2. Memcached key-value存储比 Redis 采用 hash 结构来做 key-value 存储的内存利用率更高。
> 3. Redis 提供了事务的功能，可以保证一系列命令的原子性
> 4. Redis 支持数据的持久化，可以将内存中的数据保持在磁盘中
> 5. Redis 只使用单核，而 Memcached 可以使用多核，所以平均每一个核上 Redis 在存储小数据时比 Memcached 性能更高。

- Redis 如何实现持久化？

> 1. RDB 持久化，将 Redis 在内存中的的状态保存到硬盘中，相当于备份数据库状态。
> 2. AOF 持久化（Append-Only-File），AOF 持久化是通过保存 Redis 服务器锁执行的写状态来记录数据库的。相当于备份数据库接收到的命令，所有被写入 AOF 的命令都是以 Redis 的协议格式来保存的。

### Web 安全防范

- CSRF 是什么？如何防范？

> CSRF（Cross-site request forgery）通常被叫做「跨站请求伪造」，可以这么理解：攻击者盗用用户身份，从而欺骗服务器，来完成攻击请求。

防范措施：

1. 使用验证码
2. 给每一个请求添加令牌 token 并验证

- XSS 是什么？如何防范？

> XSS(Cross Site Scripting)，跨站脚本攻击，攻击者往 Web 页面里插入恶意 Script 代码，当用户浏览该页之时，嵌入其中 Web 里面的 Script 代码会被执行，从而达到恶意攻击用户的目的。

防止 XSS 攻击的方式有很多，其核心的本质是：永远不要相信用户的输入数据，始终保持对用户数据的过滤。

- 什么是 SQL 注入？如何防范？

> SQL 注入就是攻击者通过一些方式欺骗服务器，结果执行了一些不该被执行的 SQL。

SQL 注入的常见场景

1. 数据库里被注入了大量的垃圾数据，导致服务器运行缓慢、崩溃。
2. 利用 SQL 注入暴露了应用程序的隐私数据

防范措施：

1. 保持对用户数据的过滤
2. 不要使用动态拼装 SQL
3. 增加输入验证，比如验证码
4. 对隐私数据加密，禁止明文存储

### 扩展阅读

- [3年PHPer的面试总结](http://coffeephp.com/articles/4?utm_source=laravel-china.org)
- [垃圾回收机制](http://docs.php.net/manual/zh/features.gc.performance-considerations.php)
- [S.O.L.I.D 面向对象设计](https://laravel-china.org/articles/4160/solid-object-oriented-design-and-programming-oodoop-notes?order_by=created_at&)
- [浅谈IOC--说清楚IOC是什么](http://www.cnblogs.com/DebugLZQ/archive/2013/06/05/3107957.html)
- [Redis和Memcached的区别](https://www.biaodianfu.com/redis-vs-memcached.html)
- [CSRF攻击与防御](https://www.cnblogs.com/phpstudy2015-6/p/6771239.html)
- [XSS跨站脚本攻击](https://www.cnblogs.com/phpstudy2015-6/p/6767032.html#_label9)
- [PHP 设计模式系列](http://laravelacademy.org/post/2465.html)
- [CGI、FastCGI和PHP-FPM关系图解](https://www.awaimai.com/371.html#comment-17650)
