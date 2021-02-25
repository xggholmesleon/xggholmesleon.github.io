---
title: hexo趟坑
date: 2020-06-21 17:50:45
tags: hexo
declare: true
---
<meta name="referrer" content="no-referrer"/>

### Q1:4000端口被占用

解决办法：_config.yml内加上如下代码更改hexo-server运行时的端口号：

<!--more-->

```linux
server:
  port: 8000 #　此处改成8000端口
    compress: true
      header: true
```

### Q2: Cannot GET/XXXX

解决办法：初始化分类子目录

如初始化分类目录：
```linux
hexo new page "categories"
```

最后会在source文件夹初始化目录并生成index文件

### Q3:FATAL duplicated mapping key at line XXX, column XXX

解决办法：注意缩进

其中官方配置说明：
hexo2.x.x 有冒号后换行的空格缩进，而hexo3.x.x 没有缩进要求

若依旧出现错误，两种办法都试下即可

### Q4: 主题详细配置－头像不显示

解决办法：主题配置文件中配置如下

![](2.JPG)

![](3.JPG)

如图，此处我的图片存放路径为themes/yilia/source/img/xxx.jpg
同理，网页导航栏logo设置也需要到对应路径下

### Q5:部署到远端的网页图片不能显示，本地也不能显示

解决办法：
1．修改主目录下的_config.yml参数

```linux
post_asset_folder: true
```

2．安装图片路径转换插件
```linux
npm install https://github.com/7ym0n/hexo-asset-image --save
```

3.安装完上述插件后，当我们创建新文章时 hexo n "xxx" ，就自动在 xxx.md 文件的同目录下创建一个同名的文件夹，我们需要将文章使用的图片放在该文件夹中

我的目录结构如下：

![](4.JPG)

４．最后，图片引用的方法
1)直接使用代码 ```![](hexo.png)```（虽然没有写文件夹的名字，但是可以的），hexo.png 是我们存在 new article 文件夹内的图片。这时你会发现markdown预览中无法显示这张图片，但是当你将博客上传到网站时，网站上是可以正常显示的;

2)使用代码 ```![](new article/hexo.png)```不仅可以本地预览，上传到网站也可以正常显示;

3)本地无法预览也是件很不舒服的事情，其实我们还可以另外创建一个文件夹 pictures ，里面专门存放所有文章的图片，代码 ![](pictures/hexo.png) 不仅可以本地预览，上传到网站也可以正常显示。

注意： 不管采取哪种办法，都要创建一个和md文件同名的文件夹，里面放上需要的图片。
如果 2和3 中代码无法实现网站上的正常显示，那就使用 1 中的代码。
因为 2和3 中代码我无法保证每个人都成功。

本文使用的方法是第一种

### References:

1.https://www.it1352.com/710717.html

2.https://www.cnblogs.com/Sroot/p/6305938.html

3.https://www.nickyam.com/tech/hexo-generate-sitemap.html

4.https://www.jianshu.com/p/3a05351a37dc

5.https://blog.csdn.net/qq_36408085/article/details/104117319

6.https://blog.csdn.net/xuezhisdc/article/details/53130383（注释参考）
