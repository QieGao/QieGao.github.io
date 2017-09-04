---
title: 'STEP BY STEP 1 : 用Github + HEXO 搭建属于你的个人博客(三)'
date: 2017-08-29 10:43:56
categories:
- 网站建设
tags:
- DNS
- domain
---
卖切糕也是要讲格调的，心动不如行动，本系列文章带你一步步搭建属于自己的高逼格个人博客。
- [ ] 万事开头易：申请Github帐号，创建Github Pages仓库
- [ ] 渐入佳境：本地搭建node.js、HEXO博客框架和博文发布、博文多地同步
- [x] 根本停不下来：Namesilo域名注册和DNSPod域名解析
- [ ] 添砖加瓦：七牛图床
<!-- more -->


通过前边两章的介绍，我们博客已经小有成型，通过在浏览器中输入 Github昵称.github.io，就能够从公网访问到我们的卖切糕博客了。
可是，为什么别人家的博客都是~~sb.me~~ qiegao.me  这么酷炫的域名呢，我们一定是建了一个假博客，不开森。

### 域名注册
想要变成真博客，那么我们需要花点毛爷爷，在域名服务商注册一个自己拥有的个性域名。
国内的域名服务商注册需要备案，如腾讯云、阿里云等等。
国外的随便弄，可以支付宝付款，记得去网上找优惠码，还可以便宜几刀，如*[Namesilo](https://www.namesilo.com/)* 、 _[GoDaddy](http://www.godaddy.com/)_。

本篇文章以如何在Namesilo注册域名为例。
打开Namesilo主页，在搜索框中输入你想要注册的个性域名。
![domain_search](http://ouvbp19aw.bkt.clouddn.com/qiegao-blog/170904/4m54aH0gGb.jpg?imageslim)

点击“search”后，我们可以在页面最上边看到部分搜索结果，点下下方的“Click Here to explore more options”，可以看到更多的域名，多选后，点击“submit”， 就可以在最上边“Domain search results”处看到刚刚勾选的域名了。
![domain_selete](http://ouvbp19aw.bkt.clouddn.com/qiegao-blog/170904/KEm8dm1aac.jpg?imageslim)

在页面最上方勾选自己中意的域名后，选择“register checked domains”, 可以设置下域名相关选项，点击“continue”注册namesilo帐号，然后按步骤付款即可。
![domain_cfg](http://ouvbp19aw.bkt.clouddn.com/qiegao-blog/170904/1a2BfFg4L8.jpg?imageslim)

### DNSPod域名解析
购买域名完成后，我们下一步需要注册域名解析商的服务。采用国外的域名解析商，比较慢，大家都懂的。所以我们这里采用国内的域名解析商_[DNSPod](https://www.dnspod.cn/)_，提供免费的域名解析服务。
进入DNSPod主页，注册帐号，进入管理控制台，选择域名解析，再选择添加域名，把刚刚购买的域名加上。
![dnspod_add_domain](http://ouvbp19aw.bkt.clouddn.com/qiegao-blog/170904/hb8CeK7KmI.jpg?imageslim)

点击添加的域名，选择添加记录，按图加上两条记录。
![dnspod_add_cname](http://ouvbp19aw.bkt.clouddn.com/qiegao-blog/170904/Ehk9fh219m.jpg?imageslim)

然后，我们需要把DNSPod的NameServer加入到Namesilo注册的域名的NameServers上。
DNSPod的NameServer地址参见上图的两个‘NS’记录类型，我们的NS地址为‘f1g1ns1.dnspod.net’和‘f1g1ns2.dnspod.net’。
登录Namesilo，在右侧选择‘My Account’ -> ‘domain manager’， 
![namesilo_homepage](http://ouvbp19aw.bkt.clouddn.com/qiegao-blog/170904/fiflIe78aK.jpg?imageslim)

再点击你的域名，在NameServers处选择‘Change’，把DNSPod的NS地址加入即可。
![namesilo_ns](http://ouvbp19aw.bkt.clouddn.com/qiegao-blog/170904/40LD1jlDGe.jpg?imageslim)
![namesilo_add_ns](http://ouvbp19aw.bkt.clouddn.com/qiegao-blog/170904/I1c2DkfL15.jpg?imageslim)

最后，我们需要在博客源文件里加上一个CNAME文件即可，进入我们的博客文件夹，在./source/ 文件夹下，新建文件‘CNAME’，不要有后缀，内容只有一行，就是刚刚注册的个性域名。然后部署到Github上就OK了。

    cd 博客文件夹
    echo '注册的域名' > ./source/CNAME
    hexo clean
    hexo g
    hexo d

打开浏览器，输入你的个性域名，ENTER，大功告成！！

本篇“STEP BY STEP 1 : 用Github + HEXO 搭建属于你的个人博客(三)”完结，来个com域名，妥妥的。

### 参考文献
1. _[国内国外注册域名的对比](http://www.williamlong.info/archives/3852.html)_
2. _[创建GitHub技术博客全攻略](http://blog.csdn.net/renfufei/article/details/37725057/)_