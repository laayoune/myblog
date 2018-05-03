---
title: hexo+七牛云命令工具存储图片
date: 2018-04-28
categories: 其他技术
tags: Hexo
keywords: Hexo,七牛云,图片存储
copyright: true
description:
---

##加入图片的几种方式

1. Hexo文章中的图片，可以放在本地，然后和静态文件一起发布（部署）到你的空间。将图片放在source/images目录下，然后直接引入
比较麻烦，也占用资源，想到后期图片增多的加载速度问题，果断放弃

2. 使用各种图床，如：[贴图库](https://www.tietuku.com/),注册个用户,直接上传图片
不是很稳定,而且每次都要打开web，然后上传，我是个懒人~~~~

3. 使用七牛云的命令行工具
* 首先下载工具：[点击这里](https://developer.qiniu.com/kodo/tools/1302/qshell)
该工具由于是命令行工具，所以只需要从上面的下载链接下载后即可执行使用（建议重命名为qshell）。
但每次都要找到目录打开这个命令行工具有木有很麻烦!~那么配置全局使用吧

* 增加环境变量，以mac为例，mac系统的环境变量文件有几个，我因为是全局公用的,所以我选择使用~/.bashrc文件
    --打开cmd命令行,输入
```
vim ~/.bashrc
```
进入编辑模式,增加
```shell
export PATH=$PATH:刚才下载的七牛命令行工具的位置
```
如果文件中以前有path环境变量,直接  :位置加后面就可以了
保存
然后执行
```shell
$ source ~/.bashrc
```
验证一下
```shell
$ qshell -v
```
如果成功会显示版本号

设置密钥,ak和sk登录七牛云个人中心->密钥管理中查看
```
$ qshell account ak sk
```
**安装完成，开始使用**
上传图片有几种
1. 上传100MB以下的小文件
```
$ qshell fput <Bucket> <Key> <LocalFile> [Overwrite] [MimeType] [UpHost] [FileType]
```
| 参数名称 | 描述 | 默认 |
|:-|:-|:-:|
|Bucket|七牛空间名称|N|
|Key|文件保存在七牛空间的名称|N|
|LocalFile|本地文件的路径|N|
|Overwrite|可选,是否覆盖空间已有文件，默认为false|Y|
|MimeType|可选,指定文件的MimeType|Y|
|UpHost|可选,上传入口地址|Y|
|FileType|可选,文件存储类型，0(标准存储）1(低频存储)|0|
如:
![](https://p7vioebko.bkt.clouddn.com/2.png)
上传后,在你的md文件中直接引入就OK了
```
![](https://p7vioebko.bkt.clouddn.com/a.jpg)
```
前面是七牛外联域名:
![](https://p7vioebko.bkt.clouddn.com/1.png)
2. 上传文件大小较大的文件
```
$ qshell rput <Bucket> <Key> <LocalFile> [Overwrite] [MimeType] [UpHost] [FileType]
```

3. 将本地目录中的文件同步到七牛空间
```
$ qshell qupload [<ThreadCount>] <LocalUploadConfig>
```
qupload需要本地配置文件的支持,详情请看:[点击这里](https://github.com/qiniu/qshell/blob/master/docs/qupload.md)

4. 从互联网上抓取一个资源并保存到七牛的空间中
```
$ qshell fetch <RemoteResourceUrl> <Bucket> [<Key>]
```
|参数名|描述|可选参数|
|:-|:-|:-:|
|RemoteResourceUrl|互联网上资源的链接|
|Bucket|空间名称|N|
|Key|该资源保存在空间中的名字，如果不指定这个名字，那么会使用抓取的资源的内容hash值来作为文件名|Y|

适合大文件的:
```
$ qshell sync <SrcResUrl> <Bucket> <Key> [<UpHostIp>]
```
5. 查询文件信息
```
$ qshell stat <Bucket> <Key>
```
|参数名|描述|
|:-|:-|
|Bucket|空间名称|
|Key|空间中的文件名|

6. 删除文件
```
$ qshell delete <Bucket> <Key>
```
现在再上传图片就很简单了,再也不用本地找个地方保存图片，也不用每次都开web了：）
想了解更多的，可以参考官方文档：[官方文档](https://developer.qiniu.com/kodo/tools/1302/qshell)

