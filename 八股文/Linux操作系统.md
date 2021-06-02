# Linux系统

## CPU
![CPU性能指标](https://static001.geekbang.org/resource/image/1e/07/1e66612e0022cd6c17847f3ab6989007.png)
### uptime
Load Average
### 上下文切换
`vmstat` 
```

# 每隔5秒输出1组数据
$ vmstat 5
procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu-----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st
 0  0      0 7005360  91564 818900    0    0     0     0   25   33  0  0 100  0  0
```
### CPU使用率
CPU 使用率，就是除了空闲时间外的其他时间占总 CPU 时间的百分比
### CPU架构
![CPU架构](https://static001.geekbang.org/resource/image/aa/33/aa08816b60e453b52b5fae5e63549e33.png)

### 软中断

## 内存
### 虚拟内存和物理内存的区别

### 虚拟内存加载到物理内存的方法

### 页淘汰策略


## Linux网络编程
### epoll原理
### 多路复用IO区别
### 主机接受一个数据的过程
## Linux常用命令

## Linux进程
### 进程和线程区别
进程是程序在内存中的副本, 是操作系统资源分配和调度的基本单位
线程是CPU分配和调度的基本单位, 和进程的关系是从属关系[存疑] 

### 多线程和多进程
创建切换销毁代价
调试
稳定性

### 为什么python不支持多线程呢?
CPython interpreter does not support true multi-core execution via multithreading

### 协程和线程区别
协程被认为是用户态线程, 它具有线程的特点但是在进行协程切换时无需进入内核态进行CPU上下文切换

因为协程
### top
* 进程状态 
R D Z S I

### 进程间通信

### 信号和信号量的区别
信号与信号量的区别： 1.信号：（signal）是一种处理异步事件的方式。用于通知接受进程有某种事件发生
2.信号量：（Semaphore）进程间通信处理同步互斥的机制。

## 命令
### 统计ip 
`awk '{print $1}' /var/log/nginx/access.log | sort | uniq -c | sort -nr -k1 | head -n 10`
### linux查看端口是否占用
