---
title: C指针与const限定符
date: 2017-10-07 10:45:54
tags:
  - C/C++
  - Pointer
  - const
categories:
  - 编程语言   
---

> 指针在C语言里是精髓所在，也是C语言最吸引人的地方，它可以直接操作内存，在编写程序的过程中有着极大的发挥空间。有人也把指针说成是C语言的灵魂，用好指针是对C语言理解的一个质变。

<!--more-->

## 指向`const int`型的指针

```c
const int *a;   
int const *a;  //a的类型为不带const限定的int*，指向一个带const限
               //定的变量。
```

`a`所指向的内存单元是`const int`型，不可改写，所以`(*a)++`是不允许的，但`a`是可以改写的，所以`a++`是允许的。

## 指向`int`型的`const`指针
```c
int * const a;   //a的类型为带const限定l的int*型。指向一个
                 //不带const限定的int型变量。
```

`a`是一个指向`int`型的`const`指针，`*a`是可以改写的，但`a`不允许改写。

## 指向`const int`型的`const`指针

```c
int const * const a;    //a的类型为带const限定的int*型，指向一
                        //个带const 限定的int型变量
```

`a`是一个指向`const int`型的`const`指针，因此，`*a`和`a`都不允许改写。

## 指向字符串的指针

```c
//字符串字面值类似于数组名，做右值使用时自动转换成指向首元素的指针。
const char *p = "abcd";   //如果要定义一个指针指向字符串字面值，
                          //这个指针应该是const char *型。
const char strl[5] = "abcd";
char str2[5] = "abcd";
printf("%s", p);    //printf函数原型为int printf(const char *format,...)
printf(str1);
printf(str2);
printf("abcd");
```

## `const`限定符的使用

分清楚这三种情况，并灵活运用可以让你的程序更加的健壮，我们应该尽可能多的使用`const`限定符。

> 指向`const`变量的指针可以隐式转换成指向非const变量的指针

指向非`const`变量的指针可以传给指向`const`变量的指针，编译器可以做隐式类型转换。

```c
char a = 'a';
char *pa = &a;
const char *pt = pa;

//指向const变量的指针或者const变量的地址不可以传给指向非const变量
//的指针，以免通过后者意外改写了前者所指向的内存单元，例如对下面的
//代码编译器会报警告
const char c = 'c';
const char *pc = &c;
char *pt = pc;
```
