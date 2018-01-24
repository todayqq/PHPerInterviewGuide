> Web 篇的文章，PHPer 大神们可以直接略过。

对于大公司，很少会有全栈工程师这个岗位，全栈是个花哨的词，对于现在比较热门的技术，不论是 Vue 还是 Laravel，只要智商不差，看着文档，都能写出一个 CURD 来，但是这就叫全栈了吗？

比如 Vue 中的 MVVM，其中 VM 视图的原理是什么？Laravel 为什么要这么设计？

会用这种技术栈，其实只是学到的只是皮毛，可以会用，但是必须要有自己精通擅长的一面，一定要做到人无我有，人有我优。

---

### 面试题

1. 谈谈对 Web 语义化的理解

> 语义化的含义就是用正确的标签做正确的事情，语义化让页面的内容结构化，结构更清晰，便于对浏览器、搜索引擎解析，利于 SEO，也有利于代码阅读、便于维护。

2. 简述 HTTP 协议的工作流程「重要」

> 1. 地址解析;  
> 在浏览器中输入 URL，浏览器会从中分解出协议名、主机名、端口、对象路径等部分
> 2. 封装 HTTP 请求数据包
> 3. 浏览器获取主机 IP 地址，建立 TCP 链接（TCP 的三次握手）
> 4. TCP 链接建立后发送 HTTP 请求  
> 请求方式的格式为：统一资源标识符（URL）、协议版本号，后边是 MIME 信息包括请求修饰符、客户机信息和可内容。
> 5. 服务器接到请求后，给予相应的响应信息  
> 其格式为一个状态行，包括信息的协议版本号、一个成功或错误的代码，后边是 MIME 信息包括服务器信息、实体信息和可能的内容
> 6. 服务器断开 TCP 连接

3. 为什么使用 HTTPS？实现原理是什么？ 

> HTTPS（超文本传输安全协议）是一种通过计算机网络进行安全通信的传输协议，提供对网站服务器的身份认证，保护数据传输的完整性、安全性。
> 
> 实现过程如下：
> 1. 客户端通过 TCP 和服务器建立连接之后，第一次握手的时候请求证书，服务器向客户端返回证书
> 2. 客户端在收到服务端证书后，确认证书是否有效，生成对称秘钥并使用服务器的公共秘钥进行加密，然后发送给服务器。
> 3. 服务器使用它的私钥对它进行解密，这样两台计算机可以开始进行对称加密进行通信。


4. 写出一个使用 flex 布局，在 div 垂直居中的 css 代码

```
div {
    display: flex;
    justify-content: center;
    align-items: center;
}
```

5. 为什么把 JavaScript 文件放在 Html 底部

> 1. 因为浏览器渲染 HTML 文件是从上往下渲染的，JavaScript 放在 Html 头部，会阻碍浏览器的渲染速度，增加用户的等待时间
> 2. 浏览器加载 JavaScript 脚本之后会自动执行，如果放在头部，此时的 Dom 树还没有加载完，很容易出 Bug

6. 谈谈对 JavaScript 闭包的理解

> 闭包是 JavaScript 函数的一种，声明即运行，可以在函数内部调用外部变量。

7. 如何处理 Ajax 跨域问题
 
> 1. 代理
> 2. JsonP
> 3. iframe 等等……

前端的知识比较多，一些比较基础的问题，就不再整理了，比如给 Http 常见状态码，Html5 多了那些标签，CSS 如何清除浮动等等。

如果大家有兴趣，可以阅读这些前端的常见面试题和资料。

### 扩展阅读

- [收集的前端面试题和答案](https://github.com/qiu-deqing/FE-interview)
- [前端开发面试题](https://github.com/markyun/My-blog/tree/master/Front-end-Developer-Questions/Questions-and-Answers)
- [史上最全的web前端面试题汇总及答案1](https://www.jianshu.com/p/2f7eb1ad7174)
- [前端工程师手册](https://leohxj.gitbooks.io/front-end-database/index.html)
- [HTTP协议：工作原理](http://blog.csdn.net/anndy_/article/details/77198883)
- [SSL/TLS协议运行机制的概述](http://www.ruanyifeng.com/blog/2014/02/ssl_tls.html)