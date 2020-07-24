### 第一章 Node简介

Node的主要要点：

* 事件驱动
* 非阻塞I/O

为什么叫Node？

> 通过通信协议来组织许多Node，非常容易通过扩展来达成构建大型网络应用的目的，每一个Node进程都构成这个网络应用中的一个节点，这便是它名字的含义。

#### 1.1 Node的特点

* 异步I/O
    
Don't call me, I will call you（异步调用原则）
```
var fs = require('fs');
fs.readFile('/path', function(err, file){
    console.log('读取文件完成')
});
console.log('发起读取文件');
```
* 事件与回调函数

```
var http = require('http');
var querystring = require('querystring');

...
```
* 单线程

在Node中，JS与其余线程是无法共享任何状态的。单线程最大的好处是不用像多线程编程那样处处在意状态的同步问题，这里没有死锁的存在，也没有线程上下文交换所带来的性能上的开销。

单线程的弱点：

    - 无法利用多核CPU
    - 错误会引起整个应用退出，应用的健壮性值得考验
    - 大量计算占用CPU导致无法继续调用异步I/O
    
> Web Workers能够创建工作线程来进行计算，以解决JS大计算阻塞UI渲染的问题。工作线程为了不阻塞主线程，通过消息传递的方式来传递运行结果，这使得工作线程不能访问到主线程的UI。

* 跨平台

#### 1.2 Node的应用场景（I/O密集型）

思考一个问题： Node在商城中的实践，具体可以做哪些事情，要怎么来实现，可以达到一个怎样的效果？123