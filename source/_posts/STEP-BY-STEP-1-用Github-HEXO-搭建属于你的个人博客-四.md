---
title: 'STEP BY STEP 1 : 用Github + HEXO 搭建属于你的个人博客(四)'
date: 2017-09-05 10:18:10
categories:
- 网站建设
tags:
- 图床
---
卖切糕也是要讲格调的，心动不如行动，本系列文章带你一步步搭建属于自己的高逼格个人博客。
- [ ] 万事开头易：申请Github帐号，创建Github Pages仓库
- [ ] 渐入佳境：本地搭建node.js、HEXO博客框架和博文发布、博文多地同步
- [ ] 根本停不下来：Namesilo域名注册和DNSPod域名解析
- [x] 添砖加瓦：七牛图床
<!-- more -->


这是本系列文章的最后一篇，将会陆续补充完善个人博客的一些细节功能。

### 七牛图床
Github提供的空间只有大约200~300M，作为图床是肯定不够的。国外的图床访问速度堪忧，因此，我们这里采用国内的_[七牛云](https://www.qiniu.com/)_作为图床服务，免费10G的空间。
按要求注册后，选择左侧对象存储，然后选择新建存储空间。
![qiniu_add_new_storage](http://ouvbp19aw.bkt.clouddn.com/qiegao-blog/170905/7hIL53aGa5.jpg?imageslim)
![qiniu_add_new_storage](http://ouvbp19aw.bkt.clouddn.com/qiegao-blog/170905/CHId7hE2lb.jpg?imageslim)

进入刚刚创建的存储对象，选择内容管理，记下外链默认域名，待会使用。
![qiniu_links](http://ouvbp19aw.bkt.clouddn.com/qiegao-blog/170905/EhJBC289K0.jpg?imageslim)

然后，点击右上角“个人面板”->“密钥管理”，选择“创建密钥”，生成AcessKey/SecretKey待会使用。
![qiniu_key](http://ouvbp19aw.bkt.clouddn.com/qiegao-blog/170905/eGk5gj1e4J.jpg?imageslim)


### MPic图床神器
我们使用_[MPic工具](http://mpic.lzhaofu.cn/)_向七牛云上传图片，并生成外链。
下载完毕后，我们选择设置帐号，输入刚刚新建的存储空间名称，AccessKey/SecretKey，域名输入前边记录下来的外链默认域名和存储空间名称，点击保存即可。
![mpic_homepage](http://ouvbp19aw.bkt.clouddn.com/qiegao-blog/170905/5md0G7E9IE.jpg?imageslim)
![mpic_setting](http://ouvbp19aw.bkt.clouddn.com/qiegao-blog/170905/24379405kI.jpg?imageslim)

需要上传图片的时候，将图片拖入到MPic，上传完成后点击复制，就可以把外链复制下来。

截图工具使用的是FSCapture。

本篇“STEP BY STEP 1 : 用Github + HEXO 搭建属于你的个人博客(四)”完结，以后想起什么再加。

### 参考文献
1. _[20分钟教你使用hexo搭建github博客](http://www.jianshu.com/p/e99ed60390a8)_
2. _[HEXO+Github,搭建属于自己的博客](http://www.jianshu.com/p/465830080ea9)_
3. _[手把手教你用Hexo+Github 搭建属于自己的博客](http://blog.csdn.net/gdutxiaoxu/article/details/53576018)_
4. _[多设备同步hexo搭建的Github博客](http://www.jianshu.com/p/6fb0b287f950)_
5. _[【干货】2个小时教你hexo博客添加评论、打赏、RSS等功能](http://www.jianshu.com/p/5973c05d7100)_