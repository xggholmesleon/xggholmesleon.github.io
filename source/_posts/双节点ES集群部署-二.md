---
title: 双节点ES集群部署(二)
date: 2020-07-03 21:02:55
tags: es
declare: true
---

### 1.启动ELASTICSEARCH集群前准备

#### 1.1 创建用户及用户组

Elasticsearch不能以root启动，因此需要添加非root用户:

<!--more-->
```linux
groupadd es
useradd es -g es
chown -R es:es ./elasticsearch-6.4.2
```
为非root用户添加登陆密码：

```linux
passwd es
```

我这里创建好后查看上菜单栏System-->Administration-->Users and Groups的结果如下：

![](2.JPG)

![](3.JPG)

开机的登录用户时可切换es用户

![](4.JPG)

#### 1.2 关闭防火墙

```linux
service iptables stop
```
以上命令适用于CentOS 6

CentOS 7 版本及以上使用命令如下：
```linux
systemctl stop firewalld
systemctl disable firewalld
```

至此，两个节点之间通信的前提条件准备好了


### 2.启动ELASTICSEARCH集群

#### 2.1 切换至es用户
```linux
su es
```

#### 2.2 在两个节点上分别启动es服务
```linux
cd bin
./elasticsearch -d # 设置后台启动
```

#### 2.3 访问浏览且查看启动效果：

节点1启动效果如下图所示：
![](5.JPG)

节点2启动效果如下图所示：
![](6.JPG)

#### 2.4命令行查看集群信息：
```linux
curl http://127.0.0.1:9200/_cat/allocation?v
```
结果如下：
![](7.JPG)

#### 2.5postman上插入数据
![](8.JPG)

curl查看数据入库结果如下图所示：
![](9.JPG)


#### Other:
查看集群信息目录命令：
![](10.JPG)

### References:
1.https://blog.csdn.net/genghaihua/article/details/81479619


