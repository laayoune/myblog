---
title: hexo+github搭建个人博客
categories: 其他技术
tags: Hexo
date: 2018-04-26
keywords: Hexo,博客
description:
---

## 1. 安装git和nodeJs
在搭建Hexo之前需要先安装git和nodeJs，直接去官方下载最新版本按照提示安装就好，就不再重复叙述了

## 2. 正式开始,安装Hexo
执行以下命令
```
$ sudo npm install -g hexo
```

## 3. 创建博客
安装 Hexo 完成后，执行下列命令，Hexo 将会在指定文件夹中新建所需要的文件。
```
$ hexo init <目录>
$ cd <目录>
$ npm install
```
新建完成后，指定文件夹的目录如下
>.
├── _config.yml
├── package.json
├── scaffolds
├── source
|   ├── _drafts
|   └── _posts
└── themes

## 4. 运行
执行下面的命令进行文件生成
```
$ hexo g
```
运行
```
$ hexo s
```
浏览器输入http://localhost:4000

到此，hexo博客算是搭建成功了，但是只能在本地看，下一步，我们把它部署到github上

## 5. 部署到github上

1. 首先我们需要先去[github](https://github.com/)上注册个账号
2. 登陆后新建一个仓库,仓库名称为:
>你的帐号.github.io

3. 获得新建仓库的下载地址：SSH或者HTTPS的

4. 修改hexo的配置文件，在站点目录下的_config.yml文件

修改文件里面的deploy。其中的repository就改成你刚刚复制的地址。保存这个文件
```
deploy:
  type: git
  repository: git@github.com:laayoune/laayoune.github.io.git
  branch: master
```
执行命令
```
$ hexo d
```
如果报错说没有git
那么安装插件
```
$ npm install hexo-deployer-git --save
```
后再执行hexo d命令

输入github博客地址:你的帐号.github.io，就可以看到一个简单的博客搭建成功了

注意:
如果使用的是SSH提交方式,第一次需要配置git密钥,否则会报错没有权限

* 查看是否有密钥
```
$ cd ~/.ssh
$ ls
authorized_keys2  id_dsa       known_hosts config            id_dsa.pub
```
看一下有没有id_rsa和id_rsa.pub(或者是id_dsa和id_dsa.pub之类成对的文件)，有 .pub 后缀的文件就是公钥，另一个文件则是密钥

* 如果没有,生成密钥
```
$ ssh-keygen -t rsa -C "your_email@youremail.com"
```
执行后会提示输入密码(建议输一个，当然不输也行)

* 查看你生成的公钥
```
$ cat ~/.ssh/id_rsa.pub
```

* 登陆你的github帐户。点击你的头像，然后 Settings -> 左栏点击 SSH and GPG keys -> 点击 New SSH key

然后你复制上面的公钥内容，粘贴进“Key”文本域内。 title域，自己随便起个名字就可以了





