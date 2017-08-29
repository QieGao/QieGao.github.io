---
title: 'STEP BY STEP 1 : 用Github + HEXO 搭建属于你的个人博客(二)'
date: 2017-08-28 14:26:54
categories:
- 网站建设
tags:
- hexo
- github
---
卖切糕也是要讲格调的，心动不如行动，本系列文章带你一步步搭建属于自己的高逼格个人博客。
- [ ] 万事开头易：申请Github帐号，创建Github Pages仓库
- [x] 渐入佳境：本地搭建node.js、HEXO博客框架和博文发布、博文多地同步
- [ ] 根本停不下来：Namesilo域名注册和DNSPod域名解析
- [ ] 添砖加瓦：七牛图床
<!-- more -->

### 本地安装node.js
进入_[node.js中文官网 http://nodejs.cn/](http://nodejs.cn/)_，按需下载并安装即可。


### 本地安装HEXO
HEXO是一个高效静态站点生成框架，详见_[官网 https://hexo.io/zh-cn/](https://hexo.io/zh-cn/)_，可以方便的使用markdown语法生成博客文章。
我们使用node.js的包管理工具npm来安装HEXO。

    #创建博客文件夹
    mkdir 博客文件夹 

    #进入该文件夹
    cd 博客文件夹 

    #安装部署HEXO
    npm install hexo-cli -g
    
    #由于默认npm镜像源比较慢，切换到国内源
    #1.临时修改
    npm --registry https://registry.npm.taobao.org install hexo-cli -g
    
    #2.持久修改及校验
    npm config set registry https://registry.npm.taobao.org
    npm config get registry


HEXO安装完成后，在终端输入

    $ hexo
    Usage: hexo <command>

    Commands:
        clean     Remove generated files and cache.
        config    Get or set configurations.
        deploy    Deploy your website.
        generate  Generate static files.
        help      Get help on a command.
        init      Create a new Hexo folder.
        list      List the information of the site
        migrate   Migrate your site from other system to Hexo.
        new       Create a new post.
        publish   Moves a draft post from _drafts to _posts folder.
        render    Render files with renderer plugins.
        server    Start the server.
        version   Display version information.

    Global Options:
        --config  Specify config file instead of using _config.yml
        --cwd     Specify the CWD
        --debug   Display all verbose messages in the terminal
        --draft   Display draft posts
        --safe    Disable all plugins and scripts
        --silent  Hide output on console

    For more help, you can use 'hexo help [command]' for the detailed information
    or you can check the docs: http://hexo.io/docs/


显示上述内容，说明HEXO安装成功。


### 博客初始化
HEXO安装完成后，在博客文件夹中初始化博客

    cd 博客文件夹
    hexo init
    npm install

初始化完成后，博客文件夹目录结构如下

    $ ls -l 
        _config.yml #博客配置文件
        db.json
        node_modules/
        package.json
        public/ #生成的静态博文页面
        scaffolds/
        source/ #博文存放目录
        themes/ #博客主题存放目录

具体的\_config.yml各个字段含义，可以参见_[这里](https://hexo.io/zh-cn/docs/configuration.html)_。现在，我们需要手动配置部署到Github的参数，打开_config.yml，在末尾添加如下内容

    # Deployment
    ## Docs： https://hexo.io/docs/deployment.html
    deploy:
        type: git
        repo: https://github.com/Github昵称/Github昵称.github.io.git
        branch: master


### 博客测试
上述步骤完成后，是时候来看看我们的博客长什么样了。
我们需要使用到下边几个hexo命令
    
    # Remove generated files and cache.
    hexo clean 

    #Generate static files.
    hexo generate | hexo g

    # Deploy your website.
    hexo deploy | hexo d

    # Start the server.
    hexo server | hexo s


本地测试，运行

    hexo clean
    hexo g
    hexo s

启动服务器后，打开浏览器，输入localhost:4000，走你。如果没有意外的话，恭喜你，你的第一个博客已经展现在你的眼前。

本地测试OK后，下一步需要把博客关联到Github上。

    #部署页面至github
    hexo clean
    hexo g
    hexo d

    # 报错ERROR Deployer not found: git
    # ERROR Deployer not found: github
    npm install hexo-deployer-git --save

部署完成后，在浏览器中输入github昵称.github.io，就可以在公网上访问我们的博客了。


### 博客主题修改
HEXO主题非常多，可以去HEXO官网上查看，也可以_[看这里](https://github.com/hexojs/hexo/wiki/Themes)_，不同的主题有不同的配置。
当前博客选择的主题是_[NexT](http://theme-next.iissnan.com/)_。NexT主体集成了许多第三方服务，比如评论系统、数据统计与分析、内容分享服务、搜索服务等等，只需要按要求把相关配置加入到主题配置文件中即可，具体安装使用参见NexT官网说明。


### 发布你的第一篇博文
我们的博客骨架已经基本成型了，现在该加点肉肉上去了。
在终端输入

    #新建一篇文章
    hexo new "文章标题"

在./博客文件夹/source/_post/文件夹下，可以看到刚刚创建的markdown文件。用markdown编辑器打开、编辑、保存后，我们依旧先在本地测试下效果，运行

    hexo s

在浏览器中，输入localhost:4000，就可以看到发布的文章了。
本地测试完毕后，我们需要把博文发布到github上，这样其他人才能看到博客内容，运行

    hexo g
    hexo d

完成后，试试在浏览器中输入github昵称.github.io。
如果什么都没有发生，不要着急，请暂时Hold住你的“~~wocao~~什么情况”，经个人测试一般因为缓存的原因，新博文或者修改博文会有一点点延迟才会生效。


### 博文多地同步
当我们在自己的电脑上完成了HEXO的搭建后，突然想在其他电脑上也同步博客内容，怎么办呢？我们可以利用Github创建一个分支来管理博客源文件。
打开博客所在的Github Pages仓库，https://github.com/Github昵称/Github昵称.github.io ，点击Branch，默认只有master分支，输入分支名称，点击Create branch。
因为我已经创建过分支hexo，所以这里用hexo-src作为展示，分支名称自己明白就好。
![mark](http://ouvbp19aw.bkt.clouddn.com/qiegao-blog/170829/JB0bc38cGf.jpg?imageslim)
分支创建完成后，设置默认分支为刚刚创建的分支名称。
![mark](http://ouvbp19aw.bkt.clouddn.com/qiegao-blog/170829/7e4HDC0IjG.jpg?imageslim)
接着，我们需要把博客源文件全部同步到我们刚刚创建的分支里边。运行

    #进入博客文件夹
    cd 博客文件夹

    #git初始化
    git init

    #添加远程仓库地址，即是Github的仓库地址
    git remote add origin https://github.com/Github昵称/Github昵称.github.io

    #添加所有本地文件到git
    git add .

    #git提交
    git commit -m "提交内容说明"

    #推送更改内容到远程仓库的hexo分支
    #完整写法
    git push origin master:hexo
    #简单写法
    git push

同步完成后，我们在另外一台电脑上使用git命令，下载Github新建分支上的文件

    #克隆文件到本地
    git clone -b 分支名 https://github.com/Github昵称/Github昵称.github.io

同样，我们需要在这台电脑上安装node.js、HEXO和依赖库

    #安装HEXO
    npm install hexo

    #这里不需要运行hexo初始化，hexo init，否则配置参数会重置

    #安装依赖库
    npm install

    #git部署相关
    npm install hexo-deployer-git

我们现在每次换电脑写博文，只需要多几个操作。

    #从远程仓库更新最新的内容
    git pull

    #生成、发布博文
    hexo new "博文名称"
    hexo clean
    hexo g
    hexo d

    #同步新博文到Github分支
    git add .
    git commit -m '提交内容说明'
    git push

本篇“STEP BY STEP 1 : 用Github + HEXO 搭建属于你的个人博客(二)”完结，内容较多，慢慢来。不熟悉Git命令的可以参考后边的参考文献。


### 参考文献
1. _[20分钟教你使用hexo搭建github博客](http://www.jianshu.com/p/e99ed60390a8)_
2. _[HEXO+Github,搭建属于自己的博客](http://www.jianshu.com/p/465830080ea9)_
3. _[手把手教你用Hexo+Github 搭建属于自己的博客](http://blog.csdn.net/gdutxiaoxu/article/details/53576018)_
4. _[多设备同步hexo搭建的Github博客](http://www.jianshu.com/p/6fb0b287f950)_
5. _[【干货】2个小时教你hexo博客添加评论、打赏、RSS等功能](http://www.jianshu.com/p/5973c05d7100)_
6. _[Git教程](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)_