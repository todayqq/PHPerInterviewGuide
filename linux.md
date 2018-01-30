### Linux

- 说一些常用的 Linux shell 命令

> 这个问题就不回答了，自由发挥

- Linux 硬链接和软链接有什么区别？

> 1. 硬链接不可以跨分区，软件链可以跨分区
> 2. 硬链接指向一个 i 节点，而软链接则是创建一个新的 i 节点
> 3. 删除硬链接、软链接文件，对原文件都没有什么影响，但是如果删除原文件，会导致软连接失效，硬链接无影响。


- 建立软链接(快捷方式)，以及硬链接的命令。

> 软链接： ln -s slink source  
> 硬链接： ln link source

- 怎么利用 ps 查看指定进程的信息

> ps -ef | grep pid

-  Linux 下命令有哪几种可使用的通配符？分别代表什么含义?

> “？” 可替代单个字符。   
> “*” 可替代任意多个字符。  
> 中括号“[charset]”可替代 charset 集中的任何单个字符，如[a-z]，[abABC]

### Git

- Push 代码时发生突破如何处理？

> 1、使用 git stash 将本地文件暂存
> 
> 2、更新代码 git pull
> 
> 3、还原暂存的内容 git stash pop

- 线上服务器代码出了问题如何回滚？

> git reset --hard HEAD^

- GitFlow 中都有那些分支？

> 两个长期维护分支
> 
> - 主分支（master）
> - 开发分支 （develop）
> 
> 三种短期分支
> 
> - 功能分支（feature branch）
> - 补丁分支（hotfix branch）
> - 预发分支（release branch）

### 扩展阅读

- [linux面试常问命令](http://blog.csdn.net/u010842515/article/details/72732106)
- [Linux常见面试题](https://www.leolan.top/index.php/posts/36.html)
- [Git教程](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
- [Gitflow 工作流](https://laravel-china.org/articles/6318/gitflow-workflow)