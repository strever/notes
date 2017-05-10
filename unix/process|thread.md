
1[^1]

2[^2]

3[^3]




[^1]: http://www.cnblogs.com/lmule/archive/2010/08/18/1802774.html
[^2]: http://www.cnblogs.com/tiankong101/p/4229584.html
[^3]: http://www.cnblogs.com/ChunJian-YANG/p/5506209.html




---







子进程从父进程继承了其占用内存中的所有内容，以及所有父进程已打开的文件描述符。其中继承的内存数据只有当子进程做修改时才真正发生一份拷贝。

fork子进程会返回两次，一次子进程pid；一次由子进程返回的nil

父进程的退出并不影响子进程继续运行

## 看顾进程

master/worker 或者 preforking

父进程衍生出多个子进程，确保他们能够保持响应，在他们退出时做出回应

子进程退出的信息会被存储到内核的队列上去，等待主进程去处理。如果不打算让主进程处理应该讲子进程分离`detach`掉，主进程不处理子进程也不分离，此时子进程便成了僵尸进程

任何已经结束的进程，如果他的状态信息一直未能被读取，那么他就是僵尸进程。



## 进程间通信ipc


- 管道

主进程可以io只读，fork出来的子进程会复制io的读和写文件描述符，子进程可以只写，

如果写不close，读会一直阻塞持续读取直到eof


- 套接字对

unix套接字是一种只能用于在同一台物理主机中进行通信的套接字，它比TCP套接字快的多，非常适合用于IPC











---











Linux/Unix系统

- 深入理解计算机系统
- UNIX环境高级编程
- 深入理解Linux内核

网络通信编程

- UNIX网络编程
- TCP/IP详解
- Linux多线程服务端编程

数据结构与算法

- 算法导论
- 《数据结构》（C语言版）
- C程序设计语言
- PHP语言
- PHP5权威编程


http://www.kegel.com/c10k.html

https://my.oschina.net/xianggao/blog/662803
