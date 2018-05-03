---
title: hexo+github搭建个人博客之：next主题配置文件详细说明
date: 2018-04-27
categories: 其他技术
tags: [Hexo,next,github]
keywords: Hexo,next,博客
copyright: true
description:
---
<!-- more -->
按照上面两篇的文章，一个简单的博客已经搭建好了。下面介绍下主题的配置
在 Hexo 中有两份主要的配置文件，其名称都是 _config.yml。
其中，一份位于站点根目录下，主要包含 Hexo 本身的配置，为 **站点配置文件**；
另一份位于主题目录下，这份配置由主题作者提供，主要用于配置主题相关的选项，为 **主题配置文件**

hexo下有很多的主题，具体可以看[hexo主题](https://hexo.io/themes/),选择自己喜欢的
本文是获赞最多的next主题的配置文件说明

## 安装next主题
在终端窗口下，定位到 Hexo 站点目录下。使用 Git checkout 代码：
```shell
$ cd your-hexo-site
$ git clone https://github.com/iissnan/hexo-theme-next themes/next
```

## 启用主题
与所有 Hexo 主题启用的模式一样。 当 克隆/下载 完成后，打开 **站点配置文件**， 找到 theme 字段，并将其值更改为 next。
```
theme: next
```
主题设置完毕

#### 需要修改 **站点配置文件** 的地方
```
language: zh-Hans # 语言中文
```

#### 设置主题下外观
目前 NexT 支持三种 Scheme，他们是：

Muse - 默认 Scheme，这是 NexT 最初的版本，黑白主调，大量留白
Mist - Muse 的紧凑版本，整洁有序的单栏外观
Pisces - 双栏 Scheme，小家碧玉似的清新
Scheme 的切换通过更改 主题配置文件，搜索 scheme 关键字。 你会看到有三行 scheme 的配置，将你需用启用的 scheme 前面注释 # 去除即可。
```
#scheme: Muse
#scheme: Mist
scheme: Pisces
```
#### 设置菜单
```
menu:
  home: /
  archives: /archives
  #about: /about
  #categories: /categories
  tags: /tags
  #commonweal: /404.html
```
>若你的站点运行在子目录中，请将链接前缀的 / 去掉
前面的只是键值，对应的文字在languages/{language}.yml下

配置菜单前的小图标，menu_icons下面，键值与menu中的配置一致，大小写要严格匹配

#### 设置侧栏位置
设置侧栏的位置，修改 sidebar.position 的值，目前仅 Pisces Scheme 支持 position 配置
```
sidebar:
  position: left
```
设置侧栏显示的时机，修改 sidebar.display 的值
>post - 默认行为，在文章页面（拥有目录列表）时显示
always - 在所有页面中都显示
hide - 在所有页面中都隐藏（可以手动展开）
remove - 完全移除

#### 设置 头像
修改字段 avatar， 值设置成头像的链接地址
>放置在 source/images/ 目录下 , 配置为：avatar: /images/avatar.png
或者是完整的互联网 URI :   avatar: https://example.com/avatar.png

#### 设置 代码高亮主题
NexT共有5款代码高亮主题。默认使用的是 白色的 normal 主题。可选的值有 normal，night， night blue， night bright， night eighties：
![Markdown](https://i2.bvimg.com/643403/02909620bf7fcdf5.png)
更改 highlight_theme 字段，将其值设定成你所喜爱的高亮主题，例如：
```
# Code Highlight theme
# Available value: normal | night | night eighties | night blue | night bright
# https://github.com/chriskempson/tomorrow-theme
highlight_theme: normal
```

#### 开启侧边栏社交链接
```
# Social links
social:
  GitHub: https://github.com/your-user-name
  Twitter: https://twitter.com/your-user-name
  微博: https://weibo.com/your-user-name
  豆瓣: https://douban.com/people/your-user-name
  知乎: https://www.zhihu.com/people/your-user-name
  # 等等
```

#### 开启打赏功能
````
reward_comment: 坚持原创技术分享，您的支持将鼓励我继续创作！
wechatpay: /path/to/wechat-reward-image
alipay: /path/to/alipay-reward-image
````

#### 开启友情链接
```
links:
  MacTalk: https://macshuo.com/
  Title: https://example.com/
```

#### 订阅微信公众号
在每篇文章的末尾显示微信公众号二维码，扫一扫，轻松订阅博客。
在微信公众号平台下载您的二维码，并将它存放于博客source/uploads/目录下。
然后编辑 主题配置文件，如下：
```
wechat_subscriber:
  enabled: true
  qcode: /uploads/wechat-qcode.jpg
  description: 欢迎您扫一扫上面的微信公众号，订阅我的博客！
```

#### 设置背景动画
NexT 自带两种背景动画效果
编辑 主题配置文件， 搜索 canvas_nest 或 three_waves，根据您的需求设置值为 true 或者 false 即可：
```
# canvas_nest
canvas_nest: true //开启动画
canvas_nest: false //关闭动画

# three_waves
three_waves: true //开启动画
three_waves: false //关闭动画
```

#### 设置 阅读全文
在首页显示一篇文章的部分内容，并提供一个链接跳转到全文页面是一个常见的需求。 NexT 提供三种方式来控制文章在首页的显示方式。 也就是说，在首页显示文章的摘录并显示 阅读全文 按钮，可以通过以下方法：

1. 在文章中使用 <!-- more --> 手动进行截断，Hexo 提供的方式 推荐
2. 在文章的 front-matter 中添加 description，并提供文章摘录
3. 自动形成摘要，在 **主题配置文件** 中添加：
```
auto_excerpt:
  enable: true
  length: 150
```

#### 更改内容区域的宽度
NexT 对于内容的宽度的设定如下：
* 700px，当屏幕宽度 < 1600px
* 900px，当屏幕宽度 >= 1600px
* 移动设备下，宽度自适应
```
// 修改成你期望的宽度
$content-desktop = 700px

// 当视窗超过 1600px 后的宽度
$content-desktop-large = 900px
```
方法不适用于 Pisces Scheme，Pisces Scheme 的宽度修改如下:
在 source/css/_schemes/Picses/_layout.styl 中，同时修改 header 的宽度、.main-inner 的宽度以及 .content-wrap 的宽度
```css
header{ width: 90%; }
.container .main-inner { width: 90%; }
.content-wrap { width: calc(100% - 260px); }
```

#### 添加 标签 页面
新建「标签」页面，并在菜单中显示「标签」链接。「标签」页面将展示站点的所有标签，若你的所有文章都未包含标签，此页面将是空的。 底下代码是一篇包含标签的文章的例子：
```
title: 标签测试文章
tags:
  - Testing
  - Another Tag
---
```

1. 在终端窗口下，定位到 Hexo 站点目录下。使用 hexo new page 新建一个页面，命名为 tags ：
```
$ cd your-hexo-site
$ hexo new page tags
```
2. 编辑刚新建的页面，将页面的类型设置为 tags ，主题将自动为这个页面显示标签云。页面内容如下：
```
title: 标签
date: 2014-12-22 12:39:04
type: "tags"
---
```
3. 在菜单中添加链接。编辑 **主题配置文件** ， 添加 tags 到 menu 中，如下:
```
menu:
  home: /
  archives: /archives
  tags: /tags
```

#### 添加「分类」页面
与设置标签页面相同
1. 在终端窗口下，定位到 Hexo 站点目录下。使用 hexo new page 新建一个页面，命名为 categories ：
```
$ cd your-hexo-site
$ hexo new page categories
```
2. 编辑刚新建的页面，将页面的 type 设置为 categories ，主题将自动为这个页面显示分类。页面内容如下：
```
title: 分类
date: 2014-12-22 12:39:04
type: "categories"
---
```
3. 在菜单中添加链接。编辑 主题配置文件 ， 添加 categories 到 menu 中，如下:
```
menu:
  home: /
  archives: /archives
  categories: /categories
```

#### 腾讯公益404页面
腾讯公益404页面，寻找丢失儿童，让大家一起关注此项公益事业！
使用方法，新建 404.html 页面，放到主题的 source 目录下，内容如下：
```
<!DOCTYPE HTML>
<html>
<head>
  <meta http-equiv="content-type" content="text/html;charset=utf-8;"/>
  <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1" />
  <meta name="robots" content="all" />
  <meta name="robots" content="index,follow"/>
  <link rel="stylesheet" type="text/css" href="https://qzone.qq.com/gy/404/style/404style.css">
</head>
<body>
  <script type="text/plain" src="https://www.qq.com/404/search_children.js"
          charset="utf-8" homePageUrl="/"
          homePageName="回到我的主页">
  </script>
  <script src="https://qzone.qq.com/gy/404/data.js" charset="utf-8"></script>
  <script src="https://qzone.qq.com/gy/404/page.js" charset="utf-8"></script>
</body>
</html>
```

#### 修改文章内链接文本样式
修改文件 themes\next\source\css\/_common\components\post\post.styl ，在末尾,@import前添加如下css样式：
```
// 文章内链接文本样式
.post-body p a{
  color: #0593d3;
  border-bottom: none;
  border-bottom: 1px solid #0593d3;
  &:hover {
    color: #fc6423;
    border-bottom: none;
    border-bottom: 1px solid #fc6423;
  }
}
```

#### 修改文章底部的那个带#号的标签
修改模板
/themes/next/layout/_macro/post.swig，搜索 rel=”tag”>#，将 # 换成
```
<i class="fa fa-tag"></i>
```

#### 在每篇文章末尾统一添加“本文结束”标记
1. 在路径 \themes\next\layout\/_macro 中新建 passage-end-tag.swig 文件,并添加以下内容：
```
<div>
    {% if not is_index %}
        <div style="text-align:center;color: #ccc;font-size:14px;">
            -------------本文结束
            <i class="fa fa-heartbeat"></i>
            感谢您的阅读-------------
        </div>
    {% endif %}
</div>
```
2. 接着打开\themes\next\layout\/_macro\post.swig文件，在post-body 之后， post-footer之前添加如下代码：
```
<div>
  {% if not is_index %}
    {% include 'passage-end-tag.swig' %}
  {% endif %}
</div>
```
3. 然后打开**主题配置文件** ,在末尾添加：
```
# 文章末尾添加“本文结束”标记
passage_end_tag:
  enabled: true
```

#### 网站底部字数统计和时间统计
1. 文字时间统计切换到根目录下，然后运行如下代码
```
$ npm install hexo-wordcount --save
```

2. 然后在/themes/next/layout/_partials/footer.swig文件尾部加上：
```html
<div class="theme-info">
  <div class="powered-by"></div>
  <span class="post-count">博客全站共{{ totalcount(site) }}字</span>
</div>
```

3. 时间统计在主题的配置文件中，配置如下：
```json
# Post wordcount display settings
# Dependencies: https://github.com/willin/hexo-wordcount
post_wordcount:
item_text: true
wordcount: true
min2read: true
```

#### 在文章底部增加版权信息
在目录next/layout/_macro/下添加my-copyright.swig：
```html
{% if page.copyright %}
<div class="my_post_copyright">
  <script src="//cdn.bootcss.com/clipboard.js/1.5.10/clipboard.min.js"></script>

  <!-- JS库 sweetalert 可修改路径 -->
  <script type="text/javascript"  src="http://jslibs.wuxubj.cn/sweetalert_mini/jquery-1.7.1.min.js"></script>
  <script src="http://jslibs.wuxubj.cn/sweetalert_mini/sweetalert.min.js"></script>
  <link rel="stylesheet" type="text/css" href="http://jslibs.wuxubj.cn/sweetalert_mini/sweetalert.mini.css">
  <p><span>本文标题:</span><a href="{{ url_for(page.path) }}">{{ page.title }}</a></p>
  <p><span>文章作者:</span><a href="/" title="访问 {{ theme.author }} 的个人博客">{{ theme.author }}</a></p>
  <p><span>发布时间:</span>{{ page.date.format("YYYY年MM月DD日 - HH:MM") }}</p>
  <p><span>最后更新:</span>{{ page.updated.format("YYYY年MM月DD日 - HH:MM") }}</p>
  <p><span>原始链接:</span><a href="{{ url_for(page.path) }}" title="{{ page.title }}">{{ page.permalink }}</a>
    <span class="copy-path"  title="点击复制文章链接"><i class="fa fa-clipboard" data-clipboard-text="{{ page.permalink }}"  aria-label="复制成功！"></i></span>
  </p>
  <p><span>许可协议:</span>转载请保留原文链接及作者。</p>
</div>
<script>
    var clipboard = new Clipboard('.fa-clipboard');
    clipboard.on('success', $(function(){
      $(".fa-clipboard").click(function(){
        swal({
          title: "",
          text: '复制成功',
          html: false,
          timer: 500,
          showConfirmButton: false
        });
      });
    }));
</script>
{% endif %}
```
在目录next/source/css/_common/components/post/下添加my-post-copyright.styl：
```css
.my_post_copyright {
  width: 85%;
  max-width: 45em;
  margin: 2.8em auto 0;
  padding: 0.5em 1.0em;
  border: 1px solid #d3d3d3;
  font-size: 0.93rem;
  line-height: 1.6em;
  word-break: break-all;
  background: rgba(255,255,255,0.4);
}
.my_post_copyright p{margin:0;}
.my_post_copyright span {
  display: inline-block;
  width: 5.2em;
  color: #b5b5b5;
  font-weight: bold;
}
.my_post_copyright .raw {
  margin-left: 1em;
  width: 5em;
}
.my_post_copyright a {
  color: #808080;
  border-bottom:0;
}
.my_post_copyright a:hover {
  color: #a3d2a3;
  text-decoration: underline;
}
.my_post_copyright:hover .fa-clipboard {
  color: #000;
}
.my_post_copyright .post-url:hover {
  font-weight: normal;
}
.my_post_copyright .copy-path {
  margin-left: 1em;
  width: 1em;
  +mobile(){display:none;}
}
.my_post_copyright .copy-path:hover {
  color: #808080;
  cursor: pointer;
}
```
修改next/layout/_macro/post.swig，在代码
```
{% if theme.wechat_subscriber.enabled and not is_index %}
  <div>
    {% include 'wechat-subscriber.swig' %}
  </div>
{% endif %}
```
之前添加增加如下代码：
```
{% if not is_index %}
  <div>
    {% include 'my-copyright.swig' %}
  </div>
{% endif %}
```
修改next/source/css/_common/components/post/post.styl文件，在最后一行增加代码：
```
@import "my-post-copyright"
```
保存重新生成即可。如果要在该博文下面增加版权信息的显示，需要在 Markdown 中增加copyright: true的设置，类似：
```
---
title:
date:
tags:
categories:
copyright: true
---
```

以上是一些常用的配置


## 另外next主题的菜单图标显示无效的问题：
修改themes/next/layout/_partials 下的 header.swig文件，找到以下代码
```
<i class="menu-item-icon fa fa-fw fa-{{ path.split('||')[1] | trim | default('question-circle') }}"></i>
```
改为
```
<i class="menu-item-icon fa fa-fw fa-{{ theme.menu_icons[name] | default('question-circle') }}"></i>
```

##本文参考API [next](http://theme-next.iissnan.com/getting-started.html)