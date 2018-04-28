---
title: hexo+github搭建个人博客之：站点配置文件详细说明
categories: 其他技术
tags: [Hexo,github]
date: 2018-04-26
keywords: Hexo,github,博客
copyright: true
description:
---
## 站点配置
可以在 _config.yml 中修改大部份的配置。

### 网站
```
参数              描述
title           网站标题
subtitle        网站副标题
description     网站描述
author          您的名字
language        网站使用的语言
timezone        网站时区。Hexo 默认使用您电脑的时区。时区列表。比如说：America/New_York, Japan, 和 UTC 。
```
其中，description主要用于SEO，告诉搜索引擎一个关于您站点的简单描述，通常建议在其中包含您网站的关键词。author参数用于主题显示文章的作者。

### 网址
```
参数                 描述                       默认值
url                  网址
root               网站根目录
permalink         文章的永久链接格式      :year/:month/:day/:title/
permalink_defaults  永久链接中各部分的默认值
```

### 目录
```
参数                 描述
source_dir       资源文件夹，这个文件夹用来存放内容。
public_dir       公共文件夹，这个文件夹用于存放生成的站点文件。
tag_dir          标签文件夹
archive_dir      归档文件夹
category_dir     分类文件夹
code_dir         Include code 文件夹
i18n_dir         国际化（i18n）文件夹
skip_render      跳过指定文件的渲染，您可使用 glob 表达式来匹配路径。
```
### 文章
```
参数                  描述
new_post_name       新文章的文件名称
default_layout      预设布局
auto_spacing        在中文和英文之间加入空格
titlecase           把标题转换为 title case
external_link       在新标签中打开链接
filename_case       把文件名称转换为 (1) 小写或 (2) 大写
render_drafts       显示草稿
post_asset_folder   启动 Asset 文件夹
relative_link       把链接改为与根目录的相对位址
future              显示未来的文章
highlight           代码块的设置
```

### 分类&标签
```
参数                  描述          默认值
default_category    默认分类    uncategorized
category_map        分类别名
tag_map             标签别名
```

### 时间/日期格式
```
参数              描述      默认值
date_format     日期格式    YYYY-MM-DD
time_format     时间格式    H:mm:ss
```

### 分页
```
参数          描述                              默认值
per_page    每页显示的文章量 (0 = 关闭分页功能)   10
pagination_dir  分页目录                        page
```

### 扩展
```
参数          描述
theme       当前主题名称。值为false时禁用主题
deploy      部署部分的设置
```

##完整的站点配置:
```
# Site
title: 云的妍色 #网站标题
subtitle: 一字一符一世界 #网站副标题
description: 码农的日常  #网站描述
keywords:
author: zhuyt  #博主的名字
language: zh-Hans #网站使用的语言
timezone: #网站时区。Hexo 默认使用您电脑的时区

# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: https://laayoune.github.io   #http://yoursite.com
root: /
permalink: :title:year:month:day/      #生成文件名字的格式  :year/:month/:day/:title/
permalink_defaults:

# Directory 目录配置
source_dir: source #源文件夹，这个文件夹用来存放内容。
public_dir: public #公共文件夹，这个文件夹用于存放生成的站点文件。
tag_dir: tags #标签文件夹
archive_dir: archives #归档文件夹
category_dir: categories #分类文件夹
code_dir: downloads/code #nclude code 文件夹
i18n_dir: :lang   #国际化（i18n）文件夹
skip_render:   #跳过指定文件的渲染，您可使用 glob 表达式来匹配路径。

# Writing 文章
new_post_name: :title.md # 新建文章默认文件名
default_layout: post # 默认布局
titlecase: false # Transform title into titlecase
external_link: true # 在新标签中打开一个外部链接，默认为true
filename_case: 0  #转换文件名，1代表小写；2代表大写；默认为0，意思就是创建文章的时候，是否自动帮你转换文件名
render_drafts: false #是否渲染_drafts目录下的文章，默认为false
post_asset_folder: false #启动 Asset 文件夹
relative_link: false #把链接改为与根目录的相对位址，默认false
future: true #显示未来的文章，默认false
highlight: #代码块的设置
  enable: true
  line_number: true
  auto_detect: false
  tab_replace:

# Home page setting
# path: Root path for your blogs index page. (default = '')
# per_page: Posts displayed per page. (0 = disable pagination)
# order_by: Posts order. (Order by date descending by default)
index_generator:
  path: ''
  per_page: 10
  order_by: -date

# Category & Tag 分类和标签的设置
default_category: uncategorized #默认分类
category_map:   #分类别名
tag_map:   #标签别名

# Date / Time format
## Hexo uses Moment.js to parse and display date
## You can customize the date format as defined in
## http://momentjs.com/docs/#/displaying/format/
date_format: YYYY-MM-DD
time_format: HH:mm:ss

# Pagination 分页
## Set per_page to 0 to disable pagination
per_page: 10 #每页显示的文章量 (0 = 关闭分页功能)
pagination_dir: page #分页目录

# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: next ## hexo主题

## Rss
feed:
  type: atom       #feed 类型 (atom/rss2)
  path: atom.xml   #rss 路径
  limit: 20        #在 rss 中最多生成的文章数(0显示所有)

# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git
  repository: git@github.com:laayoune/laayoune.github.io.git
  branch: master
```
