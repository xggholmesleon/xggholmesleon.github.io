---
title: 双节点ES集群部署(三)
date: 2020-07-03 21:56:29
tags: es
declare: true
---

### 1.Elasticsearch插件安装－实现更多功能

#### 1.1IK分词器插件安装

Tip1:IK分词器版本与ES版本保持一致

版本对应关系可查阅网址：http://github.com/medcl/elasticsearch-analysis-ik/releases

<!--more-->
1.1.1下载插件：
```linux
wget https://github.com/medcl/elasticsearch-analysis-ik/releases/downloads/v6.4.2/elasticsearch-analysis-ik-6.4.2.zip
```

1.1.2解压至目录elasticsearch-6.4.2/plugins/elasticsearch-analysis-ik-6.4.2

1.1.3重启es查看插件放置结果如下图所示：

![](11.JPG)


#### 1.2elasticsearch-head可视化插件安装

```linux
git clone git://github.com/mobz/elasticsearch-head.git
cd elasticsearch-head
npm install
npm run start
```

Tip2:没有git和npm指令的安装下
PS:我的CentOS 6.5(final)上原先就没有这两个，都是后安装的

1.2.1配置elasticsearch/config目录下的elasticsearch.yml
在文件末尾添加代码如下图所示：
![](14.JPG)

在elasticsearch-head目录下启动npm：
![](12.JPG)

启动结果如下：
![](13.JPG)

### References:
1.https://www.cnblogs.com/jinfanfu/p/12468858.html(CentOS安装node)
2.https://www.cnblogs.com/lcword/p/5917295.html(Linux的BOOTPROTO动态静态IP设置)
3.https://www.jianshu.com/p/04f4d7b4a1d3
