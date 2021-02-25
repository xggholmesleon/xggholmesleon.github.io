---
title: 双节点ES集群部署(一)
date: 2020-07-03 18:33:10
tags: es
declare: true
---

### 1.环境准备
#### 1.1本文实验准备搭建双节点Elastisearch集群，准备两台Linux CentOS 6.5(Final) 64bit虚机

节点1: 192.168.3.187
节点2: 192.168.3.179(克隆机)

<!--more-->

1.1.1 CentOS 6.5克隆机教程参考百度经验，需要配置下/etc/sysconfig/network文件，分别给两台机器修改不同的主机名，我这里是改成localhost1和localhost2

1.1.2 还要再配置下克隆机/etc/sysconfig/network-scripts/ifcfg-eth0文件，删除文件中UUID部分并设置对应的IPADDR以及GATEWAY（我这里的两个节点的BOOTPROTO均设置为static静态IP）

#### 1.2 Elasticsearch安装包准备

https://artifacts.elasticsearch.co/downloads/elasticsearch/elasticsearch-6.4.2.tar.gz
Tip1:
自己选择对应版本下载，我这里的是6.4.2版本

同时：
将安装包存放在/opt/elasticsearch下并解压

#### 1.3　CentOS 6.5 java环境准备(安装jdk1.8)

http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html
Tip2:
需要注册下载，还要填写公司地址和办公电话，暂时还没有工作的童鞋随意填下

同时：
将安装包存放在/usr/local/java下并解压，并设置/etc/profile下的环境变量
配置总共三个参数:JAVA_HOME,JRE_HOME,CLASS_PATH和PATH

最后：
别忘了刷新环境变量(有时候刷新完找不到java路径就多刷新几次)
```linux
source /etc/profile
```

检验是否安装成功：
```linux
java -version
```

我这里成功安装结果如下：
![](1.JPG)
### 2.节点配置

#### 2.1编辑安装目录下/config/elasticsearch.yml文件
节点192.168.3.187配置如下：
```liunx
cluster.name: holmes         # 集群名称，两个节点需一致
node.name: holmes-1          # 节点名称，两个节点需分别起名
network.host: 192.168.3.187  # 绑定的地址
network.bing_host: 0.0.0.0   # 设置本机可访问
discovery.zen.ping.unicast.hosts: ["192.168.3.187","192.168.3.179"] # hosts列表
```

同理
节点192.168.3.179配置如下：
```linux
cluster.name: holmes         
node.name: holmes-2          
network.host: 192.168.3.179
network.bing_host: 0.0.0.0  
discovery.zen.ping.unicast.hosts: ["192.168.3.187","192.168.3.179"]
```

### References:
1.https://jingyan.baidu.com/article/ac6a9a5e169b5d2b653eacbe.html(CentOS6.5虚拟机克隆教程)
2.https://www.cnblogs.com/wangmo/p/7880521.html
