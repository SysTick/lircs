---
title: 在ubuntu系统下配置shadowsocks
date: 2017-10-08 11:17:44
tags:
  - ss
  - Ubuntu
categories:
  - linux
---

![shadowsocks](/images/article/ss.png)

> 建议安装pytyon版本的shadowsocks。可以参照本文来配置，也可以使用文末参考中的自动安装脚本安装。

<!--more-->

## 配置环境

本文所用的配置环境如下：

```bash
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:        16.04
Codename:       xenial
```

## 安装及配置步骤

安装及配置分为3步。

### 安装

```bash
$ sudo apt-get install python-gevent python-pip
$ sudo pip install shadowsocks
```

### 创建配置文件

在/etc目录下创建shadowsocks.json配置文件

```bash
vim /etc/shadowsocks.json
```

单用户配置文件
```json
{
  "server":"0.0.0.0",
  "server_port":9696,
  "password":"客户端登录密码",
  "timeout":600,
  "method":"aes-256-cfb"
}
```

多用户配置文件
```json
{
  "server":"0.0.0.0",
  "password":{
    "9696":"设定9696端口密码",
    "9898":"设定9898端口密码",
  },
  "timeout":600,
  "method":"aes-256-cfb"
}
```

### 启动
```bash
$ ssserver -c /etc/shadowsocks.json -d start
```

### 查看相应的端口的监听状态

![netstat -lnp](/images/article/netstat -lnp.png)

至此，不出意外的话，我们已经可以使用shadowsocks了。

## 总结

1. 配置完以后如果还是不能使用，尝试本地ping包，确认服务器ip是否被限制(*呃，一开始我就被进了这个坑了*)。

## 相关请参考
- [VPS+SS搭建自己的VPN](http://blog.csdn.net/creasylai19/article/details/52268995)    
- [Ubuntu下shadowsocks 安装与配置（server and client）](https://my.oschina.net/lieefu/blog/500774)  
- [Shadowsocks Python版一键安装脚本](https://teddysun.com/342.html/comment-page-23)  

------------------------------------
