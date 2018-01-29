---
title: Ubuntu 下安装配置NFS服务
date: 2017-10-07 09:15:24
tags:
  - nfs
  - ubuntu
  - linux
categories:
  - 操作系统  
---

> NFS 是Network File System的缩写，即网络文件系统。一种使用于分散式文件系统的协定，由Sun公司开发，于1984年向外公布。功能是通过网络让不同的机器、不同的操作系统能够彼此分享个别的数据，让应用程序在客户端通过网络访问位于服务器磁盘中的数据，是在类Unix系统间实现磁盘文件共享的一种方法。   
NFS 的基本原则是“容许不同的客户端及服务端通过一组RPC分享相同的文件系统”，它是独立于操作系统，容许不同硬件及操作系统的系统共同进行文件的分享。

<!--more-->

## 安装nfs

```bash
$ sudo apt-get install nfs-kernel-server
```

## 配置nfs

修改/etc/exports里的内容，在文件最后加入nfs文件夹的路径及权限。   

```bash
$ /work/nfs_root/first_nfs  *(rw,sync,no_root_squash)
```

`*`：允许所有的网段访问，也可以使用具体的IP  
`rw`：挂接此目录的客户端对该共享目录具有读写权限  
`sync`：资料同步写入内存和硬盘  
`no_root_squash`：root用户具有对根目录的完全管理访问权限

## 启动nfs

```
$ sudo /etc/init.d/nfs-kernel-server start
```

## 停止nfs

```
$ sudo /etc/init.d/nfs-kernel-server stop
```
