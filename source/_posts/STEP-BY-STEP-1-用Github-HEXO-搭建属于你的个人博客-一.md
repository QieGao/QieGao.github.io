---
title: 'STEP BY STEP 1 : 用Github + HEXO 搭建属于你的个人博客(一)'
date: 2017-08-28 10:30:52
categories: 
- 网站建设
tags:
- github
---
卖切糕也是要讲格调的，心动不如行动，本系列文章带你一步步搭建属于自己的高逼格个人博客。
- [x] 万事开头易：申请Github帐号，创建Github Pages仓库
- [ ] 渐入佳境：本地搭建node.js、HEXO博客框架和博文发布、博文多地同步
- [ ] 根本停不下来：Namesilo域名注册和DNSPod域名解析
- [ ] 添砖加瓦：七牛图床
<!-- more -->

### 申请Github帐号
没有Github帐号怎么卖切糕？来嘛，_[点一下 https://github.com/](https://github.com/)_。剩下的，分分钟搞定。

### 创建Github Pages repository
登录Github后，在页面右上方选择New repository来创建仓库。
![1.1.1.New_repository](http://ouvbp19aw.bkt.clouddn.com/qiegao-blog/170828/2D4hGF6I0a.jpg?imageslim)


在Repository name处输入**Github昵称.github.io**，然后点击Create repository即可。
![1.1.2.Create_new_repository](http://ouvbp19aw.bkt.clouddn.com/qiegao-blog/170828/Je9d7Jh2bm.jpg?imageslim)


### 配置Git环境
Windows下可以考虑直接安装_[Github Desktop https://desktop.github.com/](https://desktop.github.com/)_。
Linux下安装_[Git https://git-scm.com/downloads](https://git-scm.com/downloads)_即可。


### 生成、添加SSH KEY
添加SSH KEY后，每次在本地通过git命令操作github就不需要输入帐号密码了。 
**注意保护生成的SSH KEY，特别是在公共计算机中。**

在Shell中运行
    
    ssh-keygen -t rsa -C 'github注册邮箱'

默认Enter完毕以后，会得到id\_rsa和id\_rsa.pub两个文件，把id\_rsa.pub文件的内容，全部复制，粘贴到_[这里 https://github.com/settings/keys](https://github.com/settings/keys)_。
也可以点击右上角头像，选择Settings->SSH and GPG keys。
![mark](http://ouvbp19aw.bkt.clouddn.com/qiegao-blog/170828/aHaED2D8F1.jpg?imageslim)


本篇“STEP BY STEP 1 : 用Github + HEXO 搭建属于你的个人博客(一)”完结，肿么样，si不si很easy啊。

### 参考文献
请参阅本系列文章最后一篇的内容。