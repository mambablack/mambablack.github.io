---
layout: post
title: Docker学习笔记
category: Docker
date: 2016-02-24
duoshuo: false

---

# Docker学习笔记

## 大纲

* [Docker是什么](#c1)
* [中文文档](#c2)
* [Docker优点](#c3)
* [Docker生态系统](#c4)
* [Docker命令总结](#c5)
* [学习点滴](#c6)
* [实战](#c7)

<!-- more -->

<h2 id="c1">Docker是什么</h2>

1. 容器就是轻量的VM
2. Docker是轻量的容器



<h2 id="c2">中文文档</h2>
https://github.com/widuu/chinese_docker/blob/master/userguide/usingdocker.md

http://dockerpool.com/static/books/docker_practice/index.html

http://dockerpool.com/

https://yeasy.gitbooks.io/docker_practice/content/


<h2 id='c3'>Docker优点</h2>

1. Docker 对资源的利用率极高
2. 轻量级
3. 方便构建、发布

<h2 id='c4'>Docker生态系统</h2>

1. Supervisor

   负责对 Docker 集群进行管理
   	
2. CoreOS

	云化Linux

3. Docker Machine

	负责在多种平台上快速安装 Docker 环境

4. Docker Compose(Fit)

	负责快速在集群中部署分布式应用

5. swarm

<h2 id="c5">Docker命令总结</h2>


```

docker images

```

列出当前镜像信息

---

```
docker run --help

```

-d 后台运行

-i input

-t 终端

-p 端口

-v 挂载

---

```
docker ps
```
当前运行的container

---

```
docker stats containerId
```
显示containerId的container的运行情况

---

```
dip
```
container 的ip

---

```
dpid
```
container 的pid

---

```
denter
```
进入container

---

```
以上三个命令需要安装

$ wget -P ~ https://github.com/joshhu/docker/raw/master/docker_scripts/.bashrc_docker;
$ echo "[ -f ~/.bashrc_docker ] && . ~/.bashrc_docker" >> ~/.bashrc; source ~/.bashrc
$ exit

```
```
docker history imageName
显示image的layer历史，可以用来回滚
```
	  

```

docker build
按照Dockerfile的定义构建镜像

docker build -t test/supervisord .

```
-t : 虚拟终端

test/supervisord :镜像名

. : Dockerfile目录   

---
```
docker pull registry.hub.docker.com/ubuntu:12.04

```
从注册服务器 registry.hub.docker.com 中的 ubuntu 仓库来下载标记为 12.04 的镜像

---
	
```
sudo docker run -t -i ubuntu:14.04 /bin/bash
```

如果不指定具体的标记，则默认使用 latest 标记信息。

---

```
sudo docker export 7691a814370e > ubuntu.tar
```
导出image到本地

---
```
cat ubuntu.tar | sudo docker import - test/buntu:v1.0
```

此外，也可以通过指定 URL 或者某个目录来导入，例如


```
docker import http://example.com/exampleimage.tgz example/imagerepo

```
    


<h2 id='c6'>学习点滴</h2>

1. docker 的镜像(image)是只读的，每次都会新建一个镜像

2. container是Docker的容器，是image的实例

<h2 id='c7'>实战</h2>

### 目标

1. 利用Docker Machine在多平台上安装Docker环境

2. Fig (Docker compose)隔离开发环境

3. 搭建基于coreos的tomcat集群

4. 利用nginx负载均衡

5. 利用Docker swarm 管理集群

6. 利用Supervisor管理进程

7. etcd 管理配置信息和服务发现

8. OpenStack


