---
layout: post
title: "ubuntu下修改apt源问题(无法解析域名)"
date: 2023-03-16
description: "介绍Linux的ubuntu下修改apt源问题(无法解析域名)"
tag: Linux
---
apt修改为阿里源， `sudo vim /etc/apt/sources.list`之后出现问题:


```console
W: 无法下载 http://mirrors.aliyun.com/ubuntu/dists/jammy/InRelease  暂时不能解析域名“mirrors.aliyun.com”
W: 无法下载 http://mirrors.aliyun.com/ubuntu/dists/jammy-security/InRelease  暂时不能解析域名“mirrors.aliyun.com”
W: 无法下载 http://mirrors.aliyun.com/ubuntu/dists/jammy-updates/InRelease  暂时不能解析域名“mirrors.aliyun.com”
W: 无法下载 http://mirrors.aliyun.com/ubuntu/dists/jammy-proposed/InRelease  暂时不能解析域名“mirrors.aliyun.com”
W: 无法下载 http://mirrors.aliyun.com/ubuntu/dists/jammy-backports/InRelease  暂时不能解析域名“mirrors.aliyun.com”
W: 无法下载 https://ppa.launchpadcontent.net/deadsnakes/ppa/ubuntu/dists/jammy/InRelease  暂时不能解析域名“ppa.launchpadcontent.net”
W: 部分索引文件下载失败。如果忽略它们，那将转而使用旧的索引文件。

```


## 原因

DNS没有配置好

## 解决

```sh
sudo  vim /etc/resolv.conf
# 或
sudo vim /run/systemd/resolve/stub-resolv.conf # 建议改这个
```

添加nameserver,如下：(使用阿里巴巴提供的DNS域名解析服务)

```sh
# 添加
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN

nameserver 223.5.5.5
nameserver 223.6.6.6
```
