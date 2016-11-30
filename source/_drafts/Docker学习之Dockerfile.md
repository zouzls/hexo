---
title: Docker学习之Dockerfile
tags:
  - docker
  - 构建镜像
  - Dockerfile
categories: Docker
date: 2016-07-30 11:07:25
---

好记性不如烂笔头，docker看到一大半，发现本想略过「Dockerfile」指令这部分，但是看到最后发现不行，在构建应用服务和持续集成等之中第一步就是Dockerfile，Dockerfile是基于DSL语法（我也不太懂）的指令来构建一个镜像，然后通过docker build命令基于该指令就可以构建一个新的镜像，摘录常用指令如下：
<!--more-->
#### FROM
每个Dockerfile的第一条指令必须是FROM。该指令指定一个已经存在的镜像名称，后续所有操作都基于该镜像进行，这个镜像被称为基础镜像（base image）。示例如下：
```
FROM ubuntu:14.04
```
#### MAINTAINER
指定镜像的作者和联系方式，如下：
```
MAINTAINER gs chen "zouzls@foxmail.com"
```
#### RUN
表示构建镜像要运行的命令，比如在之前的镜像基础上安装一些软件，如下是完成apt-get的更新和安装nginx服务器（尤其要注意和接下来的CMD命令进行区别开来）：
```
RUN apt-get update && apt-get install -y nginx
```

