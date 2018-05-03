---
title: hexo next主题第三方配置 评论 统计等
date: 2018-04-28
categories: 其他技术
tags: [Hexo,next]
keywords: Hexo,next,博客,评论,统计
copyright: true
description:
---
<!-- more -->
之前的文章讲了next的一般的配置，这次在说下next的第三方配置，比如评论、统计等

## 评论
在多说和网易云跟帖相继倒闭，
DISQUS、Facebook Comments、HyperComments不符合国情
来必力打开超慢的情况下，选择了 [Valine](https://valine.js.org/)

这个评论系统是基于LeanCloud的，大家应该对这个很熟悉，对，Hexo的博客阅读量统计也是它。官网网址如下，需要注册一个账户。
[LeanCloud官网](https://leancloud.cn/)

注册后进入控制台后点击左下角创建应用：
![创建应用](https://p7vioebko.bkt.clouddn.com/3.jpg)

应用创建好以后，进入刚刚创建的应用，选择左下角的设置>应用Key，然后就能看到你的appid和appkey了：
![](https://p7vioebko.bkt.clouddn.com/4.jpg)

为了数据安全，请注意设置自己的安全域名：
![](https://p7vioebko.bkt.clouddn.com/5.jpg)

配置 **主题配置文件**
![](https://p7vioebko.bkt.clouddn.com/6.png)
修改appid和appkey

如果需要邮件提箱把notify设置为true
具体的设置可以看[评论系统中的邮件提醒设置](https://github.com/xCss/Valine/wiki/Valine-%E8%AF%84%E8%AE%BA%E7%B3%BB%E7%BB%9F%E4%B8%AD%E7%9A%84%E9%82%AE%E4%BB%B6%E6%8F%90%E9%86%92%E8%AE%BE%E7%BD%AE)

## 数据统计和分析
常用的数据分析next主题都是支持的

百度统计
登录 [百度统计](https://tongji.baidu.com/web/25528541/welcome/login)，定位到站点的代码获取页面

新建站点

1. 百度提供的统计代码:
复制 hm.js? 后面那串统计脚本 id，如下图所示：
![创建应用](https://p7vioebko.bkt.clouddn.com/7.jpg)

编辑 **主题配置文件**， 修改字段 baidu_analytics，值设置成你的百度统计脚本 id。

2. CNZZ 统计
在 主题配置文件 中增加了一项 cnzz_siteid的配置项，值为 CNZZ 里面添加统计的站点ID。

3. 内容分享
百度分享
编辑 主题配置文件，添加/修改字段 baidushare，值为 true。

4. 站内搜索
安装 hexo-generator-searchdb，在站点的根目录下执行以下命令
```shell
$ npm install hexo-generator-searchdb --save
```