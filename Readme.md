Laraveler、PHPer面试指南

> 其实就是最近找工作发现的一些你可能经常用，但是理论说不清楚的问题，这里做的收集整理

### PHP
- PHP7和PHP5的区别，具体多了哪些新特性？
    * 性能提升了两倍
    * 结合比较运算符 (<=>)
    * 标量类型声明
    * 返回类型声明
     * try...catch 增加多条件判断，更多 Error 错误可以进行异常处理
     * 匿名类，现在支持通过new class 来实例化一个匿名类，这可以用来替代一些“用后即焚”的完整类定义
  [参考地址](http://php.net/manual/zh/migration70.new-features.php)
- 为什么PHP7比PHP5性能提升了？
    * 变量存储字节减小，减少内存占用，提升变量操作速度
    * 改善数组结构，数组元素和 hash 映射表被分配在同一块内存里，降低了内存占用、提升了 cpu 缓存命中率
    * 改进了函数的调用机制，通过优化参数传递的环节，减少了一些指令，提高执行效率
- 你知道哪些PHP自带的数组排序方法？

    >   sort() 函数用于对数组单元从低到高进行排序。
        rsort() 函数用于对数组单元从高到低进行排序。
        asort() 函数用于对数组单元从低到高进行排序并保持索引关系。
        arsort() 函数用于对数组单元从高到低进行排序并保持索引关系。
        ksort() 函数用于对数组单元按照键名从低到高进行排序。
        krsort() 函数用于对数组单元按照键名从高到低进行排序。
        
### laravel 模块
- 服务提供者是什么？     
    * 服务提供者是所有 Laravel 应用程序引导启动的中心, Laravel 的核心服务器、注册服务容器绑定、事件监听、中间件、路由注册以及我们的应用程序都是由服务提供者引导启动的。
- Contract的原理？   
     * Contract（契约）是 laravel 定义框架提供的核心服务的接口。Contract 和 Facades 并没有本质意义上的区别，其作用就是使接口低耦合、更简单。
- IoC容器是什么？
    * IoC（Inversion of Control）译为 「控制反转」，也被叫做「依赖注入」(DI)。什么是「控制反转」？对象 A 功能依赖于对象 B，但是控制权由对象 A 来控制，控制权被颠倒，所以叫做「控制反转」，而「依赖注入」是实现 IoC 的方法，就是由 IoC 容器在运行期间，动态地将某种依赖关系注入到对象之中。
   
    其作用简单来讲就是利用依赖关系注入的方式，把复杂的应用程序分解为互相合作的对象，从而降低解决问题的复杂度，实现应用程序代码的低耦合、高扩展。
   
    Laravel 中的服务容器是用于管理类的依赖和执行依赖注入的工具。
    [参考地址](http://www.cnblogs.com/DebugLZQ/archive/2013/06/05/3107957.html) 
    
- 依赖注入的原理？   
     * @overtrue 一句话解释：依赖注入只是一种模式：把当前类依赖的第三方实例通过参数传入的形式引入，但是如果手写依赖注入会比较费劲，管理起来也比较麻烦，因为要关心那么多类的依赖，于是就有了一个容器来自动解决这个问题，利用反射API检查类型，然后递归解决依赖。
  
- Facade是什么？  
    * Facades（一种设计模式，通常翻译为外观模式）提供了一个"static"（静态）接口去访问注册到 IoC 容器中的类。提供了简单、易记的语法，而无需记住必须手动注入或配置的长长的类名。此外，由于对 PHP 动态方法的独特用法，也使测试起来非常容易。
- 了解过Composer？实现原理是什么？
    * Composer 是 PHP 的一个依赖管理工具。工作原理就是将已开发好的扩展包从 packagist.org composer 仓库下载到我们的应用程序中，并声明依赖关系和版本控制。
  
### 缓存
- Redis、Memecache这两者有什么区别？
    * Redis 支持更加丰富的数据存储类型，String、Hash、List、Set 和 Sorted Set。Memcached 仅支持简单的 key-value 结构。
    * Memcached key-value存储比 Redis 采用 hash 结构来做 key-value 存储的内存利用率更高。
    * Redis 提供了事务的功能，可以保证一系列命令的原子性
    * Redis 支持数据的持久化，可以将内存中的数据保持在磁盘中
    * Redis 只使用单核，而 Memcached 可以使用多核，所以平均每一个核上 Redis 在存储小数据时比 Memcached 性能更高。
- Redis如何实现持久化？      
    * RDB 持久化，将 redis 在内存中的的状态保存到硬盘中，相当于备份数据库状态。
    * AOF 持久化（Append-Only-File），AOF 持久化是通过保存 Redis 服务器锁执行的写状态来记录数据库的。相当于备份数据库接收到的命令，所有被写入 AOF 的命令都是以 redis 的协议格式来保存的。
    
### 设计模式
- 了解哪些设计模式？
    *   ##### 创建性模式
       	> 单例模式、简单工厂模式、工厂方法模式、抽象工厂模式、对象池模式、 原型模式
        
        ##### 结构性模式
        > 适配器模式、桥接模式、组合模式、装饰器模式、依赖注入、门面模式、链式操作、代理模式
       
        ##### 注册器模式
       	> 行为性模式、观察者模式、责任链模式、模板方法、策略模式、访问者模式、遍历模式、空对象模式、状态模式、命令模式
       
     [参考资料](http://larabase.com/collection/5/post/143)
     熟记SOLID原则
     
### 数据库
- 什么是索引，作用是什么？常见索引类型有那些？Mysql 建立索引的原则？
    * 索引是一种特殊的文件,它们包含着对数据表里所有记录的引用指针，相当于书本的目录。其作用就是加快数据的检索效率。常见索引类型有主键、唯一索引、复合索引、全文索引。

    * 索引创建的原则
        * 最左前缀原理
        * 选择区分度高的列作为索引
        * 尽量的扩展索引，不要新建索引
    * 高并发如何处理？
        * 使用缓存
        * 优化数据库，提升数据库使用效率
        * 负载均衡        
     
# 其他待解决问题
   - 分库分表怎么设计
   - 如何处理 MySQL 死锁？
   - 谈谈你对闭包的理解
   - PHP 内存回收机制
   - 如何解决 PHP 内存溢出问题
   - 数据库优化的方法
   - 简述 Laravel 的运行原理
   - Laravel 路由实现原理
   - cookie 和 session 区别，session 保存在服务器的哪里？服务端是如何获取客户端的cookie？
   - 服务器集群搭建、负载均衡、反向代理
   - 服务器常用命令     