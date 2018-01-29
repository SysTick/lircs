---
title: aupe_note.md
date: 2018-01-18 14:33:31
tags:
---

linux 文件IO函数

> 本文介绍的函数被称为不带缓存的IO(unbuffered IO)，不带缓存是指每一个read、write函数都调用内核中的一个系统调用。
这些不带缓存的IO函数不是ANSIC C的组成部分，但是是POSIX.1和XPG3的组成部分。
> 文件描述符： 对于内核而言，所有打开的文件都由文件描述符引用，文件描述符是一个*非负整数*。按照惯例，UNIX shell
使文件描述符0与进程的标准输入(STDIN_FILENO)相结合，文件描述符1与进程的标准输出(STDOUT_FILENO)相结合，文件描述符2
与进程的标准错误输出(STDERR_FILENO)相结合。

## open函数

```c
#include <sys/types.h>
#include <sys/stat.h>
#include "fcntl.h"

//返回：若成功为文件描述符，若出错为-1
int open(const char *pathname, int oflag, .../*, mode_t mode */);

//返回：若成功为只写打开的文件描述符，若出错为-1
int create(const char *pahtname, mode_t mode);


```
pathname是要打开或者创建的文件的名字。oflag参数可用来说明此函数的多个选择项。

- O_RDONLY/O_WRONLY/O_RDWR 这三个参数中同时只能指定一个
- 
- 

- read 函数
```c
#include <unistd.h>

//返回： 读到的字节数 若到文件尾为0，出错为-1
ssize_t read(int filedes, void *buff, size_t nbytes);
```

- write
```c
#include <unistd.h>

//返回：成功：已写的字节数 出错：-1
ssize_t write(int filedes, const void * buff, size_t nbytes);
```

- lseek 函数
```c
#include <sys/types.h>
#include <unistd.h>

//返回值： 成功：新的文件位移 出错：-1
off_t lseek(int filedes, off_t offset, int whence);
```

- close 函数
```c
#include <unistd.h>

/*
 * 返回值  成功：0 出错：-1
 */
int close(int filedes);
```
关闭一个文件时，也释放该进程加在该文件上的所有记录锁。
当一个进程终止时，它所有的打开文件都由内核自动关闭。


