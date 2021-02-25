---
title: hexo静态博客搭建
date: 2020-06-20 22:08:58
tags: hexo
declare: true
---

<meta name="referrer" content="no-referrer"/>

### 1.启动虚拟机：Ubuntu 16.04
#### 1.1 虚拟网络编辑器配置 
​ error:设备“VMnet0”上的网桥没有运行。该虚拟机无法与此主机或网络上的其他主机进行通

​ 参考csdn:https://blog.csdn.net/wjb123sw99/article/details/94722505

<!--more-->

​ 1.1.1显示连接成功如下图：

![](image-20200618212842515.png)

​ 1.1.2通过桥接模式连接：

![](image-20200618213005463.png)

### 2.部署hexo安装环境（需要安装Node.js和Git）
参考教程：https://hexo.io/docs/#Install-Hexo
#### 2.1NPM安装HEXO

```linux
npm install -g hexo-cli

```

2.1.1安装完成结果如下：

![](image-20200618213621665.png)

#### 2.2 初始化HEXO工作目录
```linux
hexo init <folder>

```

2.2.1 部署目录结果：

![](image-20200618215100171.png)

2.2.2 其他问题如图：

![](image-20200618215500082.png)


2.2.3 按提示解决问题结果如下图：

![](image-20200618220357089.png)


​                                  按照提示自行选择解决即可

2.2.4 查看hexo目录结构如下图：

![](image-20200618223913699.png)

文件目录有两个文件：_config.yml站点配置文件和package.json默认安装的应用程序数据

其他四个文件夹：1.node_modules下存放大量package.json文件；

​                             2.scaffolds用于存放创建的hexo的新帖子；



​                             3.source源文件夹用于放置网络博客内容的地方；



​                             4.themes用于结合站点内容构成静态博客。

### 3.启动hexo并进行相关配置

#### 3.1 启动命令：

```linux 
hexo s

```

![](image-20200618224616699.png)

#### 3.2 启动界面

![](image-20200618225017200.png)

#### 3.3 创建第一个博客

3.3.1 新建博客名称

```linux 
hexo n "XXX"

```

3.3.2 进入目录source/_post下编辑博客内容

```linux 
vim xxx.md

```

3.3.3 回到主目录清除旧的database

```linux 
hexo clean

```

清理结果如下：

![](image-20200618234257586.png)

3.3.4 产生博客

```linux 
hexo g

```

产生结果如下：

![](image-20200618234429126.png)

重启hexo结果如下：

![](image-20200618234537578.png)

至此我们就可以看见刚刚新建的博客了~

### 4.部署到Github上公开使用

#### 4.1 在Github上创建一个repository

名称格式为:用户名.github.io（必须这样命名！！！）

![](image-20200620120605403.png)

如上图所示，一个空的地址名为“用户名.github.io”的仓库创建好了~

#### 4.2 在自己的blog目录下安装git部署所需的插件

![](image-20200620120948725.png)

安装hexo-deployer-git插件的结果如上图所示

#### 4.3 配置博客目录下的_config.yml

配置参数如下：

![](image-20200620121757309.png)

需要配置type、repo和branch参数

#### 4.4 将hexo目录推送部署到远端仓库

![](image-20200620122153384.png)

博客地址建好成果如下：

![](image-20200620122805227.png)

至此就不用通过localhost:4000访问博客地址了~

### 5. 关于博客内容和主题的设置（先将内容搞起来，以后再慢慢调试自己喜欢的主题）

#### 5.1 克隆主题到主题文件夹下

![](image-20200620160956221.png)

#### 5.2 配置_config.xml的theme参数

![](image-20200620161343097.png)


#### 5.3 删除原有库产生新库后查看更新结果

![](image-20200620161547903.png)

本地查看结果：

![](image-20200620162059194.png)

#### 5.4 将风格推送到远端Github库中

![](image-20200620162412377.png)

5.4.1 也可以通过以下方式同步主题：

```linux 
cd "你的博客目录下"/themes/yilia 
git pull

```

#### 5.5 查看推送结果

![](image-20200620162639813.png)

好的，至此已完成主题的更换。接下来该去修改博客的内容和其他细节了~

修改的主目录的_config.yml配置部分如下，后期继续配置，现在先配到这里

![](image-20200620210633501.png)

![](image-20200620210655585.png)

![](image-20200620210716477.png)

![](image-20200620211817894.png)

博客网页展示如下图：

![](image-20200620215842732.png)

