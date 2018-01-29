---
title: linux命令学习-top
date: 2018-01-24 09:57:29
tags: 
 - top 
 - linux_cmd
categories:
 - linux
---

```shell
# top   //linux 命令行
```

![](/images/article/top.png)

图中所示是在我自己的ubuntu中使用`top`时所展示的。

<!--more-->

## top 命令

```bash
top - 10:42:38 up 2 days,  1:00,  1 user,  load average: 0.30, 0.24, 0.18
Tasks: 275 total,   1 running, 274 sleeping,   0 stopped,   0 zombie
%Cpu(s):  2.1 us,  0.5 sy,  0.0 ni, 97.3 id,  0.0 wa,  0.0 hi,  0.1 si,  0.0 st
KiB Mem :  4028316 total,   152980 free,  1603968 used,  2271368 buff/cache
KiB Swap:  2094076 total,  2094076 free,        0 used.  1970028 avail Mem

PID   USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                         
49452 li        20   0 2179732 298492 186780 S  13.9  7.4   0:36.57 Web Content
```

## 解释

1. `top - 10:42:38 up 2 days,  1:00,  1 user,  load average: 0.30, 0.24, 0.18`
10:42:38 — 当前系统时间    
up 2 days, 1:00 — 系统系统运行时间    
1 users — 当前登录用户数    
load average: 0.30, 0.24, 0.18 — 系统负载 三个数分别是1分钟、5分钟、15分钟的负载情况    

2. `Tasks: 275 total,   1 running, 274 sleeping,   0 stopped,   0 zombie`、
Tasks: 任务/进程
275 total,  总共275个进程
1 running,  1个正在运行进程  
274 sleeping,   274个睡眠进程
0 stopped,  0个停止的进程     
0 zombie,   0个僵尸进程

3. `%Cpu(s):  2.1 us,  0.5 sy,  0.0 ni, 97.3 id,  0.0 wa,  0.0 hi,  0.1 si,  0.0 st`
%Cpu(s):    CPU占用       
2.1 us,  用户空间占用CPU百分比   
0.5 sy,  内核空间占用CPU百分比   
0.0 ni,  用户进程空间内改变过优先级的进程占用的百分比     
97.3 id, 空闲CPU百分比   
0.0 wa,  等待输入输出(IO)的CPU百分比      
0.0 hi,  硬件CPU中断占用的百分比      
0.1 si,  软件中断占用的百分比      
0.0 st   虚拟机占用百分比

4. `KiB Mem :  4028316 total,   152980 free,  1603968 used,  2271368 buff/cache`
KiB Mem :  物理内存
4028316 total,      物理内存总量   
152980 free,        空闲内在总量      
1603968 used,       使用的物理内存总量       
2271368 buff/cache  用作内核缓存的内在总量     

5. `KiB Swap:  2094076 total,  2094076 free,        0 used.  1970028 avail Mem`
KiB Swap:       交换分区        
2094076 total,  交换分区总量        
2094076 free,   空闲交换分区总量        
0 used.         使用的交换分区总量       
1970028 avail Mem   可用内存总量

6. `PID   USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND`
PID     进程ID        
USER    进程所有者          
PR      优先级     
NI      nice值，负值表示高优先级，正值表示低优先级         
VIRT    进程使用的虚拟内在总量，单位kb VIRT=SWAP+RES      
RES     进程使用的未被换出的  内存大小，单位kb RES=CODE+DATA     
SHR     共享内存大小，单位kb     
S       进程状态。D=不可中断的睡眠状态 R=运行 S=睡眠 T=跟踪/停止 Z=僵尸进程
%CPU    上次更新到现在的CPU时间占用百分比      
%MEM    进程使用的物理内存百分比        
TIME+   进程使用的CPU时间总计，单位1/100秒       
COMMAND 进程名称（命令名/命令行）


## 总结

top命令是Linux下常用的性能分析工具，能够实时显示系统中各个进程的资源占用状况，类似于Windows的任务管理器。top是一个动态显示过程,即可以通过用户按键来不断刷新当前状态.如果在前台执行该命令,它将独占前台,直到用户终止该程序为止.比较准确的说,top命令提供了实时的对系统处理器的状态监视.它将显示系统中CPU最“敏感”的任务列表.该命令可以按CPU使用.内存使用和执行时间对任务进行排序；而且该命令的很多特性都可以通过交互式命令或者在个人定制文件中进行设定。 

更详细的解释看`top(1)`

## 参考文档

- [Linux top命令的用法详细详解](https://www.cnblogs.com/edgedance/p/7044753.html)    
- [linux的top命令参数详解](https://www.cnblogs.com/ggjucheng/archive/2012/01/08/2316399.html)  



