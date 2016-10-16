---
title: 008-用Github与Hexo搭建免费博客
date: 2016-10-12 23:24:00
tags: 技术
---
这是一篇纯技术文，非战斗人员请撤离；这篇涉及到电脑操作，请在电脑陪同下阅读。

## 引言
在改用Markdown语言写作之后，Github顺势就成了我的文档保存柜，其好处很明显，免费的存储空间以及文档改动的存档功能，特别是后一条，我通常写出一篇初稿后上传一遍，过一天之后再修改再上传，如果以后有了想法，不仅能看到最新的修改版，还能看到文档一步步的修改过程，我觉得挺好。后来再想，反正也要用Github保存，如果保存的文档能顺势再进化一下，变成博客，让别人也能查看，那就太幸福了。没成想还真有搭建免费静态博客的方法，于是就有了这篇教程。其实网上的教程很多，我写下来的目的也主要是为了留备以后自己查用，因此此文有大量摘用，且只针对windows平台和Hexo 3.x。

## 准备工作
了解Hexo
>A fast, simple & powerful blog framework

Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用 Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。[hexo.io](http://hexo.io/)

安装GIT并注册相应帐号，用来同步以及Git Shell

[GitHub Windows](https://windows.github.com/)

安装Node.JS

[Node.JS](http://nodejs.org/)

注意 安装完成后在系统环境变量中添加Path环境变量，使npm命令生效。

    ;C:\Program Files\nodejs\node_modules\npm

安装Hexo

配置好GitHub主目录后，双击桌面上的Git Shell，输入npm命令即可安装

    npm install hexo-cli -g
    npm install hexo --save

    #如果命令无法运行，可以尝试更换taobao的npm源
    npm install -g cnpm --registry=https://registry.npm.taobao.org

## Hexo初始化配置
### 创建Hexo文件夹

安装完成后，根据自己喜好建立管理博客相关文件的目录（如E:\Doc\GitHub\Hexo），进入Git Shell并切换到该路径下E:\Doc\GitHub\Hexo执行以下指令

    hexo init
    npm install

    #初始化完成后，指定文件夹下面应该有如下目录：
    .
    ├── _config.yml
    ├── package.json
    ├── scaffolds
    ├── scripts
    ├── source
    |      ├── _drafts
    |      └── _posts
    └── themes__

### 安装Hexo插件(非必要步骤)

    npm install hexo-generator-index --save
    npm install hexo-generator-archive --save
    npm install hexo-generator-category --save
    npm install hexo-generator-tag --save
    npm install hexo-server --save
    npm install hexo-deployer-git --save
    npm install hexo-deployer-heroku --save
    npm install hexo-deployer-rsync --save
    npm install hexo-deployer-openshift --save
    npm install hexo-renderer-marked@0.2 --save
    npm install hexo-renderer-stylus@0.2 --save
    npm install hexo-generator-feed@1 --save
    npm install hexo-generator-sitemap@1 --save

继续执行以下命令：

    hexo g
    hexo s

成功后可登录http://localhost:4000 查看本地效果

### Hexo简写命令
    hexo n # new, 生成文章，或者source\_posts手动编辑
    hexo s # server, 本地发布预览效果
    hexo g # generate, 生成public静态文件
    hexo d # deploy, 同步更新至Github


## 部署静态网页到GitHub Page上
### 设置GitHub
1. 登录GitHub，在主页右下角创建New repository，name必须和用户名一致如wang_yuany.github.io
2. 配置_config.yml文件


    deploy:
      type: git
      repository: git@github.com:wang_yuany/wang_yuany.github.com.git
      branch: master

运行Git Shell切换到如E:\Doc\GitHub\hexo路径下，执行下列命令，即可将数据同步到Github

    hexo d -g

最后访问主页观察效果，首次创建耐心等待10分钟左右审核，之后即可访问静态主页如 http://wang_yuany.github.io


## 写文章
Hexo发布的.md源文件在 ./source/_posts 下面，我一般倾向于写完之后加一个文件头，用于生成网页时引用。也可以输入下列命令生成指定名称的文档：

    hexo new [layout] "postName" #新建文章



## Hexo主题
Hexo的[(主题列表)](https://github.com/hexojs/hexo/wiki/Themes)

推荐NexT主题，因为它有比较明白的中文[说明文档](http://theme-next.iissnan.com/getting-started.html)

### 下载和和使用
在博客主目录（如E:\Doc\GitHub\hexo）下输入命令行

    $ git clone https://github.com/iissnan/hexo-theme-next themes/next #主题的地址

修改全局站点文件_config.yml 中的内容

    themes: next #主题文件夹名


## 扩展阅读
Hexo Docs - http://hexo.io/docs/

HelloDog Index - http://wsgzao.github.io/index/#Hexo

[使用GitHub和Hexo搭建免费静态Blog](https://wsgzao.github.io/post/hexo-guide/)

[使用hexo+github搭建静态博客](http://qiutc.me/post/%E4%BD%BF%E7%94%A8hexo-github%E6%90%AD%E5%BB%BA%E9%9D%99%E6%80%81%E5%8D%9A%E5%AE%A2.html)

[搭建 Hexo + Github 博客](http://jianghao.wang/2015/hexo-github/)

如果喜欢我的文章，请关注我的公众号。
![公众号](http://bdbea3.duapp.com/pcs_download.php?id=3172&link=%2Fapps%2Fhgf_blog%2F%E5%85%AC%E4%BC%97%E5%8F%B7logo.jpg)
